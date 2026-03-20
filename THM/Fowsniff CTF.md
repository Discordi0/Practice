
Hack this machine and get the flag. There are lots of hints along the way and is perfect for beginners!

---

# Questions

## Q1: What was seina's password to the email service?
### A: scoobydoo2

So first we do an nmap scan

![](../Img/Pasted%20image%2020260319234145.png)

On the web page on port 80 there is this message

![](../Img/Pasted%20image%2020260319234422.png)

Going to that twitter we find these

![](../Img/Pasted%20image%2020260319234945.png)

![](../Img/Pasted%20image%2020260319234956.png)

Had to look them up in the waybackmachine

![](../Img/Pasted%20image%2020260319235015.png)

This is the content

![](../Img/Pasted%20image%2020260319234929.png)

mauer

![](../Img/Pasted%20image%2020260319235244.png)

mustikka

![](../Img/Pasted%20image%2020260319235333.png)

tegel

![](../Img/Pasted%20image%2020260319235411.png)

baksteen

![](../Img/Pasted%20image%2020260319235449.png)

seina

![](../Img/Pasted%20image%2020260319235519.png)

stone

Couldn't crack it :c

mursten

![](../Img/Pasted%20image%2020260319235724.png)

parede

![](../Img/Pasted%20image%2020260319235752.png)

sciana

![](../Img/Pasted%20image%2020260319235828.png)

Now that we have the values we can move to the next step which is metasploit

Searching for pop3 we have this

![](../Img/Pasted%20image%2020260320000038.png)

Since we need to login we are going to use 3

We set the options an run it

![](../Img/Pasted%20image%2020260320002408.png)

---
## Q2: Looking through her emails, what was a temporary password set for her?

### A: S1ck3nBluff+secureshell

Now that we have credentials we are going to try to connect

![](../Img/Pasted%20image%2020260320002853.png)

We read the first message

![](../Img/Pasted%20image%2020260320002938.png)

As per the instructions we proceed to connect via ssh and check for group perm and files

![](../Img/Pasted%20image%2020260320003735.png)

In the cube fil

![](../Img/Pasted%20image%2020260320005211.png)
