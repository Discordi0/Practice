
About Cap

Cap is an easy difficulty Linux machine running an HTTP server that performs administrative functions including performing network captures. Improper controls result in Insecure Direct Object Reference (IDOR) giving access to another user's capture. The capture contains plaintext credentials and can be used to gain foothold. A Linux capability is then leveraged to escalate to root.


Q1: How many TCP ports are open?

A: 3

I did nmap -sV {ip}

![](../../Img/Pasted%20image%2020250429163426.png)

Q2: After running a "Security Snapshot", the browser is redirected to a path of the format `/[something]/[id]`, where `[id]` represents the id number of the scan. What is the `[something]`?

A: data

Go to the page of the machine.
in the dashboard it's the option.

![](../../Img/Pasted%20image%2020250429163825.png)

![](../../Img/Pasted%20image%2020250429163851.png)

Q3: Are you able to get to other users' scans?

A: yes

I changed de id in the url. in id = 4 i found something.

![](../../Img/Pasted%20image%2020250429164005.png)

Q4: What is the ID of the PCAP file that contains sensative data?

A: 0

I was going to do a burp intruder scan to see how many previous pcap files were in the server because i downloaded and opened 4 pcap files and didn't found anything.
But pooking around a little bit more i did id = 0 and found it.

![](../../Img/Pasted%20image%2020250429165241.png)

Q5: Which application layer protocol in the pcap file can the sensetive data be found in?

A: FTP

It's in the above screenshot.

Q6: We've managed to collect nathan's FTP password. On what other service does this password work?

A: SSH

In Q1 we saw that there is only 1 other service running in the machine.

Q7: Submit the flag located in the nathan user's home directory.

A: 

Q8: 
A: 

Q9: Submit the flag located in root's home directory.

A: 
