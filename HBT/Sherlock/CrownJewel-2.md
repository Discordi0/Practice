
##### Sherlock Scenario

Forela's Domain environment is pure chaos. Just got another alert from the Domain controller of NTDS.dit database being exfiltrated. Just one day prior you responded to an alert on the same domain controller where an attacker dumped NTDS.dit via vssadmin utility. However, you managed to delete the dumped files kick the attacker out of the DC, and restore a clean snapshot. Now they again managed to access DC with a domain admin account with their persistent access in the environment. This time they are abusing ntdsutil to dump the database. Help Forela in these chaotic times!!

___

### Q1: When utilizing ntdsutil.exe to dump NTDS on disk, it simultaneously employs the Microsoft Shadow Copy Service. What is the most recent timestamp at which this service entered the running state, signifying the possible initiation of the NTDS dumping process?

#### A: 2024-05-15 05:39:55

According with this forum post i need to be looking for event id 7036 in the system log file (https://learn.microsoft.com/en-us/answers/questions/262317/whats-the-audit-event-id-for-windows-service-start)

___

### Q2: Identify the full path of the dumped NTDS file.

#### A: C:\Windows\Temp\dump_tmp\Active Directory\ntds.dit

This one was interesting, first i found this article (https://www.hackthebox.com/blog/ntds-dumping-attack-detection), but since it's from HTB i feel like it's cheating. Then i found this one (https://rootguard.gitbook.io/cyberops/detection-engineering/ad-attack-detections-and-mitigations/dumping-ntds.dit), But non of those event id are in the logs.
So digging around a little bit more i found this (https://www.researchgate.net/figure/Targeted-Events_fig3_351088021).
With event id 325 i found it.

![](../../Img/Pasted%20image%2020250427141300.png)

___

### Q3: When was the database dump created on the disk?

#### A: 2024-05-15 05:39:56

Same entry, Details tab

![](../../Img/Pasted%20image%2020250427141328.png)

___

### Q4: When was the newly dumped database considered complete and ready for use?

#### A: 2024-05-15 05:39:58

This one was difficult, i never actually knew why when is dettached, it's ready.
Looking at the documentation that i could find about ESENT db i came across the functions that it utilizes. It seams that detachment (https://learn.microsoft.com/en-us/windows/win32/extensible-storage-engine/jetdetachdatabase-function) it's like the end of a posible process that a database could incur?.
First it's created or copied, it can be attached, then can be read or manipulated and then detached.
As i said, i don't know why when it's detached it's consider ready. i got it only by inference

ESENT event id 327.

![](../../Img/Pasted%20image%2020250427143110.png)

___

### Q5: Event logs use event sources to track events coming from different sources. Which event source provides database status data like creation and detachment?

#### A: ESENT

Some DB's have it's own event source, but a widely used tool to track this types of event is ESENT

Q6: When ntdsutil.exe is used to dump the database, it enumerates certain user groups to validate the privileges of the account being used. Which two groups are enumerated by the ntdsutil.exe process? Give the groups in alphabetical order joined by comma space.

A: Administrators, Backup Operators

Overlord's AI said this.

![](../../Img/Pasted%20image%2020250427143836.png)

The 2nd event id worked (4799).
Searching for ntds related entries we can find them.

![](../../Img/Pasted%20image%2020250427144121.png)

![](../../Img/Pasted%20image%2020250427144138.png)

Q7: Now you are tasked to find the Login Time for the malicious Session. Using the Logon ID, find the Time when the user logon session started.

A: 2024-05-15 05:36:31

Maybe if i knew more this would have been obvious, but i had to look at the hint to know that this is a domain env.
So looking at the kerberos event id 4768 (wich it's only 3), we search for anything abnormal. The only user acc that logs in it's the one that we look for.

![](../../Img/Pasted%20image%2020250427144720.png)

![](../../Img/Pasted%20image%2020250427144735.png)

Tags: [Windows Event Log](../../Index/Windows%20Event%20Log.md) 