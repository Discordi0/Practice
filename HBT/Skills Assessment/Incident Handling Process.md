
In the skills assessment, you are in the role of a junior incident responder and need to perform some tasks.

## [Triage the alerts](https://academy.hackthebox.com/beta/module/148/section/3954#triage-the-alerts)

TheHive is loaded with alerts related to the Insights Nexus breach. You are requested to triage them, starting with:

- Task 1: Create a new case in TheHive. Find all the alerts that are specific to the Insights Nexus breach scenario, and link the alerts in the case. This exercise introduces you to work in TheHive alerts and cases.  
    
- Task 2: Perform triage, enrichment, and correlation in TheHive. In the notes of an alert, you can add useful information for enrichment.  
    
- Task 3: One of the alerts related to Insights Nexus in TheHive contains some information in the notes. The netstat command output shows some connectivity to external IP addresses. You can validate this finding.

![TheHive case interface showing a “Comments” panel with a pasted netstat -ano snippet from host 10.10.5.23. Entries include TCP 127.0.0.1:5357 LISTENING, TCP 10.10.5.23:139 LISTENING, outbound TCP 10.10.5.23:52344 → 198.5.x.x:443 ESTABLISHED, 10.10.5.23:52345 → 203.0.x.x:4444 ESTABLISHED, UDP 10.10.5.23:123 listening, and SMB connections to 10.10.5.17:445 and 10.10.5.18:445 (ESTABLISHED/TIME_WAIT). Top bar shows controls (Create Case, language EN-UK, user HTB-ANALYST).](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/148/ir-netstat.png)

This output was captured after the host machine rejoined the domain following recovery. However, it is still connecting to an IP address. The analyst added this in the comments of the alert.

There are some further questions asked at bottom of this section.

## [Mapping to the Cyber Kill Chain](https://academy.hackthebox.com/beta/module/148/section/3954#mapping-to-the-cyber-kill-chain)

A user opens an attachment, which executes a downloader that writes an .exe file to `%AppData%`, creates a `Run` registry key, and later loads `VaultCli.dll` via a suspicious tool, exfiltrating credentials to an external IP. Your task is to map each step of the attack to the kill chain phase.

- Task 1: Map the file download, registry, and exfiltration activity to MITRE ATT&CK.
- Task 2: Check the alert related to Mimikatz in TheHive and identify the MITRE Technique ID.

## [Investigate the collected logs](https://academy.hackthebox.com/beta/module/148/section/3954#investigate-the-collected-logs)

- Task 1: Additionally, you are provided with some event log files (i.e., `logs-wazuh.zip`). One of the tasks is to decode some PowerShell commands and extract IOCs from them.
- Task 2: Identify the user who executed the suspicious PowerShell command.


## Questions.

### Q1: Open the alert "[InsightNexus] Admin Login via ManageEngine Web Console." Find the foreign IP address starting with "203" in the comments. Check VirusTotal for the information related to this IP address, and add the details as a comment in this alert. In VirusTotal, what is the name of the file starting with "Mango" in the Files Referring section?
#### A: MangoJava.exe

We need to login with the provided credentials.

After that we look in the alerts for the one in the question.

Once inside the alert we can see the comment with the ip.

![](../../Img/Pasted%20image%2020251128141748.png)

We search for that ip address in VirusTotal (https://www.virustotal.com/gui/ip-address/203.0.113.18)

We need to go to the Relations tab to find the answer.

![](../../Img/Pasted%20image%2020251128142229.png)

---

### Q2: In VirusTotal, go to the details of the IP address starting with "198." What is the name of the city shown in the Whois Lookup?
#### A: Los Angeles

We get this Ip in Q1.

We search it in VirusTotal (https://www.virustotal.com/gui/ip-address/198.51.100.24)

Go to the Details tab and search for it.

![](../../Img/Pasted%20image%2020251128142454.png)

---

### Q3: If malware downloads files from a C2 (Command and Control) server into the victim network, under what MITRE technique ID does this tool transfer technique fall? Type it as your answer. The format is T1***.
#### A: T1105

We need to go to the Mitre Matrix (https://attack.mitre.org/)

Under the Command and Control category search for it.

![](../../Img/Pasted%20image%2020251128142823.png)

---

### Q4: Open TheHive and check the rule ID 92153 related to the VaultCli.dll module. What is the MITRE technique ID for this activity? The format is T1***.
#### A: T1555

Search for the ID in TheHive.

![](../../Img/Pasted%20image%2020251128143057.png)

Inside this alert we can find the answer.

![](../../Img/Pasted%20image%2020251128143133.png)

---

### Q5: Download the "logs-wazuh.zip" file from resources, and identify the suspicious PowerShell command in the logs. Type the suspicious IP address after decoding the command.
#### A: 198.51.100.24

Download the attached .zip file, unzip it and open it with your preferred text editor.

Now inside search for the alert. (I searched for "powershell" because it got caught in a custom alert and sysmon ID 1 would get too many hits)

![](../../Img/Pasted%20image%2020251128143848.png)

Copy the enconded command and decode it. (i used cyberchef)

![](../../Img/Pasted%20image%2020251128143939.png)

---

### Q6: In the same file (i.e., logs-wazuh.zip), identify the user who executed the suspicious PowerShell command. The format is domain\user.
#### A: CORP\svc-update

It's the same alert as Q5, so just copy it. (Mind the format)

![](../../Img/Pasted%20image%2020251128144500.png)

