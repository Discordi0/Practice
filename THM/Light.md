
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


## Q2: What is the password to the username mentioned in question 1?
### A: 
## Q3: What is the flag?
### A: 