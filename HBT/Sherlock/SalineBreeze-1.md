
##### Sherlock Scenario

Your manager has just informed you that, due to recent budget cuts, you'll need to take on additional responsibilities in threat analysis. As a junior threat intelligence analyst at a cybersecurity firm, you're now tasked with investigating a cyber espionage campaign linked to a group known as Salt Typhoon. Apparently, defending against sophisticated Nation-State cyber threats is now a "do more with less" kind of game. Your Task: Conduct comprehensive research on Salt Typhoon, focusing on their tactics, techniques, and procedures. Utilize the MITRE ATT&CK framework to map out their activities and provide actionable insights. Your findings could play a pivotal role in fortifying our defenses against this adversary. Dive deep into the data and show that even with a shoestring budget, you can outsmart the cyber baddies.


## Questions:

Q1: Starting with the MITRE ATT&CK page, which country is thought be behind Salt Typhoon?

A: China

Opening the link of MITRE's pago on Salt Typhoon. (https://attack.mitre.org/groups/G1045/). We get the answer. 

![](../../Img/Pasted%20image%2020250930165517.png)

Q2: According to that page, Salt Typhoon has been active since at least when? (Year)

A: 2019

Answer in the above question.

Q3: What kind of infrastructure does Salt Typhoon target?

A: Network

In Q1.

Q4: Salt Typhoon has been associated with multiple custom built malware, what is the name of the malware associated with the ID S1206?

A: JumbledPath

At the end of the page, we can find the Software section.

![](../../Img/Pasted%20image%2020250930165720.png)

Q5: What operating system does this malware target?

A: Linux

In the malware page (https://attack.mitre.org/software/S1206/). Main section.

![](../../Img/Pasted%20image%2020250930165843.png)

Q6: What programming language is the malware written in?

A: GO

Answer in above quesion.

Q7: On which vendor's devices does the malware act as a network sniffer?

A: Cisco

Answer in Q5.

Q8: The malware can perform 'Indicator Removal' by erasing logs. What is the MITRE ATT&CK ID for this?

A: T1070.002

In the middle of the technique section.

![](../../Img/Pasted%20image%2020250930170120.png)

Q9: On December 20th, 2024, Picus Security released a blog on Salt Typhoon detailing some of the CVEs associated with the threat actor. What was the CVE for the vulnerability related to the Sophos Firewall?

A: CVE-2022-3236

Searching for "Salt Typhoon Picus Security" i fond this (https://www.picussecurity.com/resource/blog/salt-typhoon-telecommunications-threat).
In the "Origins and Affiliations of the Chinese Threat Actor Salt Typhoon" section we can find the CVEs exploited by the group.

![](../../Img/Pasted%20image%2020250930170517.png)

Q10: The blog demonstrates how the group modifies the registry to obtain persistence with a backdoor known as Crowdoor. Which registry key do they target?

A: HKCU\Software\Microsoft\Windows\CurrentVersion\Run

Arriving at the middle of the blog post, in the "Persistence: ATT&CK TA0003" section, inside the " Modify Registry - MITRE T1112 " sub-section we find an example of a command used by the group.

![](../../Img/Pasted%20image%2020250930170846.png)

Q11: What is the MITRE ATT&CK ID of the previous technique?

A: T1112

It's in the name of the sub-section in Q10.

Q12: On November 25th, 2024, TrendMicro published a blog post detailing the threat actor. What name does this blog primarily use to refer to the group?

A: Earth Estries

Searching for "Salt Typhoon Picus Security" i found the article (https://www.trendmicro.com/en_us/research/24/k/earth-estries.html). 
The answer is right below the title of the article.

![](../../Img/Pasted%20image%2020250930171145.png)

Q13: The blog post identifies additional malware attributed to the threat actor. Which malware do they describe as a 'multi-modular backdoor...using a custom protocol protected by Transport Layer Security'

A: GhostSpider

In the middle of the article, inside the "Campaign Beta" sub-section, it's the first technique described.

![](../../Img/Pasted%20image%2020250930171646.png)

Q14: Most of the domains the malware communicates with have a .com top-level domain. One uses a .dev TLD. What is the full domain name for the .dev TLD?

A: 

Q15: What is the filename for the first GET request to the C&C server used by the malware?

A: 

Q16: On September 30th, 2021, a blog post was released on Securelist by Kaspersky. What was the threat actor's name at that time?

A: 

Q17: What is the name of the malware that this article focuses on?

A: 

Q18: What type of malware is the above malware?

A: 

Q19: The first stage consists of a malicious PowerShell dropper. What type of encryption is used to obfuscate the code?

A: 

Q20: The malware uses Input/Output Control codes to perform various tasks related to hiding malicious artifacts. What is the IOCTL code used by the malware to hide its service from the list within the services.exe process address space?

A: 


