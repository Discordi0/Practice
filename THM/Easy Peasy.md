
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
### A: 



## Q5: Further enumerate the machine, what is flag 2?
### A: 

## Q6: Crack the hash with easypeasy.txt, What is the flag 3?
### A: 

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