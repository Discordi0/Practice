
Exploit a Windows machine in this beginner level challenge.

This task involves you, paying attention to details and finding the 'keys to the castle'.

This room is designed for beginners, however, everyone is welcomed to try it out!

Enjoy the Anthem.

In this room, you don't need to brute force any login page. Just your preferred browser and Remote Desktop.

Please give the box up to 5 minutes to boot and configure.

---

# Questions

## Q1: What port is for the web server?
### A: 80

We do an nmap scan on the machine

Before the scan even finishes we can see the port

![](../Img/Pasted%20image%2020260320134718.png)

---
## Q2: What port is for remote desktop service?
### A: 3389

We got it in the nmap scan in Q1

---
## Q3: What is a possible password in one of the pages web crawlers check for?
### A: UmbracoIsTheBest!

Visiting the page this is what we find

![](../Img/Pasted%20image%2020260320135047.png)

Checking the source code i found this

![](../Img/Pasted%20image%2020260320135649.png)

I kept searching and found this in the profile of one of the autors

![](../Img/Pasted%20image%2020260320140439.png)

At a first glance this i what i found, now for the question we know that crawlers look for robots.txt so we go to that page

![](../Img/Pasted%20image%2020260320141124.png)

---
## Q4: What CMS is the website using?
### A: umbraco

We get it from robots.txt

---
## Q5: What is the domain of the website?
### A: anthem.com

It's everywhere

---
## Q6: What's the name of the Administrator
### A: Solomon Grundy

This one was more tricky, while looking around the page i found a poem

![](../Img/Pasted%20image%2020260320141856.png)

Googling that got me to a wikipedia page (https://en.wikipedia.org/wiki/Solomon_Grundy_(nursery_rhyme))

![](../Img/Pasted%20image%2020260320141921.png)

---
## Q7: Can we find find the email address of the administrator?
### A: SG@anthem.com

This was in one of the articles

![](../Img/Pasted%20image%2020260320141948.png)

We can see how the email names are formed

---
## Q8: What is flag 1?
### A: 

This one i didn't found in my initial search, so i started to llok again and found it in the metadata of one of the articles

![](../Img/Pasted%20image%2020260320142948.png)

---
## Q9: What is flag 2?
### A: THM{G!T_G00D}

This was found while searching the source code, in the search bar(?)

---
## Q10: What is flag 3?
### A: THM{L0L_WH0_D15}

Inside the profile page of one of the authors of the blog

---
## Q11: What is flag 4?
### A: THM{AN0TH3R_M3TA}

Since this one was the other that i didn't find, i did the same thing as in flag 1 but with the other article

![](../Img/Pasted%20image%2020260320143119.png)

---
## Q12: Gain initial access to the machine, what is the contents of user.txt?
### A: THM{N00T_NO0T}

We can RDP into the machine with the credentials that we found (name of the admin and pass from robots.txt)

![](../Img/Pasted%20image%2020260320143401.png)

![](../Img/Pasted%20image%2020260320143421.png)

---
## Q13: Can we spot the admin password?
### A: ChangeMeBaby1MoreTime

I started to look in the machine and came across this

![](../Img/Pasted%20image%2020260320143607.png)

So i do what it says and add me in it's permissions

![](../Img/Pasted%20image%2020260320143736.png)

And open it

![](../Img/Pasted%20image%2020260320143746.png)

---
## Q14: Escalate your privileges to root, what is the contents of root.txt?
### A: THM{Y0U_4R3_1337}

Now that we have the password i just opened cmd with admin priv

![](../Img/Pasted%20image%2020260320143945.png)

Search for the flag

![](../Img/Pasted%20image%2020260320144022.png)

Tags: [Nmap](../Index/Nmap.md) [Win Privesc](../Index/Win%20Privesc.md) 