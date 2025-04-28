
##### Sherlock Scenario

Forela's Network is constantly under attack. The security system raised an alert about an old admin account requesting a ticket from KDC on a domain controller. Inventory shows that this user account is not used as of now so you are tasked to take a look at this. This may be an AsREP roasting attack as anyone can request any user's ticket which has preauthentication disabled.


Q1: When did the ASREP Roasting attack occur, and when did the attacker request the Kerberos ticket for the vulnerable user?

A: 2024-05-29 06:36:40

Event id 4768 y 4769 are the ones to look for, it also seems like i need to search for RC4 encryption (https://attack.mitre.org/techniques/T1558/004/)
The first and only one with that description.

![](../../Img/Pasted%20image%2020250428190703.png)

![](../../Img/Pasted%20image%2020250428190719.png)

Q2: Please confirm the User Account that was targeted by the attacker.

A: arthur.kyle

It's in the Q1 screenshot, it also seems like this user acc was the only one "user created", and the domain name was sus too.

![](../../Img/Pasted%20image%2020250428190855.png)

![](../../Img/Pasted%20image%2020250428190909.png)

![](../../Img/Pasted%20image%2020250428190923.png)

Q3: What was the SID of the account?

A: S-1-5-21-3239415629-1862073780-2394361899-1601

It's under EventData in Details tab

![](../../Img/Pasted%20image%2020250428190937.png)

Q4: It is crucial to identify the compromised user account and the workstation responsible for this attack. Please list the internal IP address of the compromised asset to assist our threat-hunting team.

A: 172.17.79.129

Same

![](../../Img/Pasted%20image%2020250428191017.png)

Q5: We do not have any artifacts from the source machine yet. Using the same DC Security logs, can you confirm the user account used to perform the ASREP Roasting attack so we can contain the compromised account/s?

A: happy.grunwald

Deleting the event id filter and looking at the time of the entries, we see that after the kerberos auth, there is a kerberos ticket.

![](../../Img/Pasted%20image%2020250428191246.png)
