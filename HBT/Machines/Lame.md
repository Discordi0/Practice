
# About Lame

Lame is an easy Linux machine, requiring only one exploit to obtain root access. It was the first machine published on Hack The Box and was often the first machine for new users prior to its retirement.

___

### Q1: How many of the `nmap` top 1000 TCP ports are open on the remote host?

#### A: 4

I start with a nmap scan with de sV sC and Pn flags.

![](../../Img/Pasted%20image%2020250508224213.png)

___

### Q2: What version of VSFTPd is running on Lame?

#### A: 2.3.4

In the same scan as Q1 we get the answer.

___

### Q3: There is a famous backdoor in VSFTPd version 2.3.4, and a Metasploit module to exploit it. Does that exploit work here?

#### A: no

I started metasploit and search for the exploit.

![](../../Img/Pasted%20image%2020250508224936.png)

Check what it needs, and set it.

![](../../Img/Pasted%20image%2020250508225010.png)

Seems to kinda work?, i would say if no shell, then no worki.

![](../../Img/Pasted%20image%2020250508225042.png)

___

### Q4: What version of Samba is running on Lame? Give the numbers up to but not including "-Debian".

#### A: 3.0.20

It's in the same nmap scan as Q1.

___

### Q5: What 2007 CVE allows for remote code execution in this version of Samba via shell metacharacters involving the `SamrChangePassword` function when the "username map script" option is enabled in `smb.conf`?

#### A: CVE-2007-2447

Google the cves for samba and found this. (https://cve-mitre-org.translate.goog/cgi-bin/cvekey.cgi?keyword=samba&_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc)

![](../../Img/Pasted%20image%2020250508225450.png)

___

### Q6: Exploiting CVE-2007-2447 returns a shell as which user?

#### A: root

Since i already was using metasploit, i decided to use it.

![](../../Img/Pasted%20image%2020250508232046.png)

___

### Q7: Submit the flag located in the makis user's home directory.

#### A: 0b5492d275eed722d4026f6f379a40c1

Search for it.

![](../../Img/Pasted%20image%2020250508232156.png)

___

### Q8: Submit the flag located in root's home directory.

#### A: 4d40f74e9a845f79202b7025f740f86e

Same.

![](../../Img/Pasted%20image%2020250508232257.png)

___

### Q9: We'll explore a bit beyond just getting a root shell on the box. While the official writeup doesn't cover this, you can look at [0xdf's write-up](https://0xdf.gitlab.io/2020/04/07/htb-lame.html#beyond-root---vsftpd) for more details. With a root shell, we can look at why the VSFTPd exploit failed. Our initial `nmap` scan showed four open TCP ports. Running `netstat -tnlp` shows many more ports listening, including ones on 0.0.0.0 and the boxes external IP, so they should be accessible. What must be blocking connection to these ports?

#### A: firewall

It just seem logical.

___

### Q10: When the VSFTPd backdoor is trigger, what port starts listening?

#### A: 6200

Aftert a while i got it.
I had to install exploitDb to search for the exploit that used telnet for some reason -.-

![](../../Img/Pasted%20image%2020250509000145.png)

Q11: When the VSFTPd backdoor is triggered, does port 6200 start listening on Lame?

A: yes

Let's see.

![](../../Img/Pasted%20image%2020250509000951.png)

It actually did.

![](../../Img/Pasted%20image%2020250509000624.png)

Tags: [Mestasploit](../../Index/Mestasploit.md) [Nmap](../../Index/Nmap.md)