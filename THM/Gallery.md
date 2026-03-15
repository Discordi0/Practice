
Try to exploit our image gallery system

---

# Questions

## Q1: How many ports are open?
### A: 3

I did a simple nmap scan `nmap -A -T4 -vv 10.64.139.85`

![](../Img/Pasted%20image%2020260315160802.png)

---
## Q2: What's the name of the CMS?
### A: Simple Image Gallery

Just searching for the ip gets us a timed out

![](../Img/Pasted%20image%2020260315161033.png)

Doing IP:80 got me this

![](../Img/Pasted%20image%2020260315161104.png)

Doing IP:8080 got me something better

![](../Img/Pasted%20image%2020260315161133.png)

---
## Q3: What's the hash password of the admin user?
### A: 

Reading the page code didn't give anything

So to search for an exploit it is. I found this (https://www.exploit-db.com/exploits/50214)



## Q4: What's the user flag?
### A: 

## Q5: What's the root flag?
### A: 
