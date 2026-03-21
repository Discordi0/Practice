
A beginner level security challenge

Welcome to Lian_YU, this Arrowverse themed beginner CTF box! Capture the flags and have fun.

---

# Questions

## Q1: What is the Web Directory you found?
### A: 

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



## Q2: what is the file name you found?
### A: 

## Q3: what is the FTP Password?
### A: 

## Q4: what is the file name with SSH password?
### A: 

## Q5: user.txt
### A: 

## Q6: root.txt
### A: 
