
# About

`Expressway` is an easy-difficulty Linux machine that demonstrates enumeration and exploits the IKE service, a component of the `IPsec` framework. Upon leaking the Pre-Shared key of the service and cracking it, the retrieved clear-text credentials are used to access the target via SSH. For privilege escalation, [CVE-2025-32462](https://nvd.nist.gov/vuln/detail/CVE-2025-32462) is exploited to get a privileged shell as the `root` user.

---

# Questions

## Q1: User flag.
### A: 

First as with any machine we need to do a nmap scan to check what services it's running . `nmap -A -p- {victim-ip}`

Got only ssh, i tried with other types of scans and got the same result (-sT -sN -sS, etc -A was taking too long so i didn't complete it).

![](../../Img/Pasted%20image%2020260307163926.png)

Finally i did UDP scan `sudo nmap -sU -T4 -vv {victim-ip}` and this is what i got.

![](../../Img/Pasted%20image%2020260307165727.png)

Searching for those open ports i find that isakmp and ike are related (https://en.wikipedia.org/wiki/Internet_Security_Association_and_Key_Management_Protocol).

And searching a little bit more i see that Parrot Os comes with an ike scanner, so we use that.



## Q2: Root flag.
### A: 
