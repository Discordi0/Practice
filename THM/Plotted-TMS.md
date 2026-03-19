
Everything here is plotted!

Happy Hunting!

Tip: Enumeration is key!

---

# Questions

## Q1: What is user.txt?
### A: 

As the first step we need to do an nmap scan 

![](../Img/Pasted%20image%2020260319162609.png)

![](../Img/Pasted%20image%2020260319162624.png)

Since there is port 80 and 445 we check them in our browser

On port 70 we get the usual page

![](../Img/Pasted%20image%2020260319172628.png)

On it's source code

![](../Img/Pasted%20image%2020260319172606.png)

That link get us here

![](../Img/Pasted%20image%2020260319172828.png)

With that i proceded to use gobuster

In admin there is an id_rsa key

![](../Img/Pasted%20image%2020260319172940.png)

![](../Img/Pasted%20image%2020260319172953.png)

On shadow

![](../Img/Pasted%20image%2020260319173131.png)

On passwd

![](../Img/Pasted%20image%2020260319173102.png)

Same string on both

lmao 

![](../Img/Pasted%20image%2020260319173217.png)

The one from admin id_rsa

![](../Img/Pasted%20image%2020260319173255.png)

Trying fuzzin the directories didn't got anything usefull

So we move to port 445


## Q2: What is root.txt?
### A: 