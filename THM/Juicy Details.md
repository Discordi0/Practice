
## **Introduction**

You were hired as a SOC Analyst for one of the biggest Juice Shops in the world and an attacker has made their way into your network. 

Your tasks are:

- Figure out what techniques and tools the attacker used
- What endpoints were vulnerable
- What sensitive data was accessed and stolen from the environment  

An IT team has sent you a **zip file** containing logs from the server. Download the attached file, type in "I am ready!" and get to work! There's no time to lose!

___

## **Reconnaissance**

Analyze the provided log files.

Look carefully at:

- What tools the attacker used
- What endpoints the attacker tried to exploit
- What endpoints were vulnerable

### Questions: 

#### Q1: What tools did the attacker use? (Order by the occurrence in the log)

##### A: nmap, hydra, 

We need to open access.log and check.

The first thing we can see.

![](../Img/Pasted%20image%2020251010000522.png)

Next it's just normal traffic until we get this.

![](../Img/Pasted%20image%2020251010000624.png)


#### Q2: What endpoint was vulnerable to a brute-force attack?

##### A: 

#### Q3: What endpoint was vulnerable to SQL injection?

##### A: 

#### Q4: What parameter was used for the SQL injection?

##### A: 

#### Q5: What endpoint did the attacker try to use to retrieve files? (Include the /)

##### A: 