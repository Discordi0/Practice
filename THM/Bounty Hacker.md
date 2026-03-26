
You talked a big game about being the most elite hacker in the solar system. Prove it and claim your right to the status of Elite Bounty Hacker!

You were boasting on and on about your elite hacker skills in the bar and a few Bounty Hunters decided they'd take you up on claims! Prove your status is more than just a few glasses at the bar. I sense bell peppers & beef in your future!

---

# Questions

## Q1: Who wrote the task list?
### A: lin

We do an nmap scan

![](../Img/Pasted%20image%2020260325234444.png)

On the main web page we can find this

![](../Img/Pasted%20image%2020260325233705.png)

We have 1 directory

![](../Img/Pasted%20image%2020260325233740.png)

With no more much to do i opened a gobuster dir scan

![](../Img/Pasted%20image%2020260325234023.png)

In /images we just have the image of the main page

![](../Img/Pasted%20image%2020260325233932.png)

In /javascript we don't have permissions

![](../Img/Pasted%20image%2020260325233954.png)

In the nmap scan we also saw that port 21 was open so we try to see if ftp allows anonynmous login

![](../Img/Pasted%20image%2020260325234242.png)

locks.txt

![](../Img/Pasted%20image%2020260325234334.png)

task.txt

![](../Img/Pasted%20image%2020260325234348.png)

---
## Q2: What service can you bruteforce with the text file found?
### A: ssh


Well, sisnce the only other service that nmap got on the machine ssh, that one would have to be

---
## Q3: What is the users password?
### A: RedDr4gonSynd1cat3

We will have to bruteforce ssh

I use hydra for this task

![](../Img/Pasted%20image%2020260325235251.png)

---
## Q4: user.txt
### A: THM{CR1M3_SyNd1C4T3}

Now we can connect with ssh

![](../Img/Pasted%20image%2020260325235416.png)

Find the flag

![](../Img/Pasted%20image%2020260325235439.png)

---
## Q5: root.txt
### A: THM{80UN7Y_h4cK3r}

Checking how to privesc i found this

![](../Img/Pasted%20image%2020260325235543.png)

I used (b) payload from gtfobins (https://gtfobins.org/gtfobins/tar/)

![](../Img/Pasted%20image%2020260325235709.png)

Now find the flag

![](../Img/Pasted%20image%2020260325235739.png)

Tags: [Brute Force](../Index/Brute%20Force.md) [Fuzzing](../Index/Fuzzing.md) [Lin Privesc](../Index/Lin%20Privesc.md) [Nmap](../Index/Nmap.md) 