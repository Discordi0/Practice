
Exploit a Windows machine in this beginner level challenge.

This task involves you, paying attention to details and finding the 'keys to the castle'.

This room is designed for beginners, however, everyone is welcomed to try it out!

Enjoy the Anthem.

In this room, you don't need to brute force any login page. Just your preferred browser and Remote Desktop.

Please give the box up to 5 minutes to boot and configure.

---

# Questions

## Q1: What port is for the web server?
### A: 80

We do an nmap scan on the machine

Before the scan even finishes we can see the port

![](../Img/Pasted%20image%2020260320134718.png)

---
## Q2: What port is for remote desktop service?
### A: 3389

We got it in the nmap scan in Q1

---
## Q3: What is a possible password in one of the pages web crawlers check for?
### A: 

Visiting the page this is what we find

![](../Img/Pasted%20image%2020260320135047.png)

Checking the source code i found this

![](../Img/Pasted%20image%2020260320135649.png)



## Q4: What CMS is the website using?
### A: 

## Q5: What is the domain of the website?
### A: 

## Q6: What's the name of the Administrator
### A: 

## Q7: Can we find find the email address of the administrator?
### A: 

## Q8: What is flag 1?
### A: 

## Q9: What is flag 2?
### A: 

## Q10: What is flag 3?
### A: 

## Q11: What is flag 4?
### A: 

## Q12: Gain initial access to the machine, what is the contents of user.txt?
### A: 

## Q13: Can we spot the admin password?
### A: 

## Q14: Escalate your privileges to root, what is the contents of root.txt?
### A: 
