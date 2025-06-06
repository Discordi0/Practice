
##### Sherlock Scenario

Forela's CTO, Dutch, stores important files on a separate Windows system because the domain environment at Forela is frequently breached due to its exposure across various industries. On 24 January 2025, our worst fears were realised when an intruder accessed the fileserver, installed utilities to aid their actions, stole critical files, and then deleted them, rendering them unrecoverable. The team was immediately informed of the extortion attempt by the intruders, who are now demanding money. While our legal team addresses the situation, we must quickly perform triage to assess the incident's extent. Note from the manager: We enabled SmartScreen Debug Logs across all our machines for enhanced visibility a few days ago, following a security research recommendation. These logs can provide quick insights, so ensure they are utilised.


Q1: The attacker logged in to the machine where Dutch saves critical files, via RDP on 24th January 2025. Please determine the timestamp of this login.

A: 2025-01-24 10:15:14

Googling i found this article (https://ponderthebits.com/2018/02/windows-rdp-related-event-logs-identification-tracking-and-investigation/).
Looking into that log file, filtering for that event id, got only one entry.

![](../../Img/Pasted%20image%2020250426145522.png)

Q2: The attacker downloaded a few utilities that aided them for their sabotage and extortion operation. What was the first tool they downloaded and installed?

A: WinRAR

I tried googling about it, didn't found anything that helped.
Event Id 1033 / 11707 had entries in te Aplication log, but not 1 referenced the answer (https://superuser.com/questions/321385/windows-event-log-installs)
Looking at the hint i found the answer.
In the entries of the log, we find that msedge was... checked? executed?

![](../../Img/Pasted%20image%2020250426153033.png)

And after that, this was... done the same thing.

![](../../Img/Pasted%20image%2020250426153133.png)

Q3: They then proceeded to download and then execute the portable version of a tool that could be used to search for files on the machine quickly and efficiently. What was the full path of the executable?

A: C:\Users\Dutch\Downloads\Everything.exe

If you keep looking at whatever this events indicate, we find the answer.

![](../../Img/Pasted%20image%2020250426153226.png)

Q4: What is the execution time of the tool from task 3?

A: 2025-01-24 10:17:33

Same entry, Details tab.

![](../../Img/Pasted%20image%2020250426153249.png)

Q5: The utility was used to search for critical and confidential documents stored on the host, which the attacker could steal and extort the victim. What was the first document that the attacker got their hands on and breached the confidentiality of that document?

A: C:\Users\Dutch\Documents\2025- Board of directors Documents\Ministry Of Defense Audit.pdf

I don't really know what this log file logs, but everything seems to be here.

![](../../Img/Pasted%20image%2020250426153339.png)

Q6: Find the name and path of second stolen document as well.

A: C:\Users\Dutch\Documents\2025- Board of directors Documents\2025-BUDGET-ALLOCATION-CONFIDENTIAL.pdf

Just below Q5 answer.

![](../../Img/Pasted%20image%2020250426153435.png)

Q7: The attacker installed a Cloud utility as well to steal and exfiltrate the documents. What is name of the cloud utility?

A: MEGAsync

Same thing.

![](../../Img/Pasted%20image%2020250426153509.png)

Q8: When was this utility executed?

A: 2025-01-24 10:22:19

I thought that this was like Q4, but this entry indicate that the program was installed (hence Setup64.exe on the file name).
So, searching for a mega no setup execution i found this.

![](../../Img/Pasted%20image%2020250426153758.png)

Q9: The Attacker also proceeded to destroy the data on the host so it is unrecoverable. What utility was used to achieve this?

A: File Shredder

In the same all knowing log.
![](../../Img/Pasted%20image%2020250426153900.png)

Q10: The attacker cleared 2 important logs, thinking they covered all their tracks. When was the security log cleared?

A: 2025-01-24 10:28:41

Not so all knowing after all.
Google AI thingy says that 1102 it's the one i'm looking for.

![](../../Img/Pasted%20image%2020250426154231.png)

According to the source of the AI i have to look in the Security log (https://www.manageengine.com/products/active-directory-audit/kb/event-log-events/event-id-1102.html#:~:text=Whenever%20Windows%20Security%20audit%20log,event%20ID%201102%20is%20logged.)

There is only one.

![](../../Img/Pasted%20image%2020250426154437.png)

![](../../Img/Pasted%20image%2020250426154453.png)

