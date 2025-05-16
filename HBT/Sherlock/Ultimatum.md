
##### Sherlock Scenario

One of the Forela WordPress servers was a target of notorious Threat Actors (TA). The website was running a blog dedicated to the Forela Social Club, where Forela employees can chat and discuss random topics. Unfortunately, it became a target of a threat group. The SOC team believe this was due to the blog running a vulnerable plugin. The IT admin already followed the acquisition playbook and triaged the server for the security team. Ultimately (no pun intended) it is your responsibility to investigate the incident. Step in and confirm the culprits behind the attack and restore this important service within the Forela environment.


Q1: Which security scanning tool was utilized by the attacker to fingerprint the blog website?

A: wpscan/3.8.24

Seeing that this is a WP server, i searched for the WP logs.
I found them here (C:\Users\*******\Documents\Practice\Ultimatum\Logs\ip-172-31-11-131-20230808-0937-var-log.tar\ip-172-31-11-131-20230808-0937-var-log\var\log\apache2).

Looking through the file i got the answer.

![](../../Img/Pasted%20image%2020250516174444.png)

Q2: Which CVE was exploited by the attacker?

A: CVE-2023-3460

Since it's likely that the attack was because a vulnerable plugin, i searched for the plugins.

![](../../Img/Pasted%20image%2020250516174901.png)

We can see that the tool found a plugin named ultimate member, then proceded to attack it.
We can also see that the version of the plugin it's 2.6.4

Googling the plugin name and version for a CVE i found this.
https://wpscan.com/blog/hacking-campaign-actively-exploiting-ultimate-member-plugin/


Q3: What was the IP Address utilized by the attacker to exploit the CVE?

A: 23.106.60.163

We can see it in the logs where at the beginning it was the attacker ip, then it changed once the system was compromised.

![](../../Img/Pasted%20image%2020250516175707.png)

Q4: What is the name of the backdoor user added to the blog as part of the exploitation process?

A: Secragon

We can see it when the attacker tried to register.

![](../../Img/Pasted%20image%2020250516175945.png)

Q5: After the exploit, the SOC team observed that the attacker's IP address changed and from the logs, it seems that the attacker manually explored the website after logging in. The SOC team believes that the previous IP seen during exploitation was a public cloud IP. What is the IP Address the attacker used after logging in to the site?

A: 198.16.74.45

As i said in Q3 we can see that the attacker changed ip.

Q6: The SOC team has suspicions that the attacker added a web shell for persistent access. Confirm the full path of the web shell on the server.

A: /var/www/html/wp-content/themes/twentytwentythree/patterns/hidden-comments.php

Near the end of the access.log file we can see a lot of POST request together.
They seem to follow a theme (lol).

![](../../Img/Pasted%20image%2020250516180712.png)

They reference a hidden-comments theme N° 2023.

![](../../Img/Pasted%20image%2020250516180856.png)

So i just started searching every log for that name as it seem to be the only thing that the attacker left.
I found it in the ip-172-31-11-131-20230808-0937-pot-webshell-first-1000.txt file.

![](../../Img/Pasted%20image%2020250516182013.png)
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

