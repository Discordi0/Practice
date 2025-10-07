
## Sherlock Scenario

Byte Doctor Reyes is investigating a stealthy post-breach attack where several expected security logs and Windows Defender alerts appear to be missing. He suspects the attacker employed defense evasion techniques to disable or manipulate security controls, significantly complicating detection efforts. Using the exported event logs, your objective is to uncover how the attacker compromised the system's defenses to remain undetected.

## Questions: 


### Q1: The attacker disabled LSA protection on the compromised host by modifying a registry key. What is the full path of that registry key?

#### A: HKLM\SYSTEM\CurrentControlSet\Control\LSA

Reading through this blog post (https://www.elevenforum.com/t/enable-or-disable-local-security-authority-lsa-protection-in-windows-11.11104/) we can see that in option three there are strings in the commands that are always present, so we use one of those to check the logs.

![](../../Img/Pasted%20image%2020251007163435.png)

___

### Q2: Which PowerShell command did the attacker first execute to disable Windows Defender?

#### A: Set-MpPreference -DisableIOAVProtection $true -DisableEmailScanning $true -DisableBlockAtFirstSeen $true

Using good old trusty Google again i came across this. (https://powershellfaqs.com/disable-windows-defender-using-powershell/).
As per Q1 i used the string present in most commands `Set-MpPreference `.

There was a lot of events in the log that have that string in them, but we need to check the time of the Q1 event to get to the answer.

![](../../Img/Pasted%20image%2020251007164300.png)

___

### Q3: The attacker loaded an AMSI patch written in PowerShell. Which function in the DLL is being patched by the script to effectively disable AMSI?

#### A: AmsiScanBuffer

At a quick glance there wasn't something specific to search for so i just did a search for .dll in the logs.

The first result seem to me to be the correct one but i couldn't find the answer.

![](../../Img/Pasted%20image%2020251007164728.png)

After a little while i got it by removing the + sign.

___

### Q4: Which command did the attacker use to restart the machine in Safe Mode?

#### A: 



### Q5: Which PowerShell command did the attacker use to disable PowerShell command history logging?

#### A: 

