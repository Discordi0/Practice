
# Sherlock Scenario

LeStrade passes a disk image to Holmes. It's one of the identified breach points, now showing abnormal CPU activity and anomalies in process logs.

# About

In this Sherlock players will investigate KAPE output to see the Windows management instrumentation artifacts and persistence left by a Threat actor using the machine to pivot to an internal workstation.

---

# Questions

## Q1: What was the first (non cd) command executed by the attacker on the host?

### A: systeminfo

To see the PS command history (bc cmd doesn't store it) we need to check `C:\Users\<Nombre_Usuario>\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt`

![](../../Img/Pasted%20image%2020260311181615.png)

This did not give us the answer that we where looking for

Next we would need to check the logs in search for some event id that could give us the answer

Opening the Security logs in `C:\Windows\System32\winevet\logs\` and searching for cmd.exe (bc here cmd commands are stored, not only PS like what i did first) we get this.

![](../../Img/Pasted%20image%2020260311183047.png)

Filtering for evt id 4688 and the only user that this machine has (the only one that it's not default), then searching for cmd.exe we can find the answer.

![](../../Img/Pasted%20image%2020260311184410.png)

---

## Q2: Which parent process (full path) spawned the attacker’s commands?

### A:  C:\Windows\System32\wbem\WmiPrvSE.exe

We can find this in the same log.

---

## Q3: Which remote-execution tool was most likely used for the attack?

### A: wmiexec.py

Searching for "WmiPrvSE.exe" uses in hacking attacks i found that Impacket has a tool that utilices this service. (read more about it here: https://attack.mitre.org/software/S0357/)

---

## Q4: What was the attacker’s IP address?

### A: 10.129.242.110

Searching for event id 4624 (log on event id), then searching for some event with an ip in it.

![](../../Img/Pasted%20image%2020260311190821.png)

---

## Q5: The attacker established multiple persistence mechanisms. What is set as the name of the earliest one created?

### A: SysHelper Update

A common persistence techniques for windows machines is creating a scheduled task, so we need to check if there is one (C:\Windows\System32\Tasks)

![](../../Img/Pasted%20image%2020260313134324.png)

At first glance we can see that there is one that is not like the others

Opening it we can see that it tries some kind of bypass

![](../../Img/Pasted%20image%2020260313134514.png)

---

## Q6: Identify the script executed by the persistence mechanism.

### A: C:\Users\Werni\Appdata\Local\JM.ps1

We already saw it in the above question.

---

## Q7: What local account did the attacker create?

### A: svc_netupd

For account creation we can search for event id 4720

![](../../Img/Pasted%20image%2020260313135109.png)

To know which one is it we need to read them and check who (the username) created the account

![](../../Img/Pasted%20image%2020260313135232.png)

---

## Q8: What domain name did the attacker use for credential exfiltration?

### A: NapoleonsBlackPearl.htb

This one we got (i did but did not put it here) in Q5 or Q6 if we went to the file and opened it.

![](../../Img/Pasted%20image%2020260313135512.png)

---

## Q9: What password did the attacker's script generate for the newly created user?

### A: Watson_20250824160509

How the password was created it's in the same script we looked at earlier

![](../../Img/Pasted%20image%2020260313135825.png)

We only have the first part of the password, for the second one we need to know when the user was created, for that we need to check the time on the event in Q7

![](../../Img/Pasted%20image%2020260313140029.png)

I tried to answer with that time and it didn't work, i assume it's because there is a time difference so for that i use regitry explorer (https://ericzimmerman.github.io/#!index.md)

Go to where the timezone info it's located (ROOT/ControlSet001/Control/TimeZoneInformation/) and check for the entry "TimeZoneKeyName"

![](../../Img/Pasted%20image%2020260313141106.png)

Convert the time and u got ur answer

---

## Q10: What was the IP address of the internal system the attacker pivoted to?

### A: 



## Q11: Which TCP port on the victim was forwarded to enable the pivot?

### A: 

## Q12: What is the full registry path that stores persistent IPv4→IPv4 TCP listener-to-target mappings?

### A: 

## Q13: What is the MITRE ATT&CK ID associated with the previous technique used by the attacker to pivot to the internal system?

### A: 

## Q14: Before the attack, the administrator configured Windows to capture command line details in the event logs. What command did they run to achieve this?

### A: 