
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
#### A: makeInviteCode

We need to check the source code of the invite page in the Inspector tab and search for the script in question.

![](../../Img/Pasted%20image%2020251202170124.png)

This doesn't seem to have the answer.

Next we check the .js of Q2.

In the Response tab of the file we can chek it.

![](../../Img/Pasted%20image%2020251202170653.png)

We need to beautify/unminify it to see, i used this page. (https://lelinhtinh.github.io/de4js/)

![](../../Img/Pasted%20image%2020251202170816.png)

Reading through the code we can find the answer in the 2nd function name.

---

### Q4: The endpoint in `makeInviteCode` returns encrypted data. That message provides another endpoint to query. That endpoint returns a `code` value that is encoded with what very common binary to text encoding format. What is the name of that encoding?
#### A: Base64

First we need to check what does the endpoint in the js function get's us. `curl -X POST http://2million.htb/api/v1/invite/how/to/generate | jq`

![](../../Img/Pasted%20image%2020251202171646.png)

Me, not knowing what ROT13 is, i just google it, got this page. (https://cryptii.com/pipes/rot13-decoder)

![](../../Img/Pasted%20image%2020251202171752.png)

With the new endpoint we make another POST request. `curl -X POST http://2million.htb/api/v1/invite/generate | jq`

![](../../Img/Pasted%20image%2020251202171849.png)

Not knowing what this is, i use cyberchef Magic. (https://cyberchef.org/)

![](../../Img/Pasted%20image%2020251202171959.png)

---

### Q5: What is the path to the endpoint the page uses when a user clicks on "Connection Pack"?
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


