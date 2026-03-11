
# Sherlock Scenario

LeStrade passes a disk image to Holmes. It's one of the identified breach points, now showing abnormal CPU activity and anomalies in process logs.

# About

In this Sherlock players will investigate KAPE output to see the Windows management instrumentation artifacts and persistence left by a Threat actor using the machine to pivot to an internal workstation.

---

# Questions

## Q1: What was the first (non cd) command executed by the attacker on the host?

### A: 

To see the PS command history (bc cmd doesn't store it) we need to check `C:\Users\<Nombre_Usuario>\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt`

![](../../Img/Pasted%20image%2020260311181615.png)

This did not give us the answer that we where looking for

Next we would need to check the logs in search for some event id that could give us the answer



---

## Q2: Which parent process (full path) spawned the attacker’s commands?

### A: 

## Q3: Which remote-execution tool was most likely used for the attack?

### A: 

## Q4: What was the attacker’s IP address?

### A: 

## Q5: The attacker established multiple persistence mechanisms. What is set as the name of the earliest one created?

### A: 

## Q6: Identify the script executed by the persistence mechanism.

### A: 

## Q7: What local account did the attacker create?

### A: 

## Q8: What domain name did the attacker use for credential exfiltration?

### A: 

## Q9: What password did the attacker's script generate for the newly created user?

### A: 

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