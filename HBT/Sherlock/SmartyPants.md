
##### Sherlock Scenario

Forela's CTO, Dutch, stores important files on a separate Windows system because the domain environment at Forela is frequently breached due to its exposure across various industries. On 24 January 2025, our worst fears were realised when an intruder accessed the fileserver, installed utilities to aid their actions, stole critical files, and then deleted them, rendering them unrecoverable. The team was immediately informed of the extortion attempt by the intruders, who are now demanding money. While our legal team addresses the situation, we must quickly perform triage to assess the incident's extent. Note from the manager: We enabled SmartScreen Debug Logs across all our machines for enhanced visibility a few days ago, following a security research recommendation. These logs can provide quick insights, so ensure they are utilised.


Q1: The attacker logged in to the machine where Dutch saves critical files, via RDP on 24th January 2025. Please determine the timestamp of this login.

A: 2025-01-24 10:15:14



Q2: The attacker downloaded a few utilities that aided them for their sabotage and extortion operation. What was the first tool they downloaded and installed?

A: WinRAR

Q3: They then proceeded to download and then execute the portable version of a tool that could be used to search for files on the machine quickly and efficiently. What was the full path of the executable?

A: C:\Users\Dutch\Downloads\Everything.exe

Q4: What is the execution time of the tool from task 3?

A: 2025-01-24 10:17:33

Q5: The utility was used to search for critical and confidential documents stored on the host, which the attacker could steal and extort the victim. What was the first document that the attacker got their hands on and breached the confidentiality of that document?

A: C:\Users\Dutch\Documents\2025- Board of directors Documents\Ministry Of Defense Audit.pdf

Q6: Find the name and path of second stolen document as well.

A: C:\Users\Dutch\Documents\2025- Board of directors Documents\2025-BUDGET-ALLOCATION-CONFIDENTIAL.pdf

Q7: The attacker installed a Cloud utility as well to steal and exfiltrate the documents. What is name of the cloud utility?

A: MEGAsync

Q8: When was this utility executed?

A: 2025-01-24 10:22:19

Q9: The Attacker also proceeded to destroy the data on the host so it is unrecoverable. What utility was used to achieve this?

A: File Shredder

Q10: The attacker cleared 2 important logs, thinking they covered all their tracks. When was the security log cleared?

A: 2025-01-24 10:28:41
