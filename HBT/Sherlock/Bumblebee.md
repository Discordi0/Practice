##### Sherlock Scenario

An external contractor has accessed the internal forum here at Forela via the Guest Wi-Fi, and they appear to have stolen credentials for the administrative user! We have attached some logs from the forum and a full database dump in sqlite3 format to help you in your investigation.

___

### Q1: What was the username of the external contractor?

#### A: apoole1

To open the sqlite3 file i had to download something to open it, i got this (https://sqlitebrowser.org/).
Opening it we can see a lot of tables.

![](../../Img/Pasted%20image%2020250509162952.png)

Searching for interesting ones.

In attachments, nothing.

![](../../Img/Pasted%20image%2020250509163102.png)

Forum access, nothing.

![](../../Img/Pasted%20image%2020250509163130.png)

Ban list, nothing? what kind of forum doesn't ban anyone?
A dead one it seems.

![](../../Img/Pasted%20image%2020250509163237.png)

I see, it's full of bots.

![](../../Img/Pasted%20image%2020250509163309.png)

In logs we have something.

![](../../Img/Pasted%20image%2020250509163400.png)

User 48 is admin.

![](../../Img/Pasted%20image%2020250509163426.png)

The only ones with IP and that doesn't seem to be bots. (there is user 2 but that's admin).

![](../../Img/Pasted%20image%2020250509163539.png)

Seems like only 50 and 52 posted something.

![](../../Img/Pasted%20image%2020250509163818.png)

Looking a little bit closer i got it.

![](../../Img/Pasted%20image%2020250509164716.png)

___

### Q2: What IP address did the contractor use to create their account?

#### A: 10.10.0.78

I just used the one that was 2 column before his name. 

Opening the access.log file we can see that his IP it's the first one to access the site, so... that's that.

![](../../Img/Pasted%20image%2020250509170311.png)

___

Q3: What is the post_id of the malicious post that the contractor made?

A: 9

In the posts table we can see that there is only 1 post from that IP.

![](../../Img/Pasted%20image%2020250509170450.png)

Q4: What is the full URI that the credential stealer sends its data to?

A: http://10.10.0.78/update.php

In the same entry of the above question there is this.

![](../../Img/Pasted%20image%2020250509171051.png)

This is a full web page, i unminified because how reads all code in one line? (https://intteractivo.com/herramientas/desminificar-html/)

Found you.

![](../../Img/Pasted%20image%2020250509171215.png)

This calls a sethidden function.
The function looks for phpbb_token to dissable the hidden status of zbzbz1234. When it's called it creates a cookie and hidden goes to true again.

Q5: When did the contractor log into the forum as the administrator? (UTC)

A: 26/04/2023 10:53:12

In the log table we can see that the .78 IP login as admin.
Convert that to human time and that's the answer (UTC)

![](../../Img/Pasted%20image%2020250509172005.png)

Q6: In the forum there are plaintext credentials for the LDAP connection, what is the password?

A: Passw0rd1

In the config table.

![](../../Img/Pasted%20image%2020250509172340.png)

Q7: What is the user agent of the Administrator user?

A: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/112.0.0.0 Safari/537.36

We can search for his IP in the access.log file.

![](../../Img/Pasted%20image%2020250509172623.png)

![](../../Img/Pasted%20image%2020250509172553.png)


Q8: What time did the contractor add themselves to the Administrator group? (UTC)

A: 26/04/2023 10:53:51

Same as Q5. Find in the log table and convert.

![](../../Img/Pasted%20image%2020250509172711.png)

Q9: What time did the contractor download the database backup? (UTC)

A: 26/04/2023 11:01:38

In the log table, it only says that there was a backup, the question is the download, so to the access.log it is.

In the end of the file, we can see that the attacker's IP did a GET request to a backup. So it is that time -1 hour.

![](../../Img/Pasted%20image%2020250509173141.png)

Q10: What was the size in bytes of the database backup as stated by access.log?

A: 34707

In the same entry, we get the URI, then we have the protocol, the response code, and then there is the size.

![](../../Img/Pasted%20image%2020250509173335.png)

Tags: [DB Analysis](../../Index/DB%20Analysis.md) [Log Analysis](../../Index/Log%20Analysis.md) 