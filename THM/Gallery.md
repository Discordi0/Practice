
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

Reading through the exploit i found this

![](../Img/Pasted%20image%2020260315161940.png)

So i tried this credentials (a couple of times bc the page got stuck) and i got in

![](../Img/Pasted%20image%2020260315162024.png)

Checking the site i cam across a possible entry point

![](../Img/Pasted%20image%2020260315162752.png)

Uploading a reverse shell worked instantly

![](../Img/Pasted%20image%2020260315163602.png)

Searching the folder of the web page i found this

![](../Img/Pasted%20image%2020260315165630.png)


## Q4: What's the user flag?
### A: 

## Q5: What's the root flag?
### A: 
