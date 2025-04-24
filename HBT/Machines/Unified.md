
Q1: Which are the first four open ports?

A: 22, 6789, 8080, 8443

Scan with nmap with -sV flag.

![](../../Img/Pasted%20image%2020250424150410.png)

Q2: What is the title of the software that is running running on port 8443?

A: UniFi Network

I had to run the scan again with the -sC flag
![](../../Img/Pasted%20image%2020250424151327.png)

Q3: What is the version of the software that is running?

A: 6.4.54

There wasn't version number in the scan, so digging around i went to the web page of this service (on port 8443) and got this.
![](../../Img/Pasted%20image%2020250424151922.png)

Q4: What is the CVE for the identified vulnerability?

A: CVE-2021-44228

Googleing aroudn i found this github repo (https://github.com/puzzlepeaches/Log4jUnifi) that had the answer.

Q5: What protocol does JNDI leverage in the injection?

A: LDAP

Looking at that cve we get it.
![](../../Img/Pasted%20image%2020250424153434.png)

Q6: What tool do we use to intercept the traffic, indicating the attack was successful?

A: 

Q7: What port do we need to inspect intercepted traffic for?

A: 

Q8: What port is the MongoDB service running on?

A: 

Q9: What is the default database name for UniFi applications?

A: 

Q10: What is the function we use to enumerate users within the database in MongoDB?

A: 

Q11: What is the function we use to update users within the database in MongoDB?

A: 

Q12: What is the password for the root user?

A: 

Q13: Submit user flag

A: 

Q14: Submit root flag

A: 
