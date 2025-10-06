
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

A: Pathology-Department-Research-Records.rar

First we need to get the $MFT file. The provided .zip contains a .vhdx file, i just double click it (on Windows), and searched for the $MFT.
I used MFTECmd.exe to get a .csv file, and with that i used Timeline Explorer.

We are searching for a file in documents under Susan's user, so we start there.

![](../../Img/Pasted%20image%2020251005202759.png)

We have 2 suspicious files, the pdf was created after the rar so i assume that the .rar is the culprit.

![](../../Img/Pasted%20image%2020251005203257.png)

Q4: When was the archive file created on the disk?

A: 2025-09-02 08:13:50

Q3 2nd screenshot.

Q5: When was the archive file opened?

A: 2025-09-02 08:14:04

For this onw we need to check the Last Record Change0x10

![](../../Img/Pasted%20image%2020251005204753.png)

Q6: What is the name of the decoy document extracted from the archive file, meant to appear legitimate and distract the user?

A: Genotyping_Results_B57_Positive.pdf

This one would have to be the .pdf file we found in Q3.

Q7: What is the name and path of the actual backdoor executable dropped by the archive file?

A: C:\Users\Susan\Appdata\Local\ApbxHelper.exe

I couldn't find this one in the $MFT file, so i had to check the $J (USN Journal).
With that file i checked for files created at the same time as the .pdf  ([Update Timestamp] >= #2025-09-02 08:14:00# And [Update Timestamp] < #2025-09-02 08:15:00# And Contains([Update Reasons], 'FileCreate')).

![](../../Img/Pasted%20image%2020251005212613.png)

We can see a suspicious .exe file.

Q8: The exploit also drops a file to facilitate the persistence and execution of the backdoor. What is the path and name of this file?

A: 

Q9: What is the associated MITRE Technique ID discussed in the previous question?

A: 

Q10: When was the decoy document opened by the end user, thinking it to be a legitimate document?

A: 
