
About Bucket

Bucket is a medium difficulty Linux machine that features [LocalStack](https://github.com/localstack/localstack) which simulates a local AWS environment. Web application is running on Apache server and the files are hosted on an open S3 bucket which allows us dropping a malicious PHP file and thus gain a reverse shell. At user&amp;#039;s home directory we can find an unfinished project which utilizes DynamoDB for database. Enumerating DynamoDB reveals credentials which can be reused to move laterally. An internal application found to be running as root, which is exploited to gain root access.



Q1: How many open TCP ports are listening on Bucket?

A: 2

With a nmap scan we can see the ports. map -sV -sC -Pn 10.10.10.212

![](../../Img/Pasted%20image%2020250508140220.png)

Q2: What domain is hosting the images used on the website?

A: s3.bucket.htb

Upon opening the page, we can see that there is no image present, so i inspect where the an image should go and find the domain.

![](../../Img/Pasted%20image%2020250508141159.png)

Q3: What is the bucket name in use on s3.bucket.htb?

A: adserver

Adding the new domain to the /etc/hosts file, we can see what is it.
This is all we can see with just browsing it.

![](../../Img/Pasted%20image%2020250508142126.png)

Connecting to it with awscli and enumerating we get this.

![](../../Img/Pasted%20image%2020250508142253.png)

Q4: 
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

Q12:
A: 

Q13: 
A: 



