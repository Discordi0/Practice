
This room is aimed for beginner level hackers but anyone can try to hack this box. There are two main intended ways to root the box.

---

# Questions

## Q1: User flag
### A: 

We first do an nmap scan

![](../Img/Pasted%20image%2020260326214408.png)

Seeing that port 80 it's present, we check the web page

![](../Img/Pasted%20image%2020260326213635.png)

Not much to see on the page itself, check the source code

![](../Img/Pasted%20image%2020260326213729.png)

So we need to download that image

Not much to see on exiftool

![](../Img/Pasted%20image%2020260326213834.png)

We check with steghide

![](../Img/Pasted%20image%2020260326214024.png)

There seems to me something, but i don't have the passphrase

Now that it finally finished the nmap scan we can see that ftp is also present so let's check it out


## Q2: Root flag
### A: 
