
Boot2root, Web exploitation, Privilege escalation, LFI


---

# Questions

## Q1: Find a different hostname
### A: mafialive.thm

So first i do a quick default ports scan `nmap -A -T4 -vv 10.64.171.27`

![](../Img/Pasted%20image%2020260315140000.png)

We found port 80 so we need to check it out

In the web page we find this

![](../Img/Pasted%20image%2020260315143439.png)

---
## Q2: Find flag 1
### A: 

For this one we need to add that hostname to our "etc/hosts" file and access it

![](../Img/Pasted%20image%2020260315143952.png)

---
## Q3: Look for a page under development
### A: test.php

Now that we have a domain we can use ffuf or gobuster to check for files. `ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/common.txt -u http://mafialive.thm/FUZZ`

![](../Img/Pasted%20image%2020260315144653.png)

From this output we should know about "robots.txt" so we go there

![](../Img/Pasted%20image%2020260315144815.png)

Next we go to the next page

![](../Img/Pasted%20image%2020260315144831.png)

--- 
## Q4: Find flag 2
### A: thm{explo1t1ng_lf1}

Clicking the button results us in a parameter in the url and a message in the body of the page

![](../Img/Pasted%20image%2020260315144930.png)

Since i don't know much i google for LFI bypasses and found this (https://hacktricks.wiki/en/pentesting-web/file-inclusion/index.html?highlight=lfi%20byp#basic-lfi-and-bypasses)

I tried a lot and with this i found something "..//..//..//..//..//etc/passwd"

![](../Img/Pasted%20image%2020260315145621.png)

Now that i know that there is a user archangel i search for a bit and found this lol

![](../Img/Pasted%20image%2020260315145940.png)

I still need the flag for this question so with no more ideas to try i used the hint and got to work on it

First i tried with the mrrobot page and got this

![](../Img/Pasted%20image%2020260315150241.png)

![](../Img/Pasted%20image%2020260315150231.png)

Then i tried with the test.php page and got this

![](../Img/Pasted%20image%2020260315150539.png)

![](../Img/Pasted%20image%2020260315150625.png)

---
## Q5: Get a shell and find the user flag
### A: thm{lf1_t0_rc3_1s_tr1cky}

I didn't get a shell but i got the flag in Q4

---
## Q6: Get User 2 flag
### A: thm{h0r1zont4l_pr1v1l3g3_2sc4ll4t10n_us1ng_cr0n}

Searchin a bit on the internet i found that i can go from LFI to RCE with a poison attack, so i follow it

First i go to the apache/access.log and send it to burpsuite

![](../Img/Pasted%20image%2020260315152115.png)

I modified the user agent with `<?php system($_GET['cmd']); ?>` and send it

![](../Img/Pasted%20image%2020260315154918.png)

I the do a reverse shell from

## Q7: Root the machine and find the root flag
### A: 
