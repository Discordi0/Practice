
##### Sherlock Scenario

We've identified an unusual pattern in our network activity, indicating a possible security breach. Our team suspects an unauthorized intrusion into our systems, potentially compromising sensitive data. Your task is to investigate this incident.

___

### Q1: From what domain is the VBS script downloaded?

#### A: escuelademarina.com

Upon opening the only file (.pcap) we can see that there is a DNS request to a domain, and after that there is a smb request for a .vbs file.

![](../../Img/Pasted%20image%2020250516023042.png)

___

### Q2: What was the IP address associated with the domain in question #1 used for this attack?

#### A: 165.22.16.55

In packet N° 2 there is the ip of the domain.

___

### Q3: What is the filename of the VBS script used for initial access?

#### A: AZURE_DOC_OPEN.vbs

In screenshot of Q1.

___

### Q4: What was the URL used to get a PowerShell script?

#### A: badbutperfect.com/nrwncpwo

Checking the HTTP exports we can see what file where downloaded.

![](../../Img/Pasted%20image%2020250516023952.png)

Checking each of the files, we find this. (interesting but no what we are looking for).

![](../../Img/Pasted%20image%2020250516024112.png)

Found you.

![](../../Img/Pasted%20image%2020250516024434.png)

___

### Q5: What likely legit binary was downloaded to the victim machine?

#### A: AutoHotkey.exe

Reading the script we can find the name of the file.

___

### Q6: From what URL was the malware used with the binary from question #5 downloaded?

#### A: http://badbutperfect.com/jvtobaqj

Reading the script again.

___

### Q7: What filename was the malware from question #6 given on disk?

#### A: script.ahk

It's righ next to Q6 answer.

___

### Q8: What is the TLSH of the malware?

#### A: T15E430A36DBC5202AD8E3074270096562FE7DC0215B4B32659C9EF16835CF6FF9B6A1B8

I tried checking it myself.

![](../../Img/Pasted%20image%2020250516030309.png)

But it wasn't it.
I had to sha256sum it, check that in virustotal, and from there get the answer.

![](../../Img/Pasted%20image%2020250516030416.png)

![](../../Img/Pasted%20image%2020250516030431.png)

___

### Q9: What is the name given to this malware? Use the name used by McAfee, Ikarus, and alejandro.sanchez.

#### A: DarkGate

Check the Community tab.

![](../../Img/Pasted%20image%2020250516030615.png)

___

### Q10: What is the user-agent string of the infected machine?

#### A: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36

Filtering for http we can see all the traffic.

![](../../Img/Pasted%20image%2020250516031229.png)

___

### Q11: To what IP does the RAT from the previous question connect?

#### A: 103.124.105.78

Just check the Destination ip in wireshark.


Tags: [Network Traffic Analysis](../../Index/Network%20Traffic%20Analysis.md) [Source Code Analysis](../../Index/Source%20Code%20Analysis.md) [Threat Analysis](../../Index/Threat%20Analysis.md) [Wireshark](../../Index/Wireshark.md) 