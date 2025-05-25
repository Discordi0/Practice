
## Scenario

This skills assessment section builds upon the progress made in the `Intrusion Detection With Splunk (Real-world Scenario)` section. Our objective is to identify any missing components of the attack chain and trace the malicious process responsible for initiating the infection.

Q1: Navigate to http://[Target IP]:8000, open the "Search & Reporting" application, and find through SPL searches against all data the process that created remote threads in rundll32.exe. Answer format: _.exe

A: randomfile.exe

We need to do a search with the rundll32 as a target.
Since we are looking for created remote threads we need Event Id 8. (https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)

![](../../Img/Pasted%20image%2020250525161054.png)

![](../../Img/Pasted%20image%2020250525160931.png)

With this search we get 6 events.
I added the new filter just to see who created the threads.

![](../../Img/Pasted%20image%2020250525161231.png)

Q2: Navigate to http://[Target IP]:8000, open the "Search & Reporting" application, and find through SPL searches against all data the process that started the infection. Answer format: _.exe

A: 
