

About Ellingson

Ellingson is a hard difficulty Linux box running a python flask server in debug mode, behind a nginx proxy. The debugger can be abused to execute code on the server in the context of the user running it. The user is found to be in the adm group which has access to the shadow.bak file, from which hashes can be gained and cracked, which allows for lateral movement. A SUID binary is found to be vulnerable to a buffer overflow - but as ASLR and NX are enabled - a ROP based exploitation needs to be performed to gain a root shell.


Q1: User flag
A: 

With a Nmap scan -sV -sC -Pn i got this.

![](../../Img/Pasted%20image%2020250512155255.png)

We can see that it has port 80 open, upon visiting the web page we see that the only thing clickable are articles.

![](../../Img/Pasted%20image%2020250512155543.png)



Q2: Root flag.
A: 
