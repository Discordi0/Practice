
##### Sherlock Scenario

One of the Forela WordPress servers was a target of notorious Threat Actors (TA). The website was running a blog dedicated to the Forela Social Club, where Forela employees can chat and discuss random topics. Unfortunately, it became a target of a threat group. The SOC team believe this was due to the blog running a vulnerable plugin. The IT admin already followed the acquisition playbook and triaged the server for the security team. Ultimately (no pun intended) it is your responsibility to investigate the incident. Step in and confirm the culprits behind the attack and restore this important service within the Forela environment.


Q1: Which security scanning tool was utilized by the attacker to fingerprint the blog website?

A: 



Q2: Which CVE was exploited by the attacker?

A: 

Q3: What was the IP Address utilized by the attacker to exploit the CVE?

A: 

Q4: What is the name of the backdoor user added to the blog as part of the exploitation process?

A: 

Q5: After the exploit, the SOC team observed that the attacker's IP address changed and from the logs, it seems that the attacker manually explored the website after logging in. The SOC team believes that the previous IP seen during exploitation was a public cloud IP. What is the IP Address the attacker used after logging in to the site?

A: 

Q6: The SOC team has suspicions that the attacker added a web shell for persistent access. Confirm the full path of the web shell on the server.

A: 

Q7: What was the value of the $shell variable in the web shell?

A: 

Q8: What is the size of the webshell in bytes?

A: 

Q9: The SOC team believes that the attacker utilized the webshell to get RCE on the server. Can you confirm the C2 IP and Port?

A: 

Q10: What is the process ID of the process which enabled the Threat Actor (TA) to gain hands-on access to the server?

A: 

Q11: What is the name of the script/tool utilized as part of internal enumeration and finding privilege escalation paths on the server?

A: 

