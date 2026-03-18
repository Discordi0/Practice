
Easy boot2root Machine

Deploy and compromise the machine!

![](https://assets.tryhackme.com/additional/imgur/1pGMAEM.png)

---

# Questions

## Q1: What is the user flag?
### A: 62d77a4d5f97d47c5aa38b3b2651b831

Do an nmap scan

![](../Img/Pasted%20image%2020260318143159.png)

If we look at the page we find a "normal" looking page

![](../Img/Pasted%20image%2020260318143330.png)

Source code looks normal too

About looks fine (http://10.67.153.20/about.html)

Gallery too (http://10.67.153.20/gallery.html)

Blog too (http://10.67.153.20/blog.html)

In Contact there is a form 

![](../Img/Pasted%20image%2020260318143956.png)

With no more to go on i use gobuster to check for more directories

![](../Img/Pasted%20image%2020260318144620.png)

/custom seem interesting

![](../Img/Pasted%20image%2020260318144659.png)

css didn't have anything, but on js there is a .bak file

This is what it has

![](../Img/Pasted%20image%2020260318144857.png)

That seems like a hash of the password so we need to crack it

![](../Img/Pasted%20image%2020260318145016.png)

With this i went to try to connect to ssh since it's the only thing left

![](../Img/Pasted%20image%2020260318145126.png)

Not knowing what to do next i did a new nmap scan with -p- flag

Found this new port

![](../Img/Pasted%20image%2020260318145211.png)

Searching the ip with the new port we get this

![](../Img/Pasted%20image%2020260318145303.png)

The credentials work here, we get this

![](../Img/Pasted%20image%2020260318145339.png)

Checking the source code i found this

![](../Img/Pasted%20image%2020260318145526.png)

Nothing more note worthy

If we press submit we get this

![](../Img/Pasted%20image%2020260318145621.png)

Since i now know that i'm looking for i got a payload and tried it (https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/XXE%20Injection#detect-the-vulnerability)

![](../Img/Pasted%20image%2020260318150036.png)

Now that we know that it works we need the ssh key

With a new payload i got this

![](../Img/Pasted%20image%2020260318150333.png)

We can see that barry and joe are there at the end

We try to get the key for barry

![](../Img/Pasted%20image%2020260318150604.png)

Joe didn't have none

We need to copy the key, chmod it, use ssh2john and crack it

![](../Img/Pasted%20image%2020260318153600.png)

With this we can now ssh 

We got in

![](../Img/Pasted%20image%2020260318153721.png)

Now search for the flag

![](../Img/Pasted%20image%2020260318153748.png)

---
## Q2: What is the root flag?
### A: 

