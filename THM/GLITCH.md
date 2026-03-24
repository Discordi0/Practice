
Challenge showcasing a web app and simple privilege escalation. Can you find the glitch?

This is a simple challenge in which you need to exploit a vulnerable web application and root the machine. It is beginner oriented, some basic JavaScript knowledge would be helpful, but not mandatory. Feedback is always appreciated.

---

# Questions

## Q1: What is your access token?
### A: this_is_not_real

We first do an nmap scan 

![](../Img/Pasted%20image%2020260324144219.png)

Since we have port 80 open we can check the web page

We just get a pixelated image with title "not allowed"

![](../Img/Pasted%20image%2020260324144318.png)

In the source code we find this directories

![](../Img/Pasted%20image%2020260324144445.png)

If we go to /api/access we get this json formated string(?)

![](../Img/Pasted%20image%2020260324144545.png)

That seems base64 enconded so we go to decode it (https://cyberchef.org/)

![](../Img/Pasted%20image%2020260324144625.png)

With no much to go on i started a gobuster dir fuzzing(?)

This are the first results

![](../Img/Pasted%20image%2020260324144912.png)

/secret just gets us to another page with the same image and source code

![](../Img/Pasted%20image%2020260324145018.png)

/Secret it's the same thing

![](../Img/Pasted%20image%2020260324145110.png)

Now that we have "mapped" the base site, we can use the token that we got to see what changes in these pages

Now on the main page we get this, the title alse changed to "sad."

![](../Img/Pasted%20image%2020260324145726.png)

On the bottom of the site we can  find this

![](../Img/Pasted%20image%2020260324145924.png)

That url take us here

![](../Img/Pasted%20image%2020260324150002.png)

/api/items is this

![](../Img/Pasted%20image%2020260324150117.png)

/secrets and /Secrets changed to this

![](../Img/Pasted%20image%2020260324150043.png)

I just realized that we already have the answer to this question so lets move on

---
## Q2: What is the content of user.txt?

### A: 

Checking the methods as per the hint get us this

![](../Img/Pasted%20image%2020260324150837.png)

So we need to fuzz this now

![](../Img/Pasted%20image%2020260324151410.png)

We can see that cmd works so i searched for an reverse shell (https://medium.com/@sebnemK/node-js-rce-and-a-simple-reverse-shell-ctf-1b2de51c1a44)

We tried it and it works

![](../Img/Pasted%20image%2020260324152302.png)



## Q3: What is the content of root.txt?

### A: 