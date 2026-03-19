
The sys admin set up a rdbms in a safe way.

---

# Questions

## Q1: What is the rdbms installed on the server?
### A: 

For this first question we run an nmap scan `nmap -sV -sC -p- -T5 -vv 10.64.131.140`


![](../Img/Pasted%20image%2020260319103804.png)

![](../Img/Pasted%20image%2020260319103820.png)

We can see that in port 5432 what DB we have

--- 
## Q2: What port is the rdbms running on?
### A: 5432

We got it from the nmap scan in Q1

---
## Q3: Metasploit contains a variety of modules that can be used to enumerate in multiple rdbms, making it easy to gather valuable information.
### A: -

Ok, ty

---
## Q4: After starting Metasploit, search for an associated auxiliary module that allows us to enumerate user credentials. What is the full path of the modules (starting with auxiliary)?
### A: auxiliary/scanner/postgres/postgres_login

Since we know what we are looking for we can use the filter in metasploit to get better results

![](../Img/Pasted%20image%2020260319104544.png)

The question asks about enumeration so we know which one do we need

---
## Q5: What are the credentials you found?  example: user:password
### A: postgres:password

Since we know what module to use we just need to select it, change the options and run it

![](../Img/Pasted%20image%2020260319104915.png)

We just get 1 successful pair of credentials

---
## Q6: What is the full path of the module that allows you to execute commands with the proper user credentials (starting with auxiliary)?
### A: auxiliary/admin/postgres/postgres_sql

We use the filters again

![](../Img/Pasted%20image%2020260319105134.png)

We see that there are 3 that are not scanners, of the 3 there are 2 that relevant to the question

Using the info command we can read the description of a module

Description of module index 3

![](../Img/Pasted%20image%2020260319105728.png)

Description of module index 4

![](../Img/Pasted%20image%2020260319105752.png)

---
## Q7: Based on the results of #6, what is the rdbms version installed on the server?
### A: 9.5.21

Checking the module options we can see that it already comes with the version set

![](../Img/Pasted%20image%2020260319110016.png)

So we input the other necessary options and run it

![](../Img/Pasted%20image%2020260319110049.png)

---
## Q8: What is the full path of the module that allows for dumping user hashes (starting with auxiliary)?
### A: 

We go to the search with filters again



## Q9: How many user hashes does the module dump?
### A: 

## Q10: What is the full path of the module (starting with auxiliary) that allows an authenticated user to view files of their choosing on the server?
### A: 

## Q11: What is the full path of the module that allows arbitrary command execution with the proper user credentials (starting with exploit)?
### A: 

## Q12: Compromise the machine and locate user.txt
### A: 

## Q13: Escalate privileges and obtain root.txt
### A: 
