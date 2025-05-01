
About Strutted

`Strutted` is an medium-difficulty Linux machine featuring a website for a company offering image hosting solutions. The website provides a Docker container with the version of Apache Struts that is vulnerable to `[CVE-2024-53677](https://nvd.nist.gov/vuln/detail/CVE-2024-53677)`, which is leveraged to gain a foothold on the system. Further enumeration reveals the `tomcat-users.xml` file with a plaintext password used to authenticate as `james`. For privilege escalation, we abuse `tcpdump` while being used with `sudo` to create a copy of the `bash` binary with the `SUID` bit set, allowing us to gain a `root` shell.



Q1: How many open TCP ports are listening on Strutted?

A: 2

The nmap scan was: nmap -sV -Pn 10.10.11.59  (with the -p- flag took 40 min. and it didn't even finished).

![](../../Img/Pasted%20image%2020250501154801.png)

Q2: Clicking Download triggers a zip file download containing the Docker environment for the application, what is the name of the application server running on the target?

A: tomcat

Downloading to the .zip file and extracting it i found this.

![](../../Img/Pasted%20image%2020250501155522.png)

In other file i found this.

![](../../Img/Pasted%20image%2020250501160026.png)


Q3: In a Java project, what is the name of this file that contains the dependencies for the application?

A: pom.xml

![](../../Img/Pasted%20image%2020250501160116.png)

Q4: What is the name of the MVC framework used by the application?

A: Apache Struts

Opening that file and looking at the dependencies (i had to google them because i didn't know what they were), i found it.

![](../../Img/Pasted%20image%2020250501160932.png)

Q5: What version of the framework does the application use?

A: 6.3.0.1

It was near the start of the file.

![](../../Img/Pasted%20image%2020250501161142.png)

Q6: What is the 2024 CVE ID assigned to a vulnerability in the file upload logic vulnerability in Apache Struts?

A: CVE-2024-53677 

Google struts vulnerability, it the only one in 2024.

![](../../Img/Pasted%20image%2020250501161530.png)

Q7: What system user is the web application running as on Strutted?

A: tomcat

For this CVE i used this (https://securityvulnerability.io/vulnerability/CVE-2024-53677) and the poc in it.
To get this to work i had an error that after a long time i resolved.

When i was trying to change the upload directory with ../../shell.jps, it didn't work, it just keep uploading it to where it always does.

![](../../Img/Pasted%20image%2020250501172041.png)

To resolve this i had to change the referer attribute.
from this

![](../../Img/Pasted%20image%2020250501172145.png)

To this.

![](../../Img/Pasted%20image%2020250501172029.png)

And it worked.

![](../../Img/Pasted%20image%2020250501172231.png)

With that out of the way, procede with the attack.

![](../../Img/Pasted%20image%2020250501172414.png)

Q8: What is the james user's password on Strutted?

A: 

Q9: 
A: 

Q10: 
A: 

Q11: 
A: 
