
##### Sherlock Scenario

In this Sherlock, you will become acquainted with MFT (Master File Table) forensics. You will be introduced to well-known tools and methodologies for analyzing MFT artifacts to identify malicious activity. During our analysis, you will utilize the MFTECmd tool to parse the provided MFT file, TimeLine Explorer to open and analyze the results from the parsed MFT, and a Hex editor to recover file contents from the MFT.


Q1: Simon Stark was targeted by attackers on February 13. He downloaded a ZIP file from a link received in an email. What was the name of the ZIP file he downloaded from the link?

A: Stage-20240213T093324Z-001.zip

Parse the file and open it with Timeline Explorer.
Knowing it's a zip file, we filter for zip in the extension column.

![](../../Img/Pasted%20image%2020250429135848.png)

With the date filter we get this.

![](../../Img/Pasted%20image%2020250429140040.png)

It seems like invioces.zip came from the Stage file.

![](../../Img/Pasted%20image%2020250429140151.png)

Q2: Examine the Zone Identifier contents for the initially downloaded ZIP file. This field reveals the HostUrl from where the file was downloaded, serving as a valuable Indicator of Compromise (IOC) in our investigation/analysis. What is the full Host URL from where this ZIP file was downloaded?

A: https://storage.googleapis.com/drive-bulk-export-anonymous/20240213T093324.039Z/4133399871716478688/a40aecd0-1cf3-4f88-b55a-e188d5c1c04f/1/c277a8b4-afa9-4d34-b8ca-e1eb5e5f983c?authuser

With the zip filter in extension i couldn't find the identifier, filtering only for the name of the file gets the answer.

![](../../Img/Pasted%20image%2020250429140538.png)

Q3: What is the full path and name of the malicious file that executed malicious code and connected to a C2 server?

A: C:\Users\simon.stark\Downloads\Stage-20240213T093324Z-001\Stage\invoice\invoices\invoice.bat

In Q1 we found that the Stage file, created a directory of the same name. Filter that in the Parent path column.
There is a .bat file.

![](../../Img/Pasted%20image%2020250429140836.png)

Q4: Analyze the $Created0x30 timestamp for the previously identified file. When was this file created on disk?

A: 2024-02-13 16:38:39

Go to that column.

![](../../Img/Pasted%20image%2020250429140948.png)

Q5: Finding the hex offset of an MFT record is beneficial in many investigative scenarios. Find the hex offset of the stager file from Question 3.

A: 16E3000

Had to look at the hint for this one.
With the entry number of the file. multiply for 1024.

![](../../Img/Pasted%20image%2020250429141419.png)

Then convert that to Hex.

![](../../Img/Pasted%20image%2020250429141525.png)

Q6: Each MFT record is 1024 bytes in size. If a file on disk has smaller size than 1024 bytes, they can be stored directly on MFT File itself. These are called MFT Resident files. During Windows File system Investigation, its crucial to look for any malicious/suspicious files that may be resident in MFT. This way we can find contents of malicious files/scripts. Find the contents of The malicious stager identified in Question3 and answer with the C2 IP and port.

A: 43.204.110.203:6666

Googling around a little, it seems like you can open the MFT file with various tools, but to look for the Entry, you would normally use a hex editor.
I used HxD. Open th MFT file, go to the Entry.

![](../../Img/Pasted%20image%2020250429142503.png)