
Welcome to the Light database application!

---

# Questions

## Q1: What is the admin username?
### A: 


As per the instructions we connect using nc

![](../Img/Pasted%20image%2020260316171715.png)

After i did an nmap scan to check

![](../Img/Pasted%20image%2020260316172200.png)

i tried to ssh with the gathered credentials and got this

![](../Img/Pasted%20image%2020260316172232.png)

Seems like it's not going to work

We know that we are working on a DB so i went back to the nc connection and tried different payloads (https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/SQL%20Injection/) (https://dev.to/onyxwizard/examining-the-database-in-sql-injection-attacks-7ck)

![](../Img/Pasted%20image%2020260316174611.png)

After i got the sql version i need to check the tables names

![](../Img/Pasted%20image%2020260316175124.png)

I tried other method and got this

![](../Img/Pasted%20image%2020260316175459.png)

Now i went to get the a username and password

![](../Img/Pasted%20image%2020260316175651.png)

---
## Q2: What is the password to the username mentioned in question 1?
### A: 

Got it in last screenshot Q1

---
## Q3: What is the flag?
### A: 

This must be on the other table (usertable)

![](../Img/Pasted%20image%2020260316175942.png)

Usertable seems to have the same structure as admintable

![](../Img/Pasted%20image%2020260316180125.png)

Wasn't there

So i went back and check for other passwords in user and admin tables since i only know usernames and i can != to check for other passwords. I found it

![](../Img/Pasted%20image%2020260316180427.png)

Tags: [Nmap](../Index/Nmap.md) [SQLi](../Index/SQLi.md) 
