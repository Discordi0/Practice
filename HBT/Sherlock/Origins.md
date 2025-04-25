
##### Sherlock Scenario

A major incident has recently occurred at Forela. Approximately 20 GB of data were stolen from internal s3 buckets and the attackers are now extorting Forela. During the root cause analysis, an FTP server was suspected to be the source of the attack. It was found that this server was also compromised and some data was stolen, leading to further compromises throughout the environment. You are provided with a minimal PCAP file. Your goal is to find evidence of brute force and data exfiltration.


Q1: What is the attacker's IP address?

A: 15.206.185.207

Knowing that the entry vector is ftp (per the sherlock desc), we filter for ftp traffic and look.
Skimming through the packets, the first thing noticeable is that and ip is just spraying pswds

![](../../Img/Pasted%20image%2020250425183043.png)

Q2: It's critical to get more knowledge about the attackers, even if it's low fidelity. Using the geolocation data of the IP address used by the attackers, what city do they belong to?

A: Mumbai

Just google a page, i got this as first result (https://www.iplocation.net/ip-lookup)

![](../../Img/Pasted%20image%2020250425183243.png)

Q3: Which FTP application was used by the backup server? Enter the full name and version. (Format: Name Version)

A: vsFTPd 3.0.5

Same ftp filter on wireshark, just look for it.

![](../../Img/Pasted%20image%2020250425183428.png)

Q4: The attacker has started a brute force attack on the server. When did this attack start?

A: 2024-05-03 04:12:54

First request to the server from the attacker ip

![](../../Img/Pasted%20image%2020250425183650.png)

Q5: What are the correct credentials that gave the attacker access? (Format username:password)

A: forela-ftp:ftprocks69$

Find the first successful login, then follow tcp stream.

![](../../Img/Pasted%20image%2020250425183816.png)

Q6: The attacker has exfiltrated files from the server. What is the FTP command used to download the remote files?

A: RETR

Keep looking after the successful login, after the RETR command there is a response 226 transfer complete son this must be.

![](../../Img/Pasted%20image%2020250425183941.png)

Q7: Attackers were able to compromise the credentials of a backup SSH server. What is the password for this SSH server?

A: 

After the retrieval (i think that it what RETR means, looking it after completion) there is nothing interesting, so inside one of the 2 files exfiltrated from the victim must be the answer.
Exporting those files (aka object ftp-data) and opening the .pdf file we find it.

![](../../Img/Pasted%20image%2020250425184728.png)

Q8: What is the s3 bucket URL for the data archive from 2023?

A: 

Q9: The scope of the incident is huge as Forela's s3 buckets were also compromised and several GB of data were stolen and leaked. It was also discovered that the attackers used social engineering to gain access to sensitive data and extort it. What is the internal email address used by the attacker in the phishing email to gain access to sensitive data stored on s3 buckets?

A: 
