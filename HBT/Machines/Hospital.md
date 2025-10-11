
# About Hospital

Hospital is a medium-difficulty Windows machine that hosts an Active Directory environment, a web server, and a `RoundCube` instance. The web application has a file upload vulnerability that allows the execution of arbitrary PHP code, leading to a reverse shell on the Linux virtual machine hosting the service. Enumerating the system reveals an outdated Linux kernel that can be exploited to gain root privileges, via `[CVE-2023-35001](https://nvd.nist.gov/vuln/detail/CVE-2023-35001)`. Privileged access allows `/etc/shadow` hashes to be read and subsequently cracked, yielding credentials for the `RoundCube` instance. Emails on the service hint towards the use of `GhostScript`, which opens up the target to exploitation via `[CVE-2023-36664](https://nvd.nist.gov/vuln/detail/CVE-2023-36664)`, a vulnerability exploited by crafting a malicious Embedded PostScript (EPS) file to achieve remote code execution on the Windows host. System access is then obtained by either of two ways: using a keylogger to capture `administrator` credentials, or by abusing misconfigured `XAMPP` permissions.

___

### Q1: What is the domain name that Hospital is a domain controller for?

#### A: hospital.htb

With the nmap scan we can find it. (nmap -sC -sV -Pn 10.10.11.241)

![](../../Img/Pasted%20image%2020250505152955.png)

___

### Q2: What webmail application is running on TCP 443?

#### A: RoundCube

In the nmap scan there wasn't anything about the name of the mail application running, se we visit the page.

![](../../Img/Pasted%20image%2020250505153433.png)

The web page didn't gave an answer either (maybe if someone knew the logo, but i don't so... ).
Looking at the source code i found this.

![](../../Img/Pasted%20image%2020250505153618.png)

![](../../Img/Pasted%20image%2020250505153712.png)

___

### Q3: Looking at the web application on TCP 8080, what is the relative path of the directory where uploads are saved?

#### A: /uploads

I use Burp to see if the upload directory is found inside the request.

![](../../Img/Pasted%20image%2020250505155307.png)

Seeing that there is nothing here, i use ffuf to try to find the directory. (ffuf -w /home/discordio/SecLists-master/Discovery/Web-Content/directory-list-2.3-medium.txt:FUZZ -u http://10.10.11.241:8080/FUZZ).
This is what it found.

![](../../Img/Pasted%20image%2020250505160616.png)

___

### Q4: What file extension is allowed to be uploaded and will be executed as PHP?

#### A: phar

For this i use burp intruder.

It seems like this machine it's only blocking ".php" files. As this pass

![](../../Img/Pasted%20image%2020250505165027.png)

![](../../Img/Pasted%20image%2020250505165038.png)

But this didn't.

![](../../Img/Pasted%20image%2020250505164702.png)

![](../../Img/Pasted%20image%2020250505164646.png)

___

### Q5: What user is the webserver running as?

A: www-data

Since we know where the file goes, and what extension does the file have to be, let's get a shell.
I used weevely, as per the hint. (i'm not very good yet with shells and i also wanted to try a new thing) (https://github.com/epinna/weevely3)

weevely generate 'hospital123' shellHospital.phar

weevely http://10.10.11.241:8080/uploads/shellHospital.phar 'hospital123'

![](../../Img/Pasted%20image%2020250505170017.png)

___

### Q6: What is the kernel name (version) of the webserver?

#### A: 5.19.0-35-generic

Use uname -a to check.

![](../../Img/Pasted%20image%2020250505171158.png)

___

### Q7: What user besides root has a password hash in the `shadow` file?

#### A: drwilliams

So, i tried to to this one. (https://github.com/synacktiv/CVE-2023-35001).

![](../../Img/Pasted%20image%2020250505181711.png)

![](../../Img/Pasted%20image%2020250505181809.png)

With hascat we got it.

![](../../Img/Pasted%20image%2020250505182729.png)


___

### Q8: Who has emailed Doctor Williams?

#### A: drbrown@hospital.htb

With dr Williams credentials we log in and find this.

![](../../Img/Pasted%20image%2020250505182939.png)

___

### Q9: What is the 2023 CVE ID for a command injection vulnerability in Ghostscript when it opens `.eps` files?

#### A: CVE-2023-36664

Googling around i found this.
https://github.com/jakabakos/CVE-2023-36664-Ghostscript-command-injection

___

### Q10: Submit the flag located on the drbrown user's desktop.

#### A: 1a9e73567161eb68c6dad1bc4404581e

I use the POC in the link of the above question.
We send the created .eps file to the dear doc, and get a connection back.

![](../../Img/Pasted%20image%2020250505184059.png)

![](../../Img/Pasted%20image%2020250505184212.png)

___

### Q11: What user has an active session on Hospital?

#### A: drbrown

![](../../Img/Pasted%20image%2020250505185512.png)

___

### Q12: [Path 1] What is the administrator's password?

#### A: Th3B3stH0sp1t4l9786!

It needed a few tries because the connection just dies (every 10 min or so.) but i got it with the keyscan of meterpreter.

___

### Q13: [Path 2] On Hospital, what is the full path of the web root directory for the RoundCube instance?

#### A: C:\xampp\htdocs

I'm already admin, so i just search for it.

![](../../Img/Pasted%20image%2020250505193032.png)

___

### Q14: What user is the XAMPP webserver running as?

#### A: ???

I did get the shell and with whoami i got
nt authority\system. But this doesn't work so.. idk

___

### Q15: Submit the flag located on the administrator user's desktop.

#### A: 8a8a3d62de1e4205c1c3b7e781bdf4bf

With the credentials, use evil-winrm and find it.

![](../../Img/Pasted%20image%2020250505192439.png)

Tags: [Burp Suite](../../Index/Burp%20Suite.md) [Evil-Winrm](../../Index/Evil-Winrm.md) [ffuf](../../Index/ffuf.md) [File Uploads](../../Index/File%20Uploads.md) [Password Cracking](../../Index/Password%20Cracking.md) [HTML Review](../../Index/HTML%20Review.md) [Nmap](../../Index/Nmap.md) 