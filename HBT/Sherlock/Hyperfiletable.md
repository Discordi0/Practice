
##### Sherlock Scenario

There has been a new joiner in Forela, they have downloaded their onboarding documentation, however someone has managed to phish the user with a malicious attachment. We have only managed to pull the MFT record for the new user, are you able to triage this information?


Q1: What is the MD5 hash of the MFT?

A: 3730c2fedcdc3ecd9b83cbea08373226

Extract the mft.raw from the zip files. Then calculate the hash.

![](../../Img/Pasted%20image%2020250516190344.png)

Q2: What is the name of the only user on the system?

A: Randy Savage

MFTExplorer was taking too much time opening the mft file. With Timeline Explorer i got this.

![](../../Img/Pasted%20image%2020250516190733.png)

Q3: What is the name of the malicious HTA that was downloaded by that user?

A: Onboarding.hta

I filtered with Randy Savage in the parent path column and with .hta in the file name column and got it.

![](../../Img/Pasted%20image%2020250516190918.png)

Q4: What is the ZoneId of the download for the malicious HTA file?

A: 3

Under the Q3 entry there this file.

![](../../Img/Pasted%20image%2020250516191042.png)

And under Zone Id Contents.

![](../../Img/Pasted%20image%2020250516191104.png)

Q5: What is the download URL for the malicious HTA?

A: https://doc-10-8k-docs.googleusercontent.com/docs/securesc/9p3kedtu9rd1pnhecjfevm1clqmh1kc1/9mob6oj9jdbq89eegoedo0c9f3fpmrnj/1680708975000/04991425918988780232/11676194732725945250Z/1hsQhtmZJW9xZGgniME93H3mXZIV4OKgX?e=download&uuid=56e1ab75-ea1e-41b7-bf92-9432cfa8b645&nonce=u98832u1r35me&user=11676194732725945250Z&hash=j5meb42cqr57pa0ef411ja1k70jkgphq

Q4 screencshot.

Q6: What is the allocated size for the HTA file? (bytes)

A: 4096

In size it's 1144.

![](../../Img/Pasted%20image%2020250516191215.png)

But the "allocated" size would be 4096 since that it's the size that each registry can occupy per entry. So 1144 bein less that 4096. 4096 it's the allocated size.

Q7: What is the real size of the HTA file? (bytes)

A: 1144

Q6 screenshot.

Q8: When was the powerpoint presentation downloaded by the user?

A: 05/04/2023 13:11:49

Change the File Name filter for .ppt and look at the Created0x10 column.

Q9: The user has made notes of their work credentials, what is their password?

A: ReallyC00lDucks2023!

I found this file looking at the user directory.

![](../../Img/Pasted%20image%2020250516192316.png)

Since MFTExplorer finally opened i can search for it.
This is what it had.

![](../../Img/Pasted%20image%2020250516192353.png)

Q10: How many files remain under the C:\Users\ directory? (Recursively)

A: 3471

I had to check a hint for this, i used the edit filter function to narrow my search but i never got to the answer, i don't know what Is Ads and In Use filters are.

I searched in google and downloaded the manual from leanpub.com for the EZ Tools, but no mention of these filters.



