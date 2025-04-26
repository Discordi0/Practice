
##### Sherlock Scenario

You are a junior threat intelligence analyst at a Cybersecurity firm. You have been tasked with investigating a Cyber espionage campaign known as Operation Dream Job. The goal is to gather crucial information about this operation.


Q1: Who conducted Operation Dream Job?

A: Lazarus Group

Google it (https://attack.mitre.org/campaigns/C0022/).

![](../../Img/Pasted%20image%2020250426133453.png)

Q2: When was this operation first observed?

A: September 2019

Same page.

![](../../Img/Pasted%20image%2020250426133533.png)

Q3: There are 2 campaigns associated with Operation Dream Job. One is `Operation North Star`, what is the other?

A: Operation Interception

Same page.

![](../../Img/Pasted%20image%2020250426133554.png)

Q4: During Operation Dream Job, there were the two system binaries used for proxy execution. One was `Regsvr32`, what was the other?

A: Rundll32

In the technique section, i found this.

![](../../Img/Pasted%20image%2020250426133734.png)

Q5: What lateral movement technique did the adversary use?

A: Internal Spearphishing

In the technique section there isn't one named lateral movement, so i opened the matrix view and found it.

![](../../Img/Pasted%20image%2020250426133955.png)

Q6: What is the technique ID for the previous answer?

A: T1534

Mouse over it.

![](../../Img/Pasted%20image%2020250426134017.png)

Q7: What Remote Access Trojan did the Lazarus Group use in Operation Dream Job?

A: DRATzarus

In the Software section of the mitre page.

![](../../Img/Pasted%20image%2020250426134130.png)

Q8: What technique did the malware use for execution?

A: Native API

In the matrix view of the RAT software.

![](../../Img/Pasted%20image%2020250426134246.png)

Q9: What technique did the malware use to avoid detection in a sandbox?

A: Time Based Evasion

Defense evasion column.

![](../../Img/Pasted%20image%2020250426134427.png)

Q10: To answer the remaining questions, utilize VirusTotal and refer to the IOCs.txt file. What is the name associated with the first hash provided in the IOC file?

A: IEXPLORE.exe

First thing in the VirusTotal search result (https://www.virustotal.com/gui/file/7bb93be636b332d0a142ff11aedb5bf0ff56deabba3aa02520c85bd99258406f)

![](../../Img/Pasted%20image%2020250426134554.png)

Q11: When was the file associated with the second hash in the IOC first created?

A: 2020-05-12 19:26:17

It's in the details section, under History (https://www.virustotal.com/gui/file/adce894e3ce69c9822da57196707c7a15acee11319ccc963b84d83c23c3ea802/details)

![](../../Img/Pasted%20image%2020250426134753.png)

Q12: What is the name of the parent execution file associated with the second hash in the IOC?

A: BAE_HPC_SE.iso

In the Relations section

![](../../Img/Pasted%20image%2020250426135100.png)

Q13: Examine the third hash provided. What is the file name likely used in the campaign that aligns with the adversary's known tactics?

A: Salary_Lockheed_Martin_job_opportunities_confidential.doc

In details, under Names (https://www.virustotal.com/gui/file/0160375e19e606d06f672be6e43f70fa70093d2a30031affd2929a5c446d07c1/details)

![](../../Img/Pasted%20image%2020250426135242.png)

Q14: Which URL was contacted on 2022-08-03 by the file associated with the third hash in the IOC file?

A: https://markettrendingcenter.com/lk_job_oppor.docx

In Relations.

![](../../Img/Pasted%20image%2020250426135350.png)

