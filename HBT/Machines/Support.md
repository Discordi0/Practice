
About Support

Support is an Easy difficulty Windows machine that features an SMB share that allows anonymous authentication. After connecting to the share, an executable file is discovered that is used to query the machine&amp;amp;amp;amp;#039;s LDAP server for available users. Through reverse engineering, network analysis or emulation, the password that the binary uses to bind the LDAP server is identified and can be used to make further LDAP queries. A user called `support` is identified in the users list, and the `info` field is found to contain his password, thus allowing for a WinRM connection to the machine. Once on the machine, domain information can be gathered through `SharpHound`, and `BloodHound` reveals that the `Shared Support Accounts` group that the `support` user is a member of, has `GenericAll` privileges on the Domain Controller. A Resource Based Constrained Delegation attack is performed, and a shell as `NT Authority\System` is received.



Q1: How many shares is Support showing on SMB?

A: 6

With nmap -sV -sC -Pn {ip}, i got this.

![](../../Img/Pasted%20image%2020250430141803.png)

We see that port 445 (smb) it's there. So we tried to connect to it. smbclient -L \\\\10.10.11.174\\

![](../../Img/Pasted%20image%2020250430142451.png)


Q2: Which share is not a default share for a Windows domain controller?

A: support-tools


The support share doesn't seem like standar with smb.

![](../../Img/Pasted%20image%2020250430142412.png)


Q3: Almost all of the files in this share are publicly available tools, but one is not. What is the name of that file?

A: UserInfo.exe.zip

All of the tools look familiar, except for UserInfo.

Q4: What is the hardcoded password used for LDAP in the UserInfo.exe binary?

A: nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz

This is what was inside the .zip

![](../../Img/Pasted%20image%2020250430142830.png)

UserInfo is again here. But it can't be opened because it is a .exe. S we have to decompile it.
Got this out of first result google.

![](../../Img/Pasted%20image%2020250430143533.png)

The linux version took me here (https://github.com/icsharpcode/AvaloniaILSpy)
After intalling it and opening the file i searched around until i found something interesting.

It connects there.

![](../../Img/Pasted%20image%2020250430150602.png)

Looking a little bit more i found this.

![](../../Img/Pasted%20image%2020250430150800.png)

I thought that this was the password, but i have to decrypt it.
I had to google a lot, and look at the hint, but i finally got it.

Q5: Which field in the LDAP data for the user named support stands out as potentially holding a password?

A: info

Having decoded the password, i connected to LDAP with Apache Directory. Navigating to the support related entries i found this.

![](../../Img/Pasted%20image%2020250430152540.png)

Q6: What open port on Support allows a user in the Remote Management Users group to run PowerShell commands and get an interactive shell?

A: 5985

I had to run the nmap

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
