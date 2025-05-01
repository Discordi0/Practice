
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

A: 

Q5: 
A: 

Q6: 
A: 

Q7: 
A: 

Q8: 
A: 

Q9: 
A: 

Q10: 
A: 

Q11: 
A: 
