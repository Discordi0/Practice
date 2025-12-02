
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
#### A: /api/v1/user/vpn/generate

Seems like i need to register to check this out, so we use the invite code that we just got.

The code get us this.

![](../../Img/Pasted%20image%2020251202172243.png)

After some tries i get and account and login (for some reason test, test1, test2 were already used).

![](../../Img/Pasted%20image%2020251202172516.png)

After looking around i found were the button is. (http://2million.htb/home/access)

When we click the button there is only 1 query that gets made, check the headers.

![](../../Img/Pasted%20image%2020251202172944.png)

---

### Q6: How many API endpoints are there under `/api/v1/admin`?
#### A: 3

To check first i did a simple curl to the base(?) endpoint. 

![](../../Img/Pasted%20image%2020251202173406.png)

Got nothing, next we try with -v.

![](../../Img/Pasted%20image%2020251202173523.png)

We need to get the cookie from our session.

![](../../Img/Pasted%20image%2020251202173802.png)

With the cookie set we get the status code 200 and got a new clue.

![](../../Img/Pasted%20image%2020251202173927.png)

Just count the ones under admin.

---

### Q7: What API endpoint can change a user account to an admin account?
#### A: /api/v1/admin/settings/update

With just the name of the endpoint we can get this answer.

---

### Q8: What API endpoint has a command injection vulnerability in it?
#### A: /api/v1/admin/vpn/generate

Checking the .../update endpoint (changing to PUT request) we get this.

![](../../Img/Pasted%20image%2020251202174407.png)

We change to content type json.

![](../../Img/Pasted%20image%2020251202174523.png)

We add the parameter email.

![](../../Img/Pasted%20image%2020251202174656.png)

Add the next parameter.

![](../../Img/Pasted%20image%2020251202174809.png)

It's not True, need to change it if you tried that.

![](../../Img/Pasted%20image%2020251202174907.png)

Seems like we are admin now, we can check with one of the other admin endpoints.

![](../../Img/Pasted%20image%2020251202175405.png)

There is only one other endpoint in the admin "category", se we check that.

We try with only the cookien and content-type and get this.

![](../../Img/Pasted%20image%2020251202175713.png)

Add the parameter.

![](../../Img/Pasted%20image%2020251202180121.png)

We get the vpn key.

I don't see that this response points me in any other direction so i started to prove this endpoint and got this.

![](../../Img/Pasted%20image%2020251202180322.png)

---

### Q9: What file is commonly used in PHP applications to store environment variable values?
#### A: .env

It just the name that it is used.

---

### Q10: Submit the flag located in the admin user's home directory.
#### A: 9702e5a41ab8b8dd6c61336442ad0885

i just cat .env and got this.

![](../../Img/Pasted%20image%2020251202181040.png)

To check i cat /etc/passwd.

![](../../Img/Pasted%20image%2020251202181253.png)

As the other port that was open was SSH i tried to login with the admin credentials.

![](../../Img/Pasted%20image%2020251202181429.png)

Search for the flag.

![](../../Img/Pasted%20image%2020251202181633.png)

---

### Q11: What is the email address of the sender of the email sent to admin?
#### A: ch4p@2million.htb

Since i had no idea where to begin to check i used find. `find / -iname "mail"`

![](../../Img/Pasted%20image%2020251202181958.png)

Inside there is a file, check it.

![](../../Img/Pasted%20image%2020251202182219.png)

---

### Q12: What is the 2023 CVE ID for a vulnerability in that allows an attacker to move files in the Overlay file system while maintaining metadata like the owner and SetUID bits?
#### A: CVE-2023-0386

After searching for it and reading a little bit i found this one that seems like it's the one. (https://www.cve.news/cve-2023-0386/).

---

### Q13: Submit the flag located in root's home directory.
#### A:

Searching for a PoC i found this. (https://github.com/xkaneiki/CVE-2023-0386)



![](../../Img/Pasted%20image%2020251202183254.png)


### Q14: 
#### A:

### Q15: 
#### A:

### Q16: 
#### A:


