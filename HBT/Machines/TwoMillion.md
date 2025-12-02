
#### About

TwoMillion is an Easy difficulty Linux box that was released to celebrate reaching 2 million users on HackTheBox. The box features an old version of the HackTheBox platform that includes the old hackable invite code. After hacking the invite code an account can be created on the platform. The account can be used to enumerate various API endpoints, one of which can be used to elevate the user to an Administrator. With administrative access the user can perform a command injection in the admin VPN generation endpoint thus gaining a system shell. An .env file is found to contain database credentials and owed to password re-use the attackers can login as user admin on the box. The system kernel is found to be outdated and CVE-2023-0386 can be used to gain a root shell.

---

## Questions.

### Q1: How many TCP ports are open?
#### A: 2

First we need to do a scan, i use nmap. `nmap -p- -sVC --open 10.10.11.221`

![](../../Img/Pasted%20image%2020251202164610.png)

---

### Q2: What is the name of the JavaScript file loaded by the `/invite` page that has to do with invite codes?
#### A: inviteapi.min.js

To do this i just used Firefox, if we try to go to the IP address we get this error.

![](../../Img/Pasted%20image%2020251202164809.png)

After adding the ip and the domain to /etc/hosts we can enter the page.

![](../../Img/Pasted%20image%2020251202165124.png)

If we go to the url in the question and check the network tab in the developer tools we can see the .js file.

![](../../Img/Pasted%20image%2020251202165247.png)

---

### Q3: What JavaScript function on the invite page returns the first hint about how to get an invite code? Don't include () in the answer.
#### A:

We need to check the source code of the page in the Inspetctor tab and search for the script in question.

![](../../Img/Pasted%20image%2020251202170124.png)



### Q4: 
#### A:

### Q5: 
#### A:

### Q6: 
#### A:

### Q7: 
#### A:

### Q8: 
#### A:

### Q9: 
#### A:

### Q10: 
#### A:

### Q11: 
#### A:

### Q12: 
#### A:

### Q13: 
#### A:

### Q14: 
#### A:

### Q15: 
#### A:

### Q16: 
#### A:


