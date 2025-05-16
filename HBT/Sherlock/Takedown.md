

##### Sherlock Scenario

We've identified an unusual pattern in our network activity, indicating a possible security breach. Our team suspects an unauthorized intrusion into our systems, potentially compromising sensitive data. Your task is to investigate this incident.

Q1: From what domain is the VBS script downloaded?

A: escuelademarina.com

Upon opening the only file (.pcap) we can see that there is a DNS request to a domain, and after that there is a smb request for a .vbs file.

![](../../Img/Pasted%20image%2020250516023042.png)

Q2: What was the IP address associated with the domain in question #1 used for this attack?

A: 165.22.16.55

In packet N° 2 there is the ip of the domain.

Q3: What is the filename of the VBS script used for initial access?

A: AZURE_DOC_OPEN.vbs

In screenshot of Q1.

Q4: What was the URL used to get a PowerShell script?

A: 

Q5: What likely legit binary was downloaded to the victim machine?

A: 

Q6: From what URL was the malware used with the binary from question #5 downloaded?

A: 

Q7: What filename was the malware from question #6 given on disk?

A: 

Q8: What is the TLSH of the malware?

A: 

Q9: What is the name given to this malware? Use the name used by McAfee, Ikarus, and alejandro.sanchez.

A: 

Q10: What is the user-agent string of the infected machine?

A: 

Q11: To what IP does the RAT from the previous question connect?

A: 

