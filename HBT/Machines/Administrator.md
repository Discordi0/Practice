
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

A: 

Q6: 
A: 

Q7: 
A: 

Q8: 
A: 

Q9: 
A: 

Q10: 
A: 

Q11: 
A: 

Q12: 
A: 
