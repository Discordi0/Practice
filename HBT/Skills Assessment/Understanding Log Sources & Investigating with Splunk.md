
## Scenario

This skills assessment section builds upon the progress made in the `Intrusion Detection With Splunk (Real-world Scenario)` section. Our objective is to identify any missing components of the attack chain and trace the malicious process responsible for initiating the infection.

___

### Q1: Navigate to http://[Target IP]:8000, open the "Search & Reporting" application, and find through SPL searches against all data the process that created remote threads in rundll32.exe. Answer format: _.exe

#### A: randomfile.exe

We need to do a search with the rundll32 as a target.
Since we are looking for created remote threads we need Event Id 8. (https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)

![](../../Img/Pasted%20image%2020250525161054.png)

![](../../Img/Pasted%20image%2020250525160931.png)

With this search we get 6 events.
I added the new filter just to see who created the threads.

![](../../Img/Pasted%20image%2020250525161231.png)

___

Q2: Navigate to http://[Target IP]:8000, open the "Search & Reporting" application, and find through SPL searches against all data the process that started the infection. Answer format: _.exe

A: rundll32.exe

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

Looking at the events i can see that all have the same User.

![](../../Img/Pasted%20image%2020250525163914.png)

With this i did a new search without EventCode.

![](../../Img/Pasted%20image%2020250525164121.png)

Since i was looking how this file got here i sorted the events by time

![](../../Img/Pasted%20image%2020250525164245.png)

Looking at the first event i find this.

![](../../Img/Pasted%20image%2020250525164331.png)

Looks like the user somehow downloaded this sus .dll file
???
![](../../Img/Pasted%20image%2020250525164546.png)

![](../../Img/Pasted%20image%2020250525164619.png)

So the user was browsing around the internet and got to a compromised site and got infected.
After that demon.exe got to the system.

![](../../Img/Pasted%20image%2020250525165011.png)

![](../../Img/Pasted%20image%2020250525165028.png)

I thought that that was it, that was the first .exe that i saw.
But i was wrong.

We can see that at 1:38:30 PM of 10/05/22 Run.dll was downloaded to the machine with the Drive-by Compromise technique.
After that we can see that at 1:38:40 PM of 10/05/22 rundll32.exe was used to run run.dll.

![](../../Img/Pasted%20image%2020250525172029.png)

We could say that msedge.exe was THE process that started the infection as it was the first .exe (as Q2 says) that was used with Run.dll (the malicious dll that was first downloaded).

![](../../Img/Pasted%20image%2020250525172225.png)

But the answer is rundll32.exe as it was the .exe that was used to run the malicious dll.

