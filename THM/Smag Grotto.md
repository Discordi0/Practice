
Follow the yellow brick road.

Deploy the machine and get root privileges.

---

# Questions 

## Q1: What is the user flag?
### A: 

We do an nmap scan first

![](../Img/Pasted%20image%2020260323213837.png)

We can see that there is port 80 open so we go there

![](../Img/Pasted%20image%2020260323213923.png)

Nothing to see on the site

Nothing on it's source code

Since there is nothing to do i use gobuster to check for more directories

We find this

![](../Img/Pasted%20image%2020260323214535.png)

This is that page

![](../Img/Pasted%20image%2020260323214908.png)

This is in it's source code

![](../Img/Pasted%20image%2020260323214519.png)

There is a pcap file in the page, download it and open it

There is just 10 packets (?)

![](../Img/Pasted%20image%2020260323214948.png)

In packet 4 there is credentials in clear txt

![](../Img/Pasted%20image%2020260323215025.png)

And this is where that page is

![](../Img/Pasted%20image%2020260323215159.png)

So we and the domain and subdomain to our /etc/hosts file

Then we search for the page

![](../Img/Pasted%20image%2020260323215506.png)

Materialize seems like some kind css library

![](../Img/Pasted%20image%2020260323215614.png)

admin and login take us to the same url

![](../Img/Pasted%20image%2020260323215641.png)

We enter the credentials and get this

![](../Img/Pasted%20image%2020260323215753.png)

I tried different commands and nothing, so i try with a reverse shell

![](../Img/Pasted%20image%2020260323220050.png)

![](../Img/Pasted%20image%2020260323220105.png)

I tried to get the flag but nothing

![](../Img/Pasted%20image%2020260323220223.png)

With no more idea to what to check i got linpeas to the machine

This cronjob seems interesting

![](../Img/Pasted%20image%2020260323220938.png)

Seems like this is copying jake's backup key and putting it in the autorized folder

So i our machine we need to generate a key pair

![](../Img/Pasted%20image%2020260323221655.png)

We then send our public key to the victim machine and replace jake's and wait

![](../Img/Pasted%20image%2020260323222117.png)

Now we can search the flag

![](../Img/Pasted%20image%2020260323222141.png)

---
## Q2: What is the root flag?
### A: 

We check what we can do

![](../Img/Pasted%20image%2020260323222243.png)

I use this to 
