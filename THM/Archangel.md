
Boot2root, Web exploitation, Privilege escalation, LFI


---

# Questions

## Q1: Find a different hostname
### A: mafialive.thm

So first i do a quick default ports scan `nmap -A -T4 -vv 10.64.171.27`

![](../Img/Pasted%20image%2020260315140000.png)

We found port 80 so we need to check it out

In the web page we find this

![](../Img/Pasted%20image%2020260315143439.png)

---
## Q2: Find flag 1
### A: 

For this one we need to add that hostname to our "etc/hosts" file and access it

![](../Img/Pasted%20image%2020260315143952.png)

---
## Q3: Look for a page under development
### A: 

Now that we have a domain we can use ffuf or gobuster to check for files


## Q4: Find flag 2
### A: 

## Q5: Get a shell and find the user flag
### A: 

## Q6: Get User 2 flag
### A: 

## Q7: Root the machine and find the root flag
### A: 
