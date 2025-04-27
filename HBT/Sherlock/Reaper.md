
##### Sherlock Scenario

Our SIEM alerted us to a suspicious logon event which needs to be looked at immediately. The alert details were that the IP Address and the Source Workstation name were a mismatch. You are provided a network capture and event logs from the surrounding time around the incident timeframe. Corelate the given evidence and report back to your SOC Manager.


Q1: What is the IP Address for Forela-Wkstn001?

A: 172.17.79.129

Just opening the pncap file we see that nbns has the name we are looking for.

![](../../Img/Pasted%20image%2020250427163717.png)

Q2: What is the IP Address for Forela-Wkstn002?

A: 172.17.79.136

We filter for the protocol nbns and look for the other workstation

![](../../Img/Pasted%20image%2020250427164013.png)

Q3: What is the username of the account whose hash was stolen by attacker?

A: arthur.kyle

Logon event id is 4624.

![](../../Img/Pasted%20image%2020250427164313.png)

Filtering that event we have 11 entries. Search for the sus one.

![](../../Img/Pasted%20image%2020250427164427.png)

Q4: What is the IP Address of Unknown Device used by the attacker to intercept credentials?

A: 

Same entry.

![](../../Img/Pasted%20image%2020250427164522.png)

Q5: What was the fileshare navigated by the victim user account?

A: 

Q6: What is the source port used to logon to target workstation using the compromised account?

A: 

Q7: What is the Logon ID for the malicious session?

A: 

Q8: The detection was based on the mismatch of hostname and the assigned IP Address.What is the workstation name and the source IP Address from which the malicious logon occur?

A: 

Q9: At what UTC time did the the malicious logon happen?

A: 

Q10: What is the share Name accessed as part of the authentication process by the malicious tool used by the attacker?

A: 
