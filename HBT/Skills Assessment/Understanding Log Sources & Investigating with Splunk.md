
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

With the result of the previous question i started digging.
We can see that the threads were created by randomfile.exe.

![](../../Img/Pasted%20image%2020250525161846.png)

So i looked for all events that the .exe has associated.

![](../../Img/Pasted%20image%2020250525161937.png)

That search didn't took me anywhere since all 34 event where Sysmon Event Id 8.
So i did a broader search and got this.

![](../../Img/Pasted%20image%2020250525162406.png)

The event Id that caught my attention was Id 3 since i wanted to see how that file got to the machine.

![](../../Img/Pasted%20image%2020250525163320.png)

![](../../Img/Pasted%20image%2020250525163353.png)

With the next filter we can see that all traffic generated from that file goes to the same Ip.

![](../../Img/Pasted%20image%2020250525163628.png)

