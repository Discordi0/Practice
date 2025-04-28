
##### Sherlock Scenario

The IDS device alerted us to a possible rogue device in the internal Active Directory network. The Intrusion Detection System also indicated signs of LLMNR traffic, which is unusual. It is suspected that an LLMNR poisoning attack occurred. The LLMNR traffic was directed towards Forela-WKstn002, which has the IP address 172.17.79.136. A limited packet capture from the surrounding time is provided to you, our Network Forensics expert. Since this occurred in the Active Directory VLAN, it is suggested that we perform network threat hunting with the Active Directory attack vector in mind, specifically focusing on LLMNR poisoning.


Q1: Its suspected by the security team that there was a rogue device in Forela's internal network running responder tool to perform an LLMNR Poisoning attack. Please find the malicious IP Address of the machine.

A: 172.17.79.135

![](../../Img/Pasted%20image%2020250428140241.png)

I don't really get how this protocol works, but seeing that 135 it's telling 136 that he is a workstation is sus.

![](../../Img/Pasted%20image%2020250428140523.png)

Q2: What is the hostname of the rogue machine?

A: kali

I use the ip as a filter and look at all the traffic, skimming it i notice that there is dhcp traffic.

![](../../Img/Pasted%20image%2020250428141036.png)

Q3: Now we need to confirm whether the attacker captured the user's hash and it is crackable!! What is the username whose hash was captured?

A: john.deacon

With the same filter i just keep scrolling down until i notice rdp traffic.

![](../../Img/Pasted%20image%2020250428141135.png)

Q4: In NTLM traffic we can see that the victim credentials were relayed multiple times to the attacker's machine. When were the hashes captured the First time?

A: 2024-06-24 11:18:30

We filter for NTLM traffic (ntlmssp) and check the first one.

![](../../Img/Pasted%20image%2020250428141303.png)

Q5: What was the typo made by the victim when navigating to the file share that caused his credentials to be leaked?

A: DCC01

We go back to filter by the attacker ip.

![](../../Img/Pasted%20image%2020250428141516.png)

Q6: To get the actual credentials of the victim user we need to stitch together multiple values from the ntlm negotiation packets. What is the NTLM server challenge value?

A: 601019d191f054f1

Back to NTLM traffic filter. We see one that might be interesting. 
![](../../Img/Pasted%20image%2020250428141812.png)

Inside the SMB2 section look for it.

![](../../Img/Pasted%20image%2020250428141907.png)

Q7: Now doing something similar find the NTProofStr value.

A: 

According to this article (https://posts.specterops.io/the-renaissance-of-ntlm-relay-attacks-everything-you-need-to-know-abfc3677c34e). NTProofStr is a part of the authentication process.
Searching the next packet que find the answer.

![](../../Img/Pasted%20image%2020250428142654.png)

![](../../Img/Pasted%20image%2020250428142722.png)

Q8: To test the password complexity, try recovering the password from the information found from packet capture. This is a crucial step as this way we can find whether the attacker was able to crack this and how quickly.

A: 

I had to use the hint for this. This is what i need to do User::Domain:ServerChallenge:NTProofStr:NTLMv2Response(without first 16 bytes).

I put all of that in a file

![](../../Img/Pasted%20image%2020250428143245.png)

Then hashcat it is.



Q9: Just to get more context surrounding the incident, what is the actual file share that the victim was trying to navigate to?

A: 
