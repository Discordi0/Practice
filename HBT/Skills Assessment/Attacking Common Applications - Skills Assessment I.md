
During a penetration test against the company Inlanefreight, you have performed extensive enumeration and found the network to be quite locked down and well-hardened. You come across one host of particular interest that may be your ticket to an initial foothold. Enumerate the target host for potentially vulnerable applications, obtain a foothold, and submit the contents of the flag.txt file to complete this portion of the skills assessment.

## Questions.

### Q1: What vulnerable application is running?
#### A: Tomcat

First i did an nmap scan 'nmap -p- -sCV --open 10.129.201.89'

![](../../Img/Pasted%20image%2020251127140405.png)

![](../../Img/Pasted%20image%2020251127140428.png)

We can see that there are multiple open ports, taking into consideration the lessons of the module, there should be a couple that caught our attention.

---

### Q2: What port is this application running on?
#### A: 8080

It's in the nmap scan

---

### Q3: What version of the application is in use?
#### A: 9.0.0.M1

Same nmap scan

---

### Q4: Exploit the application to obtain a shell and submit the contents of the flag.txt file on the Administrator desktop.
#### A: 

Searching for a exploit for that version of Tomcat i found this page: https://tomcat.apache.org/security-9.html
Here i found a cve that could work.

![](../../Img/Pasted%20image%2020251127142228.png)

After reading this: https://github.com/setrus/CVE-2019-0232 and this: https://github.com/jaiguptanick/CVE-2019-0232
I fuzzed (?) the /cgi directory to see if it could be exploited. 'ffuf -w /home/discordio/Wordlists/discovery/common.txt -u http://10.129.201.89:8080/cgi/FUZZ.bat
'

![](../../Img/Pasted%20image%2020251127143316.png)

Now i had two options. Use meta


