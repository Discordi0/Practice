
##### Sherlock Scenario

The IDS device alerted us to a possible rogue device in the internal Active Directory network. The Intrusion Detection System also indicated signs of LLMNR traffic, which is unusual. It is suspected that an LLMNR poisoning attack occurred. The LLMNR traffic was directed towards Forela-WKstn002, which has the IP address 172.17.79.136. A limited packet capture from the surrounding time is provided to you, our Network Forensics expert. Since this occurred in the Active Directory VLAN, it is suggested that we perform network threat hunting with the Active Directory attack vector in mind, specifically focusing on LLMNR poisoning.


Q1: Its suspected by the security team that there was a rogue device in Forela's internal network running responder tool to perform an LLMNR Poisoning attack. Please find the malicious IP Address of the machine.

A: 

Q2: What is the hostname of the rogue machine?

A: 

Q3: Now we need to confirm whether the attacker captured the user's hash and it is crackable!! What is the username whose hash was captured?

A: 

Q4: In NTLM traffic we can see that the victim credentials were relayed multiple times to the attacker's machine. When were the hashes captured the First time?

A: 

Q5: What was the typo made by the victim when navigating to the file share that caused his credentials to be leaked?

A: 

Q6: To get the actual credentials of the victim user we need to stitch together multiple values from the ntlm negotiation packets. What is the NTLM server challenge value?

A: 

Q7: Now doing something similar find the NTProofStr value.

A: 

Q8: To test the password complexity, try recovering the password from the information found from packet capture. This is a crucial step as this way we can find whether the attacker was able to crack this and how quickly.

A: 

Q9: Just to get more context surrounding the incident, what is the actual file share that the victim was trying to navigate to?

A: 
