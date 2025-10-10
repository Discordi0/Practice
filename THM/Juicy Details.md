
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

##### A: nmap, hydra, sqlmap, curl, feroxbuster

We need to open access.log and check.

The first thing we can see.

![](../Img/Pasted%20image%2020251010000522.png)

Next it's just normal traffic until we get this.

![](../Img/Pasted%20image%2020251010000624.png)

After that it's normal traffic again until this.

![](../Img/Pasted%20image%2020251010000708.png)

Then we have all the sqlmap traffic follow by a couple of entries of normality and then this.

![](../Img/Pasted%20image%2020251010000838.png)

And lastly.

![](../Img/Pasted%20image%2020251010000907.png)

___

#### Q2: What endpoint was vulnerable to a brute-force attack?

##### A: /rest/user/login

Not sure if it is vulnerable but the attacker sure tried.

![](../Img/Pasted%20image%2020251010002039.png)

___

#### Q3: What endpoint was vulnerable to SQL injection?

##### A: /rest/products/search

This would be where the attacker used the SQLi tool.

![](../Img/Pasted%20image%2020251010002210.png)

___

#### Q4: What parameter was used for the SQL injection?

##### A: q

It can be see in the above's question screenshot.

___

#### Q5: What endpoint did the attacker try to use to retrieve files? (Include the /)

##### A: 

We can see where the attacker tried to retieve specific files.

![](../Img/Pasted%20image%2020251010002619.png)

This can be corroborated by looking at the vsftpd.log file where we can see a download happening.

![](../Img/Pasted%20image%2020251010002747.png)

___



