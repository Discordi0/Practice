
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

Q4: What user is the webserver running as on Bucket?

A: www-data

I downloaded the files inside the adserver bucket, it turn out to be the same web page.
Looking the source code of the page didn't tell me anything.

![](../../Img/Pasted%20image%2020250508143800.png)

I uploaded a .txt file to the bucket.

![](../../Img/Pasted%20image%2020250508144256.png)

I tried with html and php files as well, both showed the same response.
It appears that they can be accessed, but as the files only say "hello", they do not render.

![](../../Img/Pasted%20image%2020250508145324.png)

I uploaded a phpinfo file to see what it returns and got this.

![](../../Img/Pasted%20image%2020250508150552.png)

I did the same but with a shell, i got this.

![](../../Img/Pasted%20image%2020250508150942.png)

Q5: What database is the roy user using in their `project`?

A: DynamoDb

There is a process that deletes the files i upload to the s3 bucket, so i had to try a lot of times.
After i got the shell, i searched for the user roy. I found this.

![](../../Img/Pasted%20image%2020250508152656.png)

Q6: What is the name of the table in the DynamoDB instance hosted on Bucket?

A: users

I had to change home dir because the aws configure command wasn't working.
After changing region of aws o could enumerate the tables of the db. (aws --endpoint-url http://localhost:4566 dynamodb list-tables)

![](../../Img/Pasted%20image%2020250508153349.png)

Q7: What is the roy user's password on Bucket?

A: n2vM-<_K_Q:.Aa2

I enumerate the contents of the table users. (dynamodb scan --table-name users)

![](../../Img/Pasted%20image%2020250508153544.png)


Q8: Submit the flag located in the roy user's home directory.

A: 06f74a552d7695d40a591cbfb4abba0b

Out of those 3 passwords, the 3rd worked.
Ssh into it with roy and look for the flag.

![](../../Img/Pasted%20image%2020250508153727.png)

Q9: What user is the web site on port 8000 running as?

A: root

I had to use the hint for this one.

![](../../Img/Pasted%20image%2020250508155502.png)

Q10: What is the full path to the directory containing the source for the site listening on 8000?

A: /var/www/bucket-app

It's in the above screenshot.

Q11: What string must be in the title of an entry in the `alerts` table for it to get processed and saved?

A: Ransomware

Going to the folder i found above, i found a folder that i couldn't enter

![](../../Img/Pasted%20image%2020250508155213.png)

So i changed to roy, and looked around a bit.
I the index.html file i found this. (It looks similar to the one i found in Q5).

![](../../Img/Pasted%20image%2020250508155156.png)

Q12: What is the name of the Java Jar file used to create PDFs by the site on port 8000?

A: pd4ml_demo.jar

A liitle bit below the Q11 screenshot.

![](../../Img/Pasted%20image%2020250508160054.png)

Q13: 
A: 

We all can see where this is going, but i have no idea how to create tables in Dynamodb, so i had to use this. (https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/getting-started-step-1.html) Under AWS Cli.

aws --endpoint-url=http://localhost:4566 dynamodb create-table --table-name
alerts --attribute-definitions AttributeName=title,AttributeType=S
AttributeName=data,AttributeType=S --key-schema
AttributeName=title,KeyType=HASH AttributeName=data,KeyType=RANGE --
provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5



