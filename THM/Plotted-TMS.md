
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

So we move to port 445, got the same default page

![](../Img/Pasted%20image%2020260319190216.png)

And nothing on the source code, so we move to fuzzing

On the management

![](../Img/Pasted%20image%2020260319190625.png)

We have a login form

![](../Img/Pasted%20image%2020260319190654.png)

We try different payloads until 1 hit (``admin' or '1'='1'#``)

Seems like we are admins

![](../Img/Pasted%20image%2020260319190807.png)

I went to "my account" and it seems like we can upload a file here

![](../Img/Pasted%20image%2020260319190946.png)

I got a reverse shell, change the values, uploaded it and it worked (https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php)

![](../Img/Pasted%20image%2020260319191301.png)

I got linpeas onto the system, and i got a couple of interesting things, but this is the best

![](../Img/Pasted%20image%2020260319194113.png)

But first we need to be plot_admin, for that we use this

![](../Img/Pasted%20image%2020260319194241.png)


## Q2: What is root.txt?
### A: 