
Identify recent vulnerabilities to try exploit the system or read files that you should not have access to.

![](https://assets.tryhackme.com/additional/imgur/fR0jVuM.png)

**Are you able to complete the challenge?**

---

# Questions

## Q1: Compromise this machine and obtain user.txt
### A: THM{GhostCat_1s_so_cr4sy}

I started with an nmap scan 

![](../Img/Pasted%20image%2020260323191227.png)

We can see that we have some interesting ports open, i started with port 8009 bc it's the one that i have never seen

I searched for an exploit and found that there was one in metasploit

Open msfconsole and find it

![](../Img/Pasted%20image%2020260323192401.png)

Select it and set the options

This is what i got

![](../Img/Pasted%20image%2020260323192348.png)

I have no idea what those are for, but since we have ssh (port 22) open, lets try them there

It worked

![](../Img/Pasted%20image%2020260323192649.png)

Find the flag

![](../Img/Pasted%20image%2020260323192740.png)

---
## Q2: Escalate privileges and obtain root.txt

### A: 

Now we need to privesc in the user directory we found a .pgp file, so i assume that this is the route

Copy the files to our machine then use pgp2john

![](../Img/Pasted%20image%2020260323193522.png)

Now use john to crack it

![](../Img/Pasted%20image%2020260323193549.png)

Decrypt the file

![](../Img/Pasted%20image%2020260323193845.png)

I assume that this ones are other ssh credentials, so use them

Got it

![](../Img/Pasted%20image%2020260323194010.png)

