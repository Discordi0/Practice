
## Sherlock Scenario

Byte Doctor Reyes is investigating a stealthy post-breach attack where several expected security logs and Windows Defender alerts appear to be missing. He suspects the attacker employed defense evasion techniques to disable or manipulate security controls, significantly complicating detection efforts. Using the exported event logs, your objective is to uncover how the attacker compromised the system's defenses to remain undetected.

## Questions: 


### Q1: The attacker disabled LSA protection on the compromised host by modifying a registry key. What is the full path of that registry key?

#### A: HKLM\SYSTEM\CurrentControlSet\Control\LSA

Reading through this blog post (https://www.elevenforum.com/t/enable-or-disable-local-security-authority-lsa-protection-in-windows-11.11104/) we can see that in option three there are strings in the commands that are always present, so we use one of those to check the logs.

![](../../Img/Pasted%20image%2020251007163435.png)

___

### Q2: Which PowerShell command did the attacker first execute to disable Windows Defender?

#### A: 

Using good old trusty Google again i came across this. (https://powershellfaqs.com/disable-windows-defender-using-powershell/).
As per Q1 i used the string present in most commands `Set-MpPreference `.

There was a lot of events in the log that could be

### Q3: The attacker loaded an AMSI patch written in PowerShell. Which function in the DLL is being patched by the script to effectively disable AMSI?

#### A: 

### Q4: Which command did the attacker use to restart the machine in Safe Mode?

#### A: 

### Q5: Which PowerShell command did the attacker use to disable PowerShell command history logging?

#### A: 

