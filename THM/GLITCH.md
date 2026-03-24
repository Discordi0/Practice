
Challenge showcasing a web app and simple privilege escalation. Can you find the glitch?

This is a simple challenge in which you need to exploit a vulnerable web application and root the machine. It is beginner oriented, some basic JavaScript knowledge would be helpful, but not mandatory. Feedback is always appreciated.

---

# Questions

## Q1: What is your access token?
### A: 

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



## Q2: What is the content of user.txt?

### A: 
## Q3: What is the content of root.txt?

### A: 