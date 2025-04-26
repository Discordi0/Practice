
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



Q8: What malware/tool was used to carry out data destruction in a compromised environment during the same campaign?

A: CaddyWiper

Q9: The malware/tool identified in question 8 also had additional capabilities. What is the Mitre Att&ck ID of the specific technique it could perform in Execution tactic?

A: T1106

Q10: The Sandworm Team is known to use different tools in their campaigns. They are associated with an auto-spreading malware that acted as a ransomware while having worm-like features .What is the name of this malware?

A: NotPetya

Q11: What was the Microsoft security bulletin ID for the vulnerability that the malware from question 10 used to spread around the world?

A: MS17-010

Q12: What is the name of the malware/tool used by the group to target modems?

A: AcidRain

Q13: Threat Actors also use non-standard ports across their infrastructure for Operational-Security purposes. On which port did the Sandworm team reportedly establish their SSH server for listening?

A: 6789

Q14: The Sandworm Team has been assisted by another APT group on various operations. Which specific group is known to have collaborated with them?

A: APT28

