
boot2root machine for FIT and bsides guatemala CTF

---

# Questions

## Q1: user.txt
### A: 606083fd33beb1284fc51f411a706af8

We first start with an nmap scan

There is ftp 

![](../Img/Pasted%20image%2020260320160206.png)

And ssh 

![](../Img/Pasted%20image%2020260320160221.png)

We can see that we can login as anonymous in ftp so we do that

![](../Img/Pasted%20image%2020260320160514.png)

Then i searched for the flag, downloaded to my machine and open it

![](../Img/Pasted%20image%2020260320160453.png)

---
## Q2: root.txt
### A: 

Searching for what to do now i found this strange

![](../Img/Pasted%20image%2020260320161127.png)

So i went to /notread

![](../Img/Pasted%20image%2020260320161245.png)

A quick google got me this

![](../Img/Pasted%20image%2020260320161315.png)

![](../Img/Pasted%20image%2020260320161406.png)

So if i'm getting this right, i need to crack private for it to get the pgp file open

We use pgp2john first, the crack it with john

![](../Img/Pasted%20image%2020260320161759.png)

![](../Img/Pasted%20image%2020260320161746.png)

With this passphrase(?) we can open the pgp file

