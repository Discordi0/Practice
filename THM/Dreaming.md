
Solve the riddle that dreams have woven.

While the king of dreams was imprisoned, his home fell into ruins.  

Can you help Sandman restore his kingdom?

---

# Questions

## Q1: What is the Lucien Flag?
### A: THM{TH3_L1BR4R14N}

First we start with an nmap scan

Before the scan finishes we can see that we have ssh and http

![](../Img/Pasted%20image%2020260322135933.png)

Checking the web page

This seems like the regular ubuntu/apache page

![](../Img/Pasted%20image%2020260322140029.png)

Nothing on the source code

We procced to use gobuster ans see if it has any other directory

![](../Img/Pasted%20image%2020260322140927.png)

This is what we get when we go to that page

![](../Img/Pasted%20image%2020260322140958.png)

Going to pluck get us here

![](../Img/Pasted%20image%2020260322141037.png)

There is also a login page

![](../Img/Pasted%20image%2020260322141059.png)

Nothing to see on the source code of both

lol password worked

![](../Img/Pasted%20image%2020260322141821.png)

Searching for an exploit got me this

![](../Img/Pasted%20image%2020260322142111.png)

Reading through the exploit we get it's usage

Download it and check if it works

![](../Img/Pasted%20image%2020260322142949.png)

![](../Img/Pasted%20image%2020260322143005.png)

We have some users

![](../Img/Pasted%20image%2020260322143036.png)

Next i got a reverse shell to my machine

Since Lucien it's the first flag, let's check for something interesting there

![](../Img/Pasted%20image%2020260322144025.png)

This is what we have in the first file

![](../Img/Pasted%20image%2020260322144058.png)

With the password i loged in with ssh

![](../Img/Pasted%20image%2020260322144417.png)

And got the flag

![](../Img/Pasted%20image%2020260322144444.png)

---
## Q2: What is the Death Flag?
### A: 

Checking what i can do i got this

![](../Img/Pasted%20image%2020260322144632.png)

And checking for death 

![](../Img/Pasted%20image%2020260322144728.png)

Going to opt again this is what that file has

![](../Img/Pasted%20image%2020260322144904.png)

Sadly password is redacted

Checking the lucien user history

![](../Img/Pasted%20image%2020260322145014.png)

We try the credentials

![](../Img/Pasted%20image%2020260322145318.png)


## Q3: What is the Morpheus Flag?
### A: 