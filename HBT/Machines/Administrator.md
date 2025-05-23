
About Administrator

`Administrator` is a medium-difficulty Windows machine designed around a complete domain compromise scenario, where credentials for a low-privileged user are provided. To gain access to the `michael` account, ACLs (Access Control Lists) over privileged objects are enumerated, leading us to discover that the user `olivia` has `GenericAll` permissions over `michael`, allowing us to reset his password. With access as `michael`, it is revealed that he can force a password change on the user `benjamin`, whose password is reset. This grants access to `FTP` where a `backup.psafe3` file is discovered, cracked, and reveals credentials for several users. These credentials are sprayed across the domain, revealing valid credentials for the user `emily`. Further enumeration shows that `emily` has `GenericWrite` permissions over the user `ethan`, allowing us to perform a targeted Kerberoasting attack. The recovered hash is cracked and reveals valid credentials for `ethan`, who is found to have `DCSync` rights ultimately allowing retrieval of the `Administrator` account hash and full domain compromise.


Machine Information

As is common in real life Windows pentests, you will start the Administrator box with credentials for the following account: Username: Olivia Password: ichliebedich



Q1: What is the lowest TCP port listening on Administrator?

A: 21

I did nmap scan: nmap -sV -sC -Pn 10.10.11.42

![](../../Img/Pasted%20image%2020250502141356.png)

Q2: What permission does the Olivia user have over the Michael user (as shown by BloodHound)?

A: GenericAll

As per the hint, we download and run bloodhound.py  with the credentials given to us. We start the db and run Bloodhund to check the results.

We search for olivia (the only user we have), and check the attributes that the user has.

![](../../Img/Pasted%20image%2020250502150237.png)

Q3: What permission does the Michael user have on the Benjamin user?

A: ForceChangePassword

We select michael node and check.

![](../../Img/Pasted%20image%2020250502151431.png)

Q4: What is the name of a non-default group that Benjamin is a part of?

A: Share Moderators

Check Banjamin.

![](../../Img/Pasted%20image%2020250502151559.png)

Q5: What is the Master Password for `Backup.psafe3`?

A: tekieromucho

First we need to log in as olivia.

![](../../Img/Pasted%20image%2020250502155230.png)

Then we need to change michael's password.

![](../../Img/Pasted%20image%2020250502155313.png)

We then login as michael and change the password of benjamin, to then log is as benjamin in ftp.

![](../../Img/Pasted%20image%2020250502155432.png)

We see that this user has the file.

![](../../Img/Pasted%20image%2020250502155504.png)

We get it, and crack it with hashcat.

![](../../Img/Pasted%20image%2020250502155124.png)

Q6: What is the Emily user's password on Administrator?

A: UXLCI5iETUsIBoFVTj8yQFKoHjXmb

The file was a Password safe file, so we install that.

![](../../Img/Pasted%20image%2020250502155733.png)

![](../../Img/Pasted%20image%2020250502160036.png)

Q7: Submit the flag located in the Emily user's home directory.

A: d16aa4e6d9b8334d51b1dd4c98b7f6cf

It's in the Desktop of the user.

![](../../Img/Pasted%20image%2020250502160400.png)

Q8: What permission does the Emily user have over the Ethan user?

A: GenericWrite

Check in Bloodhound

![](../../Img/Pasted%20image%2020250502160504.png)

Q9: What is the Ethan user's password on Administrator?

A: limpbizkit

I use the targetedkerberoasting.py attack.

![](../../Img/Pasted%20image%2020250502164924.png)

And crack it with hashcat.

![](../../Img/Pasted%20image%2020250502165119.png)

Q10: What permission does the Ethan user have over the domain (according to Bloodhound) that will allow for a full domain takeover?

A: DCSync

It's in OUTBOUND OBJECT CONTROL

![](../../Img/Pasted%20image%2020250502165524.png)

Q11: What is the Administrator user's NTLM hash?

A: 3dc553ce4b9fd20bd016e098d2d2fd2e

Secrets from impaket.

![](../../Img/Pasted%20image%2020250502165856.png)

Q12: Submit the flag located on the Administrator user's Desktop.

A: 19b5e0deb5ba108939a1e9795a4bb961

We use evil-winrm to connect.
Then just search it.

![](../../Img/Pasted%20image%2020250502170510.png)
