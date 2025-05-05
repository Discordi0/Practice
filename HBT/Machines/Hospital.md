
About Hospital

Hospital is a medium-difficulty Windows machine that hosts an Active Directory environment, a web server, and a `RoundCube` instance. The web application has a file upload vulnerability that allows the execution of arbitrary PHP code, leading to a reverse shell on the Linux virtual machine hosting the service. Enumerating the system reveals an outdated Linux kernel that can be exploited to gain root privileges, via `[CVE-2023-35001](https://nvd.nist.gov/vuln/detail/CVE-2023-35001)`. Privileged access allows `/etc/shadow` hashes to be read and subsequently cracked, yielding credentials for the `RoundCube` instance. Emails on the service hint towards the use of `GhostScript`, which opens up the target to exploitation via `[CVE-2023-36664](https://nvd.nist.gov/vuln/detail/CVE-2023-36664)`, a vulnerability exploited by crafting a malicious Embedded PostScript (EPS) file to achieve remote code execution on the Windows host. System access is then obtained by either of two ways: using a keylogger to capture `administrator` credentials, or by abusing misconfigured `XAMPP` permissions.



Q1: What is the domain name that Hospital is a domain controller for?

A: hospital.htb

With the nmap scan we can find it. (nmap -sC -sV -Pn 10.10.11.241)

![](../../Img/Pasted%20image%2020250505152955.png)

Q2: What webmail application is running on TCP 443?

A: RoundCube

In the nmap scan there wasn't anything about the name of the mail application running, se we visit the page.

![](../../Img/Pasted%20image%2020250505153433.png)

The web page didn't gave an answer either (maybe if someone knew the logo, but i don't so... ).
Looking at the source code i found this.

![](../../Img/Pasted%20image%2020250505153618.png)

![](../../Img/Pasted%20image%2020250505153712.png)

Q3: Looking at the web application on TCP 8080, what is the relative path of the directory where uploads are saved?

A: /uploads

I use Burp to see if the upload directory is found inside the request.

![](../../Img/Pasted%20image%2020250505155307.png)

Seeing that there is nothing here, i use ffuf to try to find the directory. (ffuf -w /home/discordio/SecLists-master/Discovery/Web-Content/directory-list-2.3-medium.txt:FUZZ -u http://10.10.11.241:8080/FUZZ).
This is what it found.

![](../../Img/Pasted%20image%2020250505160616.png)

Q4: What file extension is allowed to be uploaded and will be executed as PHP?

A: phar

For this i use burp intruder.

It seems like this machine it's only blocking ".php" files. As this pass

![](../../Img/Pasted%20image%2020250505165027.png)

![](../../Img/Pasted%20image%2020250505165038.png)

But this didn't.

![](../../Img/Pasted%20image%2020250505164702.png)

![](../../Img/Pasted%20image%2020250505164646.png)

Q5: What user is the webserver running as?

A: 

Since we know where the file goes, and what extension does the file have to be, let's get a shell.
I used weevely, as per the hint. (i'm not very good yet with shells and i also wanted to try a new thing) (https://github.com/epinna/weevely3)

weevely generate 'hospital123' shellHospital.phar

weevely http://10.10.11.241:8080/uploads/shellHospital.phar 'hospital123'

![](../../Img/Pasted%20image%2020250505170017.png)

Q6: What is the kernel name (version) of the webserver?

A: 5.19.0-35-generic

Use uname -a to check.

![](../../Img/Pasted%20image%2020250505171158.png)

Q7: What user besides root has a password hash in the `shadow` file?

A: 

So, i tried to to this one, but it just got stuck, and the shell just died a lot. (https://github.com/synacktiv/CVE-2023-35001)

![](../../Img/Pasted%20image%2020250505174948.png)



So i tried another one that i found.
Q8: 
A: 

Q9: 
A: 

Q10: 
A: 

Q11: 
A: 

Q12: 
A: 

Q13: 
A: 

Q14: 
A: 

Q15: 
A: 

