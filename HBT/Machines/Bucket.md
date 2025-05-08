
About Bucket

Bucket is a medium difficulty Linux machine that features [LocalStack](https://github.com/localstack/localstack) which simulates a local AWS environment. Web application is running on Apache server and the files are hosted on an open S3 bucket which allows us dropping a malicious PHP file and thus gain a reverse shell. At user&amp;#039;s home directory we can find an unfinished project which utilizes DynamoDB for database. Enumerating DynamoDB reveals credentials which can be reused to move laterally. An internal application found to be running as root, which is exploited to gain root access.



Q1: How many open TCP ports are listening on Bucket?

A: 2

With a nmap scan we can see the ports. map -sV -sC -Pn 10.10.10.212



Q2: What domain is hosting the images used on the website?

A: 

Q3: 
A: 

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



