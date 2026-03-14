
A ctf for beginners, can you root me?

# Questions

## Q1: Scan the machine, how many ports are open?
### A: 2

With a simple nmap scan we can get the ports `nmap -A -vv 10.66.180.138`

![](../Img/Pasted%20image%2020260314155234.png)

---
## Q2: What version of Apache is running?
### A: 2.4.41

In the above screenshot we can see the version.

---
## Q3: What service is running on port 22?
### A: ssh

It's in Q1 screenshot

---
## Q4: Find directories on the web server using the GoBuster tool.
### A: 

I just used gobuster to search `gobuster dir -u http://10.66.180.138/ -w /usr/share/seclists/Discovery/Web-Content/combined_directories.txt`


## Q5: What is the hidden directory?
### A: 

## Q6: 
### A: 

## Q7: 
### A: 

## Q8: 
### A: 

## Q9: 
### A: 

