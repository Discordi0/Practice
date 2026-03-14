
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

A: pass

A little bit below.

![](../../Img/Pasted%20image%2020250930231137.png)

Q6: What is the domain used in the phishing URL inside the email?

A: secure.business-finance.com

In the content of the email, it's the only link.

![](../../Img/Pasted%20image%2020250930231332.png)

Q7: What is the fake company name used in the email?

A: Business Finance Ltd.

In the next lines.

![](../../Img/Pasted%20image%2020250930231425.png)

Q8: What is the name of the attachment included in the email?

A: Invoice_2025_Payment.zip

At the bottom of the email, where the included file is.

![](../../Img/Pasted%20image%2020250930231525.png)

Q9: What is the SHA-256 hash of the attachment?

A: 8379c41239e9af845b2ab6c27a7509ae8804d7d73e455c800a551b22ba25bb4a

I opened the email with Thunderbird, save the .zip file and sha256sum it.

![](../../Img/Pasted%20image%2020250930232910.png)

Q10: What is the filename of the malicious file contained within the ZIP attachment?

A: invoice_document.pdf.bat

You can just open the .zip file to see, but if you don't think it's wise, just copy the string from inside the email (opened with a txt editor).

![](../../Img/Pasted%20image%2020250930233146.png)

And decode it.

![](../../Img/Pasted%20image%2020250930233205.png)

Q11: Which MITRE ATT&CK techniques are associated with this attack?

A: T1566.001

Search for the phishing technique in mitre (https://attack.mitre.org/techniques/T1566/), then look for the right sub-technique.

![](../../Img/Pasted%20image%2020250930233329.png)
