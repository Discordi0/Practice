
Now with more Cat Pictures!


---

# Questions

## Q1: What is Flag 1?
### A: 

We start with an nmap scan `nmap -sV -A -T4 -vv 10.64.149.15`

![](../Img/Pasted%20image%2020260316092819.png)

![](../Img/Pasted%20image%2020260316092839.png)

![](../Img/Pasted%20image%2020260316092854.png)

We got several ports, let's first check the web pages

Searching for just the ip we get this pictures site

![](../Img/Pasted%20image%2020260316093019.png)

Clicking through the site i can see where the pictures are located 

![](../Img/Pasted%20image%2020260316093111.png)

If u click share it gets u this link

![](../Img/Pasted%20image%2020260316093203.png)

There is also a sign in

![](../Img/Pasted%20image%2020260316093250.png)

Checking the information of all the pictures, we find this in the first one

![](../Img/Pasted%20image%2020260316094231.png)

With exiftool we can find out what does this picture has

![](../Img/Pasted%20image%2020260316094714.png)

In that link we get this

![](../Img/Pasted%20image%2020260316094752.png)

We get here

![](../Img/Pasted%20image%2020260316094841.png)

we try the credentials that we found and we get in

![](../Img/Pasted%20image%2020260316094934.png)

I read all the file from /ansible and inside flag1.txt we find the first answer

![](../Img/Pasted%20image%2020260316095059.png)

---
## Q2: What is Flag 2?
### A: 

Now if we go to ansible in port 1337 we get this

![](../Img/Pasted%20image%2020260316095401.png)

Running the playbook we can see that it runs the code that i found in gitea

![](../Img/Pasted%20image%2020260316095720.png)

![](../Img/Pasted%20image%2020260316095733.png)

So i tried to change the code from gitea to a reverse shell and see if it works

![](../Img/Pasted%20image%2020260316100259.png)

And it works

![](../Img/Pasted%20image%2020260316100345.png)

---
## Q3: What is Flag 3?
### A: 

Now that we have a connection, i get linpeas in the machine and run it

The first we get it the sudo version

![](../Img/Pasted%20image%2020260316101713.png)

I used the cve that was listed below and got the exploit (https://github.com/blasty/CVE-2021-3156)

Transfer it to the machine and run it

![](../Img/Pasted%20image%2020260316103201.png)

Search for the last flag

![](../Img/Pasted%20image%2020260316103349.png)


Tags: [[]]