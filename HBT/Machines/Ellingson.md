

About Ellingson

Ellingson is a hard difficulty Linux box running a python flask server in debug mode, behind a nginx proxy. The debugger can be abused to execute code on the server in the context of the user running it. The user is found to be in the adm group which has access to the shadow.bak file, from which hashes can be gained and cracked, which allows for lateral movement. A SUID binary is found to be vulnerable to a buffer overflow - but as ASLR and NX are enabled - a ROP based exploitation needs to be performed to gain a root shell.


Q1: User flag
A: 

With a Nmap scan -sV -sC -Pn i got this.

![](../../Img/Pasted%20image%2020250512155255.png)

We can see that it has port 80 open, upon visiting the web page we see that the only thing clickable are articles.

![](../../Img/Pasted%20image%2020250512155543.png)

Trying to see if there is other articles we get this.

![](../../Img/Pasted%20image%2020250512155716.png)

We can see that it uses python3 and flask.
When i was looking at the error page i saw that if i hover the darker textbox there is an icon that appears.

![](../../Img/Pasted%20image%2020250512160521.png)

It is a debug console?

![](../../Img/Pasted%20image%2020250512160551.png)

Whe can see that the console does work.

![](../../Img/Pasted%20image%2020250512161716.png)

Poking around i found this.

![](../../Img/Pasted%20image%2020250512162349.png)

After more poking around i found that 

Q2: Root flag.
A: 
