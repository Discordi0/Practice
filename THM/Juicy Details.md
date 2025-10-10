
## **Introduction**

You were hired as a SOC Analyst for one of the biggest Juice Shops in the world and an attacker has made their way into your network. 

Your tasks are:

- Figure out what techniques and tools the attacker used
- What endpoints were vulnerable
- What sensitive data was accessed and stolen from the environment  

An IT team has sent you a **zip file** containing logs from the server. Download the attached file, type in "I am ready!" and get to work! There's no time to lose!

___

## **Reconnaissance**

Analyze the provided log files.

Look carefully at:

- What tools the attacker used
- What endpoints the attacker tried to exploit
- What endpoints were vulnerable

### Questions: 

#### Q1: What tools did the attacker use? (Order by the occurrence in the log)

##### A: nmap, hydra, sqlmap, curl, feroxbuster

We need to open access.log and check.

The first thing we can see.

![](../Img/Pasted%20image%2020251010000522.png)

Next it's just normal traffic until we get this.

![](../Img/Pasted%20image%2020251010000624.png)

After that it's normal traffic again until this.

![](../Img/Pasted%20image%2020251010000708.png)

Then we have all the sqlmap traffic follow by a couple of entries of normality and then this.

![](../Img/Pasted%20image%2020251010000838.png)

And lastly.

![](../Img/Pasted%20image%2020251010000907.png)

___

#### Q2: What endpoint was vulnerable to a brute-force attack?

##### A: /rest/user/login

Not sure if it is vulnerable but the attacker sure tried.

![](../Img/Pasted%20image%2020251010002039.png)

___

#### Q3: What endpoint was vulnerable to SQL injection?

##### A: /rest/products/search

This would be where the attacker used the SQLi tool.

![](../Img/Pasted%20image%2020251010002210.png)

___

#### Q4: What parameter was used for the SQL injection?

##### A: q

It can be see in the above's question screenshot.

___

#### Q5: What endpoint did the attacker try to use to retrieve files? (Include the /)

##### A: /ftp

We can see where the attacker tried to retieve specific files.

![](../Img/Pasted%20image%2020251010002619.png)

This can be corroborated by looking at the vsftpd.log file where we can see a download happening.

![](../Img/Pasted%20image%2020251010002747.png)

___

## Stolen data

Analyze the provided log files.

Look carefully at:  

- The attacker's movement on the website
- Response codes
- Abnormal query strings

___

### Questions:

#### Q1: What section of the website did the attacker use to scrape user email addresses?

##### A: product reviews

Looking more carefully the access.log file, the only section that could be use for that would be this.

![](../Img/Pasted%20image%2020251010003650.png)

___

#### Q2: Was their brute-force attack successful? If so, what is the timestamp of the successful login? (Yay/Nay, 11/Apr/2021:09:xx:xx +0000)

##### A: Yay, 11/Apr/2021:09:16:31 +0000

The brute-force that this question is refering it's where hydra was used, so if we look carefully we will see the successful response.

![](../Img/Pasted%20image%2020251010003925.png)

___

#### Q3: What user information was the attacker able to retrieve from the endpoint vulnerable to SQL injection?

##### A: email, password

To check this we need to go over to the sqlmap section of the log.
Near the end of that section where curl was used we can see what he managed to extract.

![](../Img/Pasted%20image%2020251010004309.png)

___

#### Q4: What files did they try to download from the vulnerable endpoint? (endpoint from the previous task, question #5)

##### A: coupons_2013.md.bak, www-data.bak

This is at the end of the file, where the attacker was using feroxbuster on the /ftp endpoint.
There are only 2 files named. (Answer is by alphabetical order, no accessed order).

![](../Img/Pasted%20image%2020251010004610.png)

This also it's in vsftpd.log.

![](../Img/Pasted%20image%2020251010004818.png)

___

#### Q5: What service and account name were used to retrieve files from the previous question? (service, username)

##### A: ftp, anonymous

In the vsftpd.log file just before the download of the files, we can see the successful login in a service with an account.

![](../Img/Pasted%20image%2020251010005001.png)

___

#### Q6: What service and username were used to gain shell access to the server? (service, username)

##### A: ssh, www-data

This ca be found in the last file that we never used (auth.log), where near the end of the log we can see an accepted login.

![](../Img/Pasted%20image%2020251010005237.png)

