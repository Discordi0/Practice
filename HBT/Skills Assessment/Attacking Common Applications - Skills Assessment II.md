
During an external penetration test for the company Inlanefreight, you come across a host that, at first glance, does not seem extremely interesting. At this point in the assessment, you have exhausted all options and hit several dead ends. Looking back through your enumeration notes, something catches your eye about this particular host. You also see a note that you don't recall about the `gitlab.inlanefreight.local` vhost.

Performing deeper and iterative enumeration reveals several serious flaws. Enumerate the target carefully and answer all the questions below to complete the second part of the skills assessment.

## Questions.

### Q1: What is the URL of the WordPress instance?
#### A: http://blog.inlanefreight.local

We start with a nmap scan 'nmap -p- -sCV --open 10.129.201.90'

![](../../Img/Pasted%20image%2020251127151854.png)

![](../../Img/Pasted%20image%2020251127151913.png)

We can see multiple services, but no wordpress, so we check the web page.

![](../../Img/Pasted%20image%2020251127152503.png)

Seems like a normal page.
Looking around a little bit we can see something about an employee blog.

![](../../Img/Pasted%20image%2020251127152553.png)

It get us here.

![](../../Img/Pasted%20image%2020251127152620.png)


![](../../Img/Pasted%20image%2020251127152646.png)

### Q2: What is the name of the public GitLab project?
#### A: 

### Q3: What is the FQDN of the third vhost?
#### A: 

### Q4: What application is running on this third vhost? (One word)
#### A: 

### Q5: What is the admin password to access this application?
#### A: 

### Q6: Obtain reverse shell access on the target and submit the contents of the flag.txt file.
#### A: 
