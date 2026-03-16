
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
### A: **a228b12a08b6527e7978cbe5d914531c**

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

Now that i have a connection i dropped linpeas and left it to run.

I tried this exploit but it didn't work

![](../Img/Pasted%20image%2020260315174455.png)

I did see some creedentials on the linpeas output so i used those and got the user mike

And i did use mysql with the creedentials of the screenshot to get the hash.

---

## Q4: What's the user flag?
### A: THM{af05cd30bfed67849befd546ef}

Once i got mike just search for the file and use cat


---

## Q5: What's the root flag?
### A: THM{ba87e0dfe5903adfa6b8b450ad7567bafde87}

For this one once i was mike i used sudo -l and got a file

For that file i searched in gtfobins and used the instructions and got root.



# PS

There was no screenshot for the last part because the Try Hack Me platform and machine were crashing, at least it's free no?

Tags: [File Uploads](../Index/File%20Uploads.md) [Lin Privesc](../Index/Lin%20Privesc.md) [Nmap](../Index/Nmap.md) [SQLi](../Index/SQLi.md) 


