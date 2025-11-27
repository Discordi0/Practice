
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

With the name of the classes and the scripts we can see that this is WordPress

![](../../Img/Pasted%20image%2020251127152646.png)

---

### Q2: What is the name of the public GitLab project?
#### A: Virtualhost

Finding this one should be more easy given that we get a link to the GitLab instance in the briefing.
Browsing the link given to us get us here (http://gitlab.inlanefreight.local:8180/users/sign_in)

![](../../Img/Pasted%20image%2020251127152844.png)

After creating an account and loggin in we can search for projects (http://gitlab.inlanefreight.local:8180/explore)

![](../../Img/Pasted%20image%2020251127153029.png)

---

### Q3: What is the FQDN of the third vhost?
#### A: monitoring.inlanefreight.local

Reading through the public project we find this. (http://gitlab.inlanefreight.local:8180/root/virtualhost)

![](../../Img/Pasted%20image%2020251127153332.png)

It seems we can't just browse the page.

![](../../Img/Pasted%20image%2020251127153453.png)

After adding it to the /etc/hosts file we can access it.

![](../../Img/Pasted%20image%2020251127153821.png)

---

### Q4: What application is running on this third vhost? (One word)
#### A: nagios

It's in the above screenshot.

---

### Q5: What is the admin password to access this application?
#### A: oilaKglm7M09@CPL&^lC

Now that we know the name of the app, i went to check the project with tha name in GitLab.
INSTALL seems interesting, also what are those Last update dates...

![](../../Img/Pasted%20image%2020251127154203.png)

Reading it for a bit we find this.

![](../../Img/Pasted%20image%2020251127154316.png)

It works.

![](../../Img/Pasted%20image%2020251127154455.png)


---

### Q6: Obtain reverse shell access on the target and submit the contents of the flag.txt file.
#### A: 

Searching the version of nagios on exploidb i found this. (https://www.exploit-db.com/exploits/49422)

I downloaded the script and check for the usage.

![](../../Img/Pasted%20image%2020251127155111.png)


