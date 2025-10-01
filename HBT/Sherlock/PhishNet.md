
##### Sherlock Scenario

An accounting team receives an urgent payment request from a known vendor. The email appears legitimate but contains a suspicious link and a .zip attachment hiding malware. Your task is to analyze the email headers, and uncover the attacker's scheme.


## Questions: 

Q1: What is the originating IP address of the sender?

A: 45.67.89.10

The scenario comes with a .eml file.
We open that file and search for the ip.

![](../../Img/Pasted%20image%2020250930230613.png)

Q2: Which mail server relayed this email before reaching the victim?

A: 203.0.113.25

If we keep reading the email, we reach the section where the trace(?) is.

![](../../Img/Pasted%20image%2020250930230842.png)

Q3: What is the sender's email address?

A: finance@business-finance.com

It's in the above screenshot. (first relay)

Q4: What is the 'Reply-To' email address specified in the email?

A: support@business-finance.com

Top of the email.

![](../../Img/Pasted%20image%2020250930231051.png)

Q5: What is the SPF (Sender Policy Framework) result for this email?

A: 

Q6: What is the domain used in the phishing URL inside the email?

A: 

Q7: What is the fake company name used in the email?

A: 

Q8: What is the name of the attachment included in the email?

A: 

Q9: What is the SHA-256 hash of the attachment?

A: 

Q10: What is the filename of the malicious file contained within the ZIP attachment?

A: 

Q11: Which MITRE ATT&CK techniques are associated with this attack?

A: 
