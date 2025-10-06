
##### Sherlock Scenario

Our SOC team detected suspicious activity in Network Traffic, the machine has been compromised and company information that should not have been there has now been stolen – it’s up to you to figure out what has happened and what data has been taken.

___

### Q1: What is the IP address used for initial access?

#### A: 162.252.172.54

There is only a single .pcap file, so open that.
With a quick glance i couldn't find anything interesting, so i went to the conversations menu.
In the first 3 tabs there wasn't much, but in the TCP tab i found this.

![](../../Img/Pasted%20image%2020250515160158.png)

Why is this machine sending to a http/web page port so much data (compared to the rest).
I found that there is only 1 other ip that the machine connected in port 80.

![](../../Img/Pasted%20image%2020250515160342.png)

But the traffic is almost nothing.
Applying that ip as a filter, we can see that the first thing that our victim does it's access a weird (possible malicious) link.

![](../../Img/Pasted%20image%2020250515160656.png)

___

### Q2: What is the SHA256 hash of the malware?

#### A: 9b8ffdc8ba2b2caa485cca56a82b2dcbd251f65fb30bc88f0ac3da6704e4d3c6

Having the file name, we can see what it was by downloading it.

![](../../Img/Pasted%20image%2020250515160934.png)

We just need to get the hash now.

![](../../Img/Pasted%20image%2020250515161132.png)

___

### Q3: What is the Family label of the malware?

#### A: Pikabot

Enter the 256 hash in virustotal.

![](../../Img/Pasted%20image%2020250515164641.png)

___

### Q4: When was the malware first seen in the wild (UTC)?

#### A: 2023-05-19 14:01:21

In VirusTotal, on Details under History.

![](../../Img/Pasted%20image%2020250515164749.png)

___

### Q5: The malware used HTTPS traffic with a self-signed certificate. What are the ports, from smallest to largest?

#### A: 2078, 2222, 32999

According to this (https://superuser.com/questions/1756591/how-can-i-view-the-tls-1-2-and-1-3-certificates-in-wireshark) and this (https://community.fortinet.com/t5/FortiGate/Technical-Tip-Extracting-certificates-from-SSL-TLS-handshake/ta-p/221235)
I need to filter for handshake type 11.

![](../../Img/Pasted%20image%2020250515170914.png)

Checking the traffic i can see that there is a lot of ports, but checking if the cert is self signed (if issuer and subject are the same) i can gather the answer.

![](../../Img/Pasted%20image%2020250515171401.png)

![](../../Img/Pasted%20image%2020250515171417.png)

![](../../Img/Pasted%20image%2020250515171446.png)

Q6: What is the id-at-localityName of the self-signed certificate associated with the first malicious IP?

A: Pyopneumopericardium

Checking the details.

![](../../Img/Pasted%20image%2020250515172240.png)

Q7: What is the notBefore time(UTC) for this self-signed certificate?

A: 2023-05-14 08:36:52

Just under Q6.

![](../../Img/Pasted%20image%2020250515172357.png)

Q8: What was the domain used for tunneling?

A: steasteel.net

Changing the filter to dns, we see traffic for only 2 ips.

![](../../Img/Pasted%20image%2020250515172703.png)

Tags: [Traffic Analysis](../../Index/Traffic%20Analysis.md) [Wireshark](../../Index/Wireshark.md) 