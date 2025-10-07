
##### Sherlock Scenario

Talion suspects that the threat actor carried out anti-virtualization checks to avoid detection in sandboxed environments. Your task is to analyze the event logs and identify the specific techniques used for virtualization detection. Byte Doctor requires evidence of the registry checks or processes the attacker executed to perform these checks.

## Questions:

### Q1: Which WMI class did the attacker use to retrieve model and manufacturer information for virtualization detection?

#### A: Win32_ComputerSystem

Provided with the scenario comes a .zip file with 2 .evtx inside, Powershell and Powershell Operational.

Reading through this article (https://vulnerx.com/malware-evasion-wmi/) i can see that it uses `Get-WmiObject` in all of its querys, so let's search for that in the Powershell evt.

![](../../Img/Pasted%20image%2020251007005501.png)

In the 3rd try we can find the class that was mentioned in the article.

___

### Q2: Which WMI query did the attacker execute to retrieve the current temperature value of the machine?

#### A: 


As per this article (https://stackoverflow.com/questions/45736193/how-can-we-get-a-cpu-temperature-through-wmi) we should be looking for 
### Q3: The attacker loaded a PowerShell script to detect virtualization. What is the function name of the script?

#### A: 

### Q4: Which registry key did the above script query to retrieve service details for virtualization detection?

#### A: 

### Q5: The VM detection script can also identify VirtualBox. Which processes is it comparing to determine if the system is running VirtualBox?

#### A: 

### Q6: The VM detection script prints any detection with the prefix 'This is a'. Which two virtualization platforms did the script detect?

#### A: 
