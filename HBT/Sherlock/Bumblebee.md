
##### Sherlock Scenario

An external contractor has accessed the internal forum here at Forela via the Guest Wi-Fi, and they appear to have stolen credentials for the administrative user! We have attached some logs from the forum and a full database dump in sqlite3 format to help you in your investigation.



Q1: What was the username of the external contractor?

A: apoole1

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

Q2: What IP address did the contractor use to create their account?

A: 

Q3: What is the post_id of the malicious post that the contractor made?

A: 

Q4: What is the full URI that the credential stealer sends its data to?

A: 

Q5: When did the contractor log into the forum as the administrator? (UTC)

A: 

Q6: In the forum there are plaintext credentials for the LDAP connection, what is the password?

A: 

Q7: What is the user agent of the Administrator user?

A: 

Q8: What time did the contractor add themselves to the Administrator group? (UTC)

A: 

Q9: What time did the contractor download the database backup? (UTC)

A: 

Q10: What was the size in bytes of the database backup as stated by access.log?

A: 

