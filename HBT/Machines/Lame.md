
About Lame

Lame is an easy Linux machine, requiring only one exploit to obtain root access. It was the first machine published on Hack The Box and was often the first machine for new users prior to its retirement.


Q1: How many of the `nmap` top 1000 TCP ports are open on the remote host?

A: 4

I start with a nmap scan with de sV sC and Pn flags.

![](../../Img/Pasted%20image%2020250508224213.png)

Q2: What version of VSFTPd is running on Lame?

A: 2.3.4

In the same scan as Q1 we get the answer.

Q3: There is a famous backdoor in VSFTPd version 2.3.4, and a Metasploit module to exploit it. Does that exploit work here?

A: no

I started metasploit and search for the exploit.

![](../../Img/Pasted%20image%2020250508224936.png)

Check what it needs, and set it.

![](../../Img/Pasted%20image%2020250508225010.png)

Seems to kinda work?, i would say if no shell then no worki.

![](../../Img/Pasted%20image%2020250508225042.png)

Q4: What version of Samba is running on Lame? Give the numbers up to but not including "-Debian".

A: 3.0.20

It's in the same nmap scan as Q1.

Q5: What 2007 CVE allows for remote code execution in this version of Samba via shell metacharacters involving the `SamrChangePassword` function when the "username map script" option is enabled in `smb.conf`?

A: CVE-2007-2447

Google the cves for samba and read. (https://cve-mitre-org.translate.goog/cgi-bin/cvekey.cgi?keyword=samba&_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc)

![](../../Img/Pasted%20image%2020250508225450.png)

Q6: Exploiting CVE-2007-2447 returns a shell as which user?

A: 

Since i already was using metasploit, i decided to use it.
It didn't work.

![](../../Img/Pasted%20image%2020250508230032.png)



Q7: Submit the flag located in the makis user's home directory.

A: 

Q8: Submit the flag located in root's home directory.

A: 

Q9: 
A: 

Q10: 
A: 

Q11: 
A: 

