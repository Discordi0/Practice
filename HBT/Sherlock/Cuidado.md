
##### Sherlock Scenario

Recently, a user triggered multiple alerts after downloading several potentially unwanted applications (PUAs), prompting concern from the security team. To gain deeper insight into the user's activity, the team began monitoring network traffic from their workstation. Their objective is to assess whether the downloads are linked to more serious malware threats.

---
## Questions:


Q1: What is the victim's IP address?

A: 192.168.1.152

The scenario comes with a .zip file, inside that there is a .pcap file, opening that with wireshark we can see the traffic.
In the conversations tab we can see that most of the traffic comes from 1 IP.

![](../../Img/Pasted%20image%2020251001142111.png)

---

Q2: What is the IP address of the attacker from whom the files were downloaded?

A: 94.156.177.109

Going into the export object tab, we can see that there is only 1 IP from where files were downloaded.

![](../../Img/Pasted%20image%2020251001142520.png)

---

Q3: Which malicious file appears to be the first one downloaded?

A: sh

If we see that screenshot above, we can see that the first download it's in packet 126. If we check that we can see that it's no "file".

![](../../Img/Pasted%20image%2020251001142816.png)

So we check where was the next download and go to packet 140.

![](../../Img/Pasted%20image%2020251001142917.png)

This one it's a file.

---

Q4: What is the name of the function that the attacker used to download the payload?

A: dlr

From the packet we can follow the stream, there we can see the name of the function.

![](../../Img/Pasted%20image%2020251001143219.png)

---

Q5: Which port does the attacker's server use?

A: 80

In the above screenshot we can see the IP followed by the port (after the /).

---

Q6: The script checks which directories it can write to by attempting to create test files. What is the size of the second test file? (Size in MB)

A: 2

Further down in the TCP stream we can see where it's creating the test files.

![](../../Img/Pasted%20image%2020251001143434.png)

---

Q7: What is the full command that the script uses to identify the CPU architecture?

A: uname -mp

On top of where the script creates the test files, we can find the creation of the variable(?) where it checks the architecture.

![[Pasted image 20251001144305.png]]

Q8: What is the name of the file that is downloaded after the CPU architecture is compared with reference values?

A: x86_64

Further down we can see "$ARCH" being used.

![[Pasted image 20251001144453.png]]

Q9: What is the full command that the attacker used to disable any existing mining service?

A: systemctl disable c3pool_miner

I used "ip.addr == 94.156.177.109" as a filter to see the traffic from the attacker's IP.

![[Pasted image 20251001145135.png]]

We can see that we have packet 140 from the previous questions, next we have packet 182 that did a GET request to another file.

![[Pasted image 20251001145253.png]]

Following that TCP stream we get the answer.

Q10: Apparently, the attacker used a packer to compress the malware. Which version of this packer was used? (Format X.XX)

A: 4.23

The next file downloaded was "x86_64" and following that file's TCP stream we get something like  this.

![[Pasted image 20251001151655.png]]

As far as i could see the whole stream it's that. So i went to the end to see if i could get something and found this.

![[Pasted image 20251001151804.png]]

UPX sounded familiar so i started to check further up and found this.

![[Pasted image 20251001151900.png]]

Q11: What is the entropy value of unpacked malware?

A: 6.488449

I tried to check the entropy with DiE.

![[Pasted image 20251001154802.png]]

None of those values was correct. 
I then tried with ent.

![[Pasted image 20251001154839.png]]

That was the answer.

Q12: What is the file name with which the unpacked malware was submitted on VirusTotal?

A: redtail.cuidado

I did a sha256sum of the unpacked malware and uploaded it to VirusTotal.

![[Pasted image 20251001155152.png]]

![[Pasted image 20251001155207.png]]

In there i searched for a name. In the list of names i looked for something realted to the case.

![[Pasted image 20251001155311.png]]

Q13: What MITRE ATT&CK technique ID is associated with the main purpose of the malware?

A: T1496

Since the main page referenced something like miner i started looking at the techniques in the behavior tab.

![[Pasted image 20251001160113.png]]

![[Pasted image 20251001160003.png]]
