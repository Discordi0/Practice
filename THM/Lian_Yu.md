
A beginner level security challenge

Welcome to Lian_YU, this Arrowverse themed beginner CTF box! Capture the flags and have fun.

---

# Questions

## Q1: What is the Web Directory you found?
### A: 2100

First we do an nmap scan

![](../Img/Pasted%20image%2020260321154253.png)

Before the scan finishes we can see some of the open ports

I first checked out the web page

![](../Img/Pasted%20image%2020260321154349.png)

Not much to see on the source code

My nmap scan finally finished

![](../Img/Pasted%20image%2020260321155248.png)

Since the page in itself didn't have much to see, i used gobuster to search for directories

The first that i found it's this

![](../Img/Pasted%20image%2020260321155428.png)

We check it

![](../Img/Pasted%20image%2020260321155443.png)

![](../Img/Pasted%20image%2020260321155452.png)

Gobuster scan finished with no more hits, so i ran another one but with the medium list

I got this one also

![](../Img/Pasted%20image%2020260321162345.png)

Now we scan /island

First result

![](../Img/Pasted%20image%2020260321162412.png)

In the web page we find this

![](../Img/Pasted%20image%2020260321162459.png)

This was in the page source code

![](../Img/Pasted%20image%2020260321162538.png)

---
## Q2: what is the file name you found?
### A: green_arrow.ticket

Seems like i need to find a file, and with the hint we got i did a new gobuster scan but searching for a .ticket file

We can see that it got one file

![](../Img/Pasted%20image%2020260321163955.png)

And the page

![](../Img/Pasted%20image%2020260321164025.png)

---
## Q3: what is the FTP Password?
### A: !#th3h00d


The string we got from the page it's encoded, so i went to cyber chef and tried until i found the answer

![](../Img/Pasted%20image%2020260321164245.png)

---
## Q4: what is the file name with SSH password?
### A: 

Since we have some credentials we can try to login in ftp

![](../Img/Pasted%20image%2020260321164646.png)

This is what i gathered from ftp

![](../Img/Pasted%20image%2020260321165249.png)

I downloaded the png and jpg files

This is what exiftool got from the files

aa.jpg

![](../Img/Pasted%20image%2020260321165446.png)

Queen's

![](../Img/Pasted%20image%2020260321165513.png)

Leave's

![](../Img/Pasted%20image%2020260321165534.png)

Seems like the last file has an error in it's format

Checking it in a hexeditor we see the error (https://medium.com/@0xwan/png-structure-for-beginner-8363ce2a9f73)

After changing it's format we get this

![](../Img/Pasted%20image%2020260321170012.png)

This is what that image was

## Q5: user.txt
### A: 

## Q6: root.txt
### A: 
