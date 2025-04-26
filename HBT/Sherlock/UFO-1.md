
##### Sherlock Scenario

Being in the ICS Industry, your security team always needs to be up to date and should be aware of the threats targeting organizations in your industry. You just started as a Threat intelligence intern, with a bit of SOC experience. Your manager has given you a task to test your skills in research and how well can you utilize Mitre Att&ck to your advantage. Do your research on Sandworm Team, also known as BlackEnergy Group and APT44. Utilize Mitre ATT&CK to understand how to map adversary behavior and tactics in actionable form. Smash the assessment and impress your manager as Threat intelligence is your passion.


Q1: According to the sources cited by Mitre, in what year did the Sandworm Team begin operations?

A: 2009

Main mitre page for Sandworm Team (https://attack.mitre.org/groups/G0034/).

![](../../Img/Pasted%20image%2020250426140552.png)

Q2: Mitre notes two credential access techniques used by the BlackEnergy group to access several hosts in the compromised network during a 2016 campaign against the Ukrainian electric power grid. One is LSASS Memory access (T1003.001). What is the Attack ID for the other?

A: T1110

Search for the 2016 campaign in the same page, in techniques open the matrix view (https://mitre-attack.github.io/attack-navigator//#layerURL=https%3A%2F%2Fattack.mitre.org%2Fcampaigns%2FC0025%2FC0025-enterprise-layer.json)

![](../../Img/Pasted%20image%2020250426140745.png)

Q3: During the 2016 campaign, the adversary was observed using a VBS script during their operations. What is the name of the VBS file?

A: ufn.vbs

There is more than one VBS metion in the techniques section, but the only one that has a especifique name is this one.

![](../../Img/Pasted%20image%2020250426141112.png)

Q4: The APT conducted a major campaign in 2022. The server application was abused to maintain persistence. What is the Mitre Att&ck ID for the persistence technique was used by the group to allow them remote access?

A: T1505.003

In the matrix view of the attack, under persistence. The only one that would allow remote access per se is this one.

![](../../Img/Pasted%20image%2020250426141718.png)

Q5: What is the name of the malware / tool used in question 4?

A: Neo-REGEORG

Search the web shell in the techniques of the attack

![](../../Img/Pasted%20image%2020250426141955.png)

Q6: Which SCADA application binary was abused by the group to achieve code execution on SCADA Systems in the same campaign in 2022?

A: scilc.exe

Two techniques below the web shell.

![](../../Img/Pasted%20image%2020250426142130.png)

Q7: Identify the full command line associated with the execution of the tool from question 6 to perform actions against substations in the SCADA environment.

A: C:\sc\prog\exec\scilc.exe -do pack\scil\s1.txt

Two below form the one before.
![](../../Img/Pasted%20image%2020250426142255.png)

Q8: What malware/tool was used to carry out data destruction in a compromised environment during the same campaign?

A: CaddyWiper

Softwre section.

![](../../Img/Pasted%20image%2020250426142316.png)

Q9: The malware/tool identified in question 8 also had additional capabilities. What is the Mitre Att&ck ID of the specific technique it could perform in Execution tactic?

A: T1106

Under Execution in the matrxi view of the software.

![](../../Img/Pasted%20image%2020250426142354.png)

Q10: The Sandworm Team is known to use different tools in their campaigns. They are associated with an auto-spreading malware that acted as a ransomware while having worm-like features. What is the name of this malware?

A: NotPetya

This one took more time, but the description kinda gave it away.

![](../../Img/Pasted%20image%2020250426142558.png)

Searching for that software i found the answer.

![](../../Img/Pasted%20image%2020250426142810.png)

Q11: What was the Microsoft security bulletin ID for the vulnerability that the malware from question 10 used to spread around the world?

A: MS17-010

Looking through the techniques used, this one stood up for me.

![](../../Img/Pasted%20image%2020250426143221.png)

Searchig for that vulnerability online i found what i was looking for.

![](../../Img/Pasted%20image%2020250426143346.png)

Q12: What is the name of the malware/tool used by the group to target modems?

A: AcidRain

I had to start looking at each one of the software in the list, lucky for me that the 2nd one was the answer.

![](../../Img/Pasted%20image%2020250426143546.png)

![](../../Img/Pasted%20image%2020250426143644.png)

Q13: Threat Actors also use non-standard ports across their infrastructure for Operational-Security purposes. On which port did the Sandworm team reportedly establish their SSH server for listening?

A: 6789

In the techniques section. The one called that.

![](../../Img/Pasted%20image%2020250426143817.png)

Q14: The Sandworm Team has been assisted by another APT group on various operations. Which specific group is known to have collaborated with them?

A: APT28

It's in the main description of the group.

![](../../Img/Pasted%20image%2020250426143851.png)


