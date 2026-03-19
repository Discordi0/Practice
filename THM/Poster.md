
The sys admin set up a rdbms in a safe way.

---

# Questions

## Q1: What is the rdbms installed on the server?
### A: 

For this first question we run an nmap scan `nmap -sV -sC -p- -T5 -vv 10.64.131.140`


![](../Img/Pasted%20image%2020260319103804.png)


## Q2: What port is the rdbms running on?
### A: 

## Q3: Metasploit contains a variety of modules that can be used to enumerate in multiple rdbms, making it easy to gather valuable information.
### A: 

## Q4: After starting Metasploit, search for an associated auxiliary module that allows us to enumerate user credentials. What is the full path of the modules (starting with auxiliary)?
### A: 

## Q5: What are the credentials you found?  example: user:password
### A: 

## Q6: What is the full path of the module that allows you to execute commands with the proper user credentials (starting with auxiliary)?
### A: 

## Q7: Based on the results of #6, what is the rdbms version installed on the server?
### A: 

## Q8: What is the full path of the module that allows for dumping user hashes (starting with auxiliary)?
### A: 

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
