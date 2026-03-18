
Easy boot2root Machine

Deploy and compromise the machine!

![](https://assets.tryhackme.com/additional/imgur/1pGMAEM.png)

---

# Questions

## Q1: What is the user flag?
### A: 

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


## Q2: What is the root flag?
### A: 