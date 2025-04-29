
##### Sherlock Scenario

In this Sherlock, you will familiarize yourself with Sysmon logs and various useful EventIDs for identifying and analyzing malicious activities on a Windows system. Palo Alto's Unit42 recently conducted research on an UltraVNC campaign, wherein attackers utilized a backdoored version of UltraVNC to maintain access to systems. This lab is inspired by that campaign and guides participants through the initial access stage of the campaign.


Q1: How many Event logs are there with Event ID 11?

A: 56

Open the log file, filter by the event id.

![](../../Img/Pasted%20image%2020250428194032.png)

Q2: Whenever a process is created in memory, an event with Event ID 1 is recorded with details such as command line, hashes, process path, parent process path, etc. This information is very useful for an analyst because it allows us to see all programs executed on a system, which means we can spot any malicious processes being executed. What is the malicious process that infected the victim's system?

A: 

Filter by the event id.
This .exe.exe file definitely is.

![](../../Img/Pasted%20image%2020250428194337.png)

Q3: Which Cloud drive was used to distribute the malware?

A: dropbox

Having the time of the event and with no idea what I'm looking for. I delete the filter ans search for events in that time frame.
Seem like dropbox it's the one.

![](../../Img/Pasted%20image%2020250428194930.png)

Q4: For many of the files it wrote to disk, the initial malicious file used a defense evasion technique called Time Stomping, where the file creation date is changed to make it appear older and blend in with other files. What was the timestamp changed to for the PDF file?

A: 2024-01-14 08:10:06

I have to look for event id 2 (https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/event.aspx?eventid=90002)
With the filter in place, just search for a pdf file.

![](../../Img/Pasted%20image%2020250428195250.png)


Q5: The malicious file dropped a few files on disk. Where was "once.cmd" created on disk? Please answer with the full path along with the filename.

A: C:\Users\CyberJunkie\AppData\Roaming\Photo and Fax Vn\Photo and vn 1.1.2\install\F97891C\WindowsVolume\Games\once.cmd

Lucky i saw once.cmd when i was searching for the Q4 answer.

![](../../Img/Pasted%20image%2020250428195352.png)

Q6: The malicious file attempted to reach a dummy domain, most likely to check the internet connection status. What domain name did it try to connect to?

A: www.example.com

With filter in event id 22 (DNS query).

![](../../Img/Pasted%20image%2020250428195635.png)

Q7: Which IP address did the malicious process try to reach out to?

A: 93.184.216.34

Seeing that this are sysmon logs, Google for it.

![](../../Img/Pasted%20image%2020250428195754.png)

Filter the log. There is only one

![](../../Img/Pasted%20image%2020250428195835.png)

Q8: The malicious process terminated itself after infecting the PC with a backdoored variant of UltraVNC. When did the process terminate itself?

A: 

Again, search for it.

![](../../Img/Pasted%20image%2020250428195913.png)



