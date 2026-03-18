
Practice using tools such as Nmap and GoBuster to locate a hidden directory to get initial access to a vulnerable machine. Then escalate your privileges through a vulnerable cronjob.

---

# Questions

## Q1: How many ports are open?
### A: 3

We need to do an nmap scan `nmap -sV -sC -T4 -vv -p- 10.64.166.135`

![](../Img/Pasted%20image%2020260318103719.png)

---
## Q2: What is the version of nginx?
### A: 1.16.1

In the nmap scan we got it

![](../Img/Pasted%20image%2020260318103804.png)

---
## Q3: What is running on the highest port?
### A: Apache

In nmap scan

![](../Img/Pasted%20image%2020260318103852.png)

---
## Q4: Using GoBuster, find flag 1.
### A: flag{f1rs7_fl4g}

Using gobuster we find this

![](../Img/Pasted%20image%2020260318105228.png)

It takes us here

![](../Img/Pasted%20image%2020260318105342.png)

Nothing on the source code

We continue to use gobuster on the discovered directory

![](../Img/Pasted%20image%2020260318110834.png)

It takes us to another image

![](../Img/Pasted%20image%2020260318110858.png)

But this one has something hidden

![](../Img/Pasted%20image%2020260318110929.png)

Decode it

![](../Img/Pasted%20image%2020260318110940.png)

---
## Q5: Further enumerate the machine, what is flag 2?
### A: 

Since there is nothing more in port 80 we move to port 56624

![](../Img/Pasted%20image%2020260318114516.png)

Normal looking page but in the source code

![](../Img/Pasted%20image%2020260318114615.png)

If we take the hint and try to decode it from base we will find that it's in base62

![](../Img/Pasted%20image%2020260318115430.png)

If we keep reading the code we will also find this

![](../Img/Pasted%20image%2020260318115611.png)



## Q6: Crack the hash with easypeasy.txt, What is the flag 3?
### A: flag{9fdafbd64c47471a8f54cd3fc64cd312}

Found in Q5

---
## Q7: What is the hidden directory?
### A: 

## Q8: Using the wordlist that provided to you in this task crack the hash  
what is the password?
### A: 

## Q9: What is the password to login to the machine via SSH?
### A: 

## Q10: What is the user flag?
### A: 

## Q11: What is the root flag?
### A: 