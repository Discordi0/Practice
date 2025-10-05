
##### Sherlock Scenario

Susan works at the Research Lab in Forela International Hospital. A Microsoft Defender alert was received from her computer, and she also mentioned that while extracting a document from the received file, she received tons of errors, but the document opened just fine. According to the latest threat intel feeds, WinRAR is being exploited in the wild to gain initial access into networks, and WinRAR is one of the Software programs the staff uses. You are a threat intelligence analyst with some background in DFIR. You have been provided a lightweight triage image to kick off the investigation while the SOC team sweeps the environment to find other attack indicators.


## Questions:


Q1: What is the CVE assigned to the WinRAR vulnerability exploited by the RomCom threat group in 2025?

A: CVE-2025-8088

With a internet search (WinRAR Romcom 2025) i got this. (https://socprime.com/es/blog/detect-cve-2025-8088-exploitation-for-romcom-delivery/)

![](../../Img/Pasted%20image%2020251005201425.png)

Q2: What is the nature of this vulnerability?

A: Path Traversal

Searching that CVE i got it. (https://nvd.nist.gov/vuln/detail/CVE-2025-8088)

![](../../Img/Pasted%20image%2020251005201544.png)

Q3: What is the name of the archive file under Susan's documents folder that exploits the vulnerability upon opening the archive file?

A: 

First we need to get the $MFT file. The provided .zip contains a .vhdx file, i just double click it (on Windows), and searched for the $MFT.
I used MFTECmd.exe to get a .csv file, and with that i used Timeline Explorer.

We are searching for a file in documents under Susan's user, so we start there.

![](../../Img/Pasted%20image%2020251005202759.png)



Q4: When was the archive file created on the disk?

A: 

Q5: When was the archive file opened?

A: 

Q6: What is the name of the decoy document extracted from the archive file, meant to appear legitimate and distract the user?

A: 

Q7: What is the name and path of the actual backdoor executable dropped by the archive file?

A: 

Q8: The exploit also drops a file to facilitate the persistence and execution of the backdoor. What is the path and name of this file?

A: 

Q9: What is the associated MITRE Technique ID discussed in the previous question?

A: 

Q10: When was the decoy document opened by the end user, thinking it to be a legitimate document?

A: 
