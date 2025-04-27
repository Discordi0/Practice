
##### Sherlock Scenario

Forela's domain controller is under attack. The Domain Administrator account is believed to be compromised, and it is suspected that the threat actor dumped the NTDS.dit database on the DC. We just received an alert of vssadmin being used on the DC, since this is not part of the routine schedule we have good reason to believe that the attacker abused this LOLBIN utility to get the Domain environment's crown jewel. Perform some analysis on provided artifacts for a quick triage and if possible kick the attacker as early as possible.



Q1: Attackers can abuse the vssadmin utility to create volume shadow snapshots and then extract sensitive files like NTDS.dit to bypass security mechanisms. Identify the time when the Volume Shadow Copy service entered a running state.

A: 2024-05-14 03:42:16

Event id 7036 it's the one we have to look for. Search through the result until you find the Shadow Copy service.

![](../../Img/Pasted%20image%2020250427145931.png)

Q2: When a volume shadow snapshot is created, the Volume shadow copy service validates the privileges using the Machine account and enumerates User groups. Find the two user groups the volume shadow copy process queries and the machine account that did it.

A: Administrators, Backup Operators, DC01$

Event id 4799 it's the user group enumeration one. Using the time frame of the previous question and checking the process name we find the answer.

![](../../Img/Pasted%20image%2020250427150656.png)

![](../../Img/Pasted%20image%2020250427150644.png)

Q3: Identify the Process ID (in Decimal) of the volume shadow copy service process.

A: 4496

Make 0x1190 decimal

![](../../Img/Pasted%20image%2020250427150855.png)

Q4: Find the assigned Volume ID/GUID value to the Shadow copy snapshot when it was mounted.

A: {06c4a997-cca8-11ed-a90f-000c295644f9}

This AI say it's event id 4

![](../../Img/Pasted%20image%2020250427151758.png)

Looks like i don't have this.

![](../../Img/Pasted%20image%2020250427151927.png)

But looking for shadow copy i found it

![](../../Img/Pasted%20image%2020250427152032.png)

![](../../Img/Pasted%20image%2020250427152041.png)

Q5: Identify the full path of the dumped NTDS database on disk.

A: C:\Users\Administrator\Documents\backup_sync_Dc\Ntds.dit

I don't think that this is going to be in one of the logs file provided, luckily there is an MFT file.
Parsing that and opening with Timeline Explorer. We search for ntds and find it.
The \Users path seams like the one created by a user.

![](../../Img/Pasted%20image%2020250427152430.png)

Q6: When was newly dumped ntds.dit created on disk?

A: 2024-05-14 03:44:22

Same entry, but in the Created column.

![](../../Img/Pasted%20image%2020250427152542.png)


Q7: A registry hive was also dumped alongside the NTDS database. Which registry hive was dumped and what is its file size in bytes?

A: SYSTEM, 17563648

We search for the path on the Parent Path column (bc it's the user created one), and find only 1 other file.

![](../../Img/Pasted%20image%2020250427152801.png)

And it's size.

![](../../Img/Pasted%20image%2020250427152816.png)
