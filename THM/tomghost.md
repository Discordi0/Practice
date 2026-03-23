
Identify recent vulnerabilities to try exploit the system or read files that you should not have access to.

![](https://assets.tryhackme.com/additional/imgur/fR0jVuM.png)

**Are you able to complete the challenge?**

---

# Questions

## Q1: Compromise this machine and obtain user.txt
### A: 

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


## Q2: Escalate privileges and obtain root.txt

### A: 
