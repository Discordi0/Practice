
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


## Q2: What is the root flag?
### A: 
