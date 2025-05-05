
About Hospital

Hospital is a medium-difficulty Windows machine that hosts an Active Directory environment, a web server, and a `RoundCube` instance. The web application has a file upload vulnerability that allows the execution of arbitrary PHP code, leading to a reverse shell on the Linux virtual machine hosting the service. Enumerating the system reveals an outdated Linux kernel that can be exploited to gain root privileges, via `[CVE-2023-35001](https://nvd.nist.gov/vuln/detail/CVE-2023-35001)`. Privileged access allows `/etc/shadow` hashes to be read and subsequently cracked, yielding credentials for the `RoundCube` instance. Emails on the service hint towards the use of `GhostScript`, which opens up the target to exploitation via `[CVE-2023-36664](https://nvd.nist.gov/vuln/detail/CVE-2023-36664)`, a vulnerability exploited by crafting a malicious Embedded PostScript (EPS) file to achieve remote code execution on the Windows host. System access is then obtained by either of two ways: using a keylogger to capture `administrator` credentials, or by abusing misconfigured `XAMPP` permissions.



Q1: What is the domain name that Hospital is a domain controller for?

A: hospital.htb

With the nmap scan we can find it. (nmap -sC -sV -Pn 10.10.11.241)

![](../../Img/Pasted%20image%2020250505152955.png)

Q2: What webmail application is running on TCP 443?

A: 

In the nmap scan there wasn't anything about the name of the mail application running, se we visit the page.

![](../../Img/Pasted%20image%2020250505153433.png)

The web page didn't gave an answer either (maybe if someone knew the logo, but i don't so)

Q3: 
A: 

Q4: 
A: 

Q5: 
A: 

Q6: 
A: 

Q7: 
A: 

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

