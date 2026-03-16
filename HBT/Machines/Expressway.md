
# About

`Expressway` is an easy-difficulty Linux machine that demonstrates enumeration and exploits the IKE service, a component of the `IPsec` framework. Upon leaking the Pre-Shared key of the service and cracking it, the retrieved clear-text credentials are used to access the target via SSH. For privilege escalation, [CVE-2025-32462](https://nvd.nist.gov/vuln/detail/CVE-2025-32462) is exploited to get a privileged shell as the `root` user.

---

# Questions

## Q1: User flag.
### A: 78dda3fb349a50c9f8dee071d97ec080

First as with any machine we need to do a nmap scan to check what services it's running . `nmap -A -p- {victim-ip}`

Got only ssh, i tried with other types of scans and got the same result (-sT -sN -sS, etc -A was taking too long so i didn't complete it).

![](../../Img/Pasted%20image%2020260307163926.png)

Finally i did UDP scan `sudo nmap -sU -T4 -vv {victim-ip}` and this is what i got.

![](../../Img/Pasted%20image%2020260307165727.png)

Searching for those open ports i find that isakmp and ike are related (https://en.wikipedia.org/wiki/Internet_Security_Association_and_Key_Management_Protocol).

And searching a little bit more i see that Parrot Os comes with an ike scanner, so we use that. `sudo ike-scan {victim-ip}`

![](../../Img/Pasted%20image%2020260307170611.png)

Reading the man page of the scan i found that -P lets me crack the password, so we do that.

![](../../Img/Pasted%20image%2020260307170733.png)

With this i can use hashcat to try to crack it.

![](../../Img/Pasted%20image%2020260307171121.png)

Since i know that we have ssh in the machine, i tried to connect to it with the pswd and the user ike.

![](../../Img/Pasted%20image%2020260307171334.png)

Now search for the flag.

![](../../Img/Pasted%20image%2020260307171427.png)

---
## Q2: Root flag.
### A: 

Now that we have accessed the machine we need to privesc, for that i got linpeas into the machine to check it out.

![](../../Img/Pasted%20image%2020260307172117.png)

The first thing that the scan show is in red it's this. if we follow the link (https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#sudo-version) it takes us to CVE-2025-32463 (https://github.com/pr0v3rbs/CVE-2025-32463_chwoot).

Trying that exploit get us this.

![](../../Img/Pasted%20image%2020260307172535.png)

Seems like we are already root, so let's find the root flag.

![](../../Img/Pasted%20image%2020260307172616.png)

Tags: [Ike](../../Index/Ike.md) [Lin Privesc](../../Index/Lin%20Privesc.md) [Nmap](../../Index/Nmap.md) [Password Cracking](../../Index/Password%20Cracking.md) 