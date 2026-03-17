
Exploit a recent vulnerability and hack Webmin, a web-based system configuration tool.

---

# Questions

## Q1: user.txt
### A: 

First we do an nmap scan `nmap -sV -sC -T5 -vv 10.66.150.205`

![](../Img/Pasted%20image%2020260317171913.png)

![](../Img/Pasted%20image%2020260317171948.png)

We can see that on port 1000 we have a http server, so we check it 

![](../Img/Pasted%20image%2020260317172147.png)

Change to https 

![](../Img/Pasted%20image%2020260317172221.png)

Nothing on source code

I tried standard payload

![](../Img/Pasted%20image%2020260317172609.png)

![](../Img/Pasted%20image%2020260317172619.png)

With other payloads i get this 

![](../Img/Pasted%20image%2020260317172742.png)

But when i try something like this `" or true--` i get the invalid character, so no --

But after a lot of tries i just went to another route

I opened metasploit and searched for something

![](../Img/Pasted%20image%2020260317173516.png)


## Q2: root.txt
### A: 

