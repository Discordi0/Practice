
Something seems a little off with the server.

![](https://tryhackme-images.s3.amazonaws.com/room-icons/5dbc4e7d8515e7bc05b7742f26944ae9.png)  

Agent T uncovered this website, which looks innocent enough, but something seems off about how the server responds...

After deploying the vulnerable machine attached to this task, please wait a couple of minutes for it to respond.

---

# Questions

## Q1: What is the flag?
### A: flag{4127d0530abf16d6d23973e3df8dbecb}

First with the nmap scan

![](../Img/Pasted%20image%2020260320163218.png)

We can already see that there is a web page (as per the description of the box)

I just opened the page and seems like i'm already admin

![](../Img/Pasted%20image%2020260320163352.png)

Reading it's source code i found nothing

After 10+ min the scan didn't give an output, so i had to make a new one only on port 80

This is what i got

![](../Img/Pasted%20image%2020260320165252.png)

Searching for PHP 8.1.0-dev got mi this (https://www.exploit-db.com/exploits/49933)

So we download it and check

![](../Img/Pasted%20image%2020260320170552.png)

Seem like i'm already root, so we just need to search for the flag

![](../Img/Pasted%20image%2020260320170525.png)


Tags: [Lin Privesc](../Index/Lin%20Privesc.md) [Nmap](../Index/Nmap.md) 


