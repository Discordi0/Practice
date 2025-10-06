##### Sherlock Scenario

Alonzo Spotted Weird files on his computer and informed the newly assembled SOC Team. Assessing the situation it is believed a Kerberoasting attack may have occurred in the network. It is your job to confirm the findings by analyzing the provided evidence. You are provided with: 1- Security Logs from the Domain Controller 2- PowerShell-Operational Logs from the affected workstation 3- Prefetch Files from the affected workstation


Q1: Analyzing Domain Controller Security Logs, can you confirm the date & time when the kerberoasting activity occurred?

A: 2024-05-21 03:18:09

Looking for the event id 4769 inside the log file, we see that there is only one entry that stands out.

![](../../Img/Pasted%20image%2020250428191948.png)

![](../../Img/Pasted%20image%2020250428192002.png)

Q2: What is the Service Name that was targeted?

A: MSSQLService

It's in the screenshot.

Q3: It is really important to identify the Workstation from which this activity occurred. What is the IP Address of the workstation?

A: 172.17.79.129

Same screenshot.

Q4: Now that we have identified the workstation, a triage including PowerShell logs and Prefetch files are provided to you for some deeper insights so we can understand how this activity occurred on the endpoint. What is the name of the file used to Enumerate Active directory objects and possibly find Kerberoastable accounts in the network?

A: powerview.ps1

Looking at the powershell log, we can see that the attacker tried to run a script.

![](../../Img/Pasted%20image%2020250428192318.png)

Tried a bypass

![](../../Img/Pasted%20image%2020250428192414.png)

Then what it seems to be a big script executed.

![](../../Img/Pasted%20image%2020250428192451.png)

Q5: When was this script executed?

A: 2024-05-21 03:16:32

Same entry, Details tab.

![](../../Img/Pasted%20image%2020250428192522.png)

Q6: What is the full path of the tool used to perform the actual kerberoasting attack?

A: C:\Users\Alonzo.spire\Downloads\Rubeus.exe

The log file doesn't say anything about the tool, Google says that Rubeus it's used for Kerberos.
Parsing the .pf files, and then opening the csv file in Timeline Explorer. We can search for the tool.
I assume that the tool it's in the downloads folder (bc that's where the script was too).

![](../../Img/Pasted%20image%2020250428193225.png)

Q7: When was the tool executed to dump credentials?

A: 2024-05-21 03:18:08

Same entry, under Run Time.

![](../../Img/Pasted%20image%2020250428193308.png)

