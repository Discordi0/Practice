
##### Sherlock Scenario

Happy Grunwald contacted the sysadmin, Alonzo, because of issues he had downloading the latest version of Microsoft Office. He had received an email saying he needed to update, and clicked the link to do it. He reported that he visited the website and solved a captcha, but no office download page came back. Alonzo, who himself was bombarded with phishing attacks last year and was now aware of attacker tactics, immediately notified the security team to isolate the machine as he suspected an attack. You are provided with network traffic and endpoint artifacts to answer questions about what happened.


Q1: It is crucial to understand any payloads executed on the system for initial access. Analyzing registry hive for user happy grunwald. What is the full command that was run to download and execute the stager.

A: 

Q2: At what time in UTC did the malicious payload execute?

A: 

Q3: The payload which was executed initially downloaded a PowerShell script and executed it in memory. What is sha256 hash of the script?

A: 

Q4: To which port did the reverse shell connect?

A: 

Q5: For how many seconds was the reverse shell connection established between C2 and the victim's workstation?

A: 

Q6: Attacker hosted a malicious Captcha to lure in users. What is the name of the function which contains the malicious payload to be pasted in victim's clipboard?

A: 
