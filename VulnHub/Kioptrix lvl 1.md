
Machine IP: 10.0.2.15
OpenSSH 2.9p2
redhat linux
Apache: 1.3.20 (?)
mod_ssl: 2.8.4
OpenSSL: 0.9.6b
Samba: 2.2.1a

### Nmap scan.

`nmap -p- -T4 -A 10.0.2.15`

![](../Img/Pasted%20image%2020251204135115.png)

![](../Img/Pasted%20image%2020251204135149.png)

### Web page

First check is port 80

![](../Img/Pasted%20image%2020251204135641.png)

Link clicked. (http://10.0.2.15/manual/mod/core.html#documentroot)

![](../Img/Pasted%20image%2020251204135819.png)

Not much to see in Inspector.

The only comment.

![](../Img/Pasted%20image%2020251204142958.png)


### Nikto

`nikto -h http://10.0.2.15/`

Possible vulnerabilities.

![](../Img/Pasted%20image%2020251204140444.png)

### dirbuster
`dirbuster -u http://10.0.2.15/ -l [Wordlist path]/discovery/directory_list_2.3_small.txt -e php`


### SMB

metasploit scanner/smb/smb_version

![](../Img/Pasted%20image%2020251204143720.png)

`smbclient -L \\10.0.2.15`

![](../Img/Pasted%20image%2020251204144102.png)

`smbclient \\\\10.0.2.15\\IPC$`

![](../Img/Pasted%20image%2020251204144544.png)

`smbclient \\\\10.0.2.15\\ADMIN$`

![](../Img/Pasted%20image%2020251204144630.png)

### SSH

`ssh 10.0.2.15`

![](../Img/Pasted%20image%2020251204145314.png)

`ssh 10.0.2.15 -oKexAlgorithms=+diffie-hellman-group1-sha1`

![](../Img/Pasted%20image%2020251204145353.png)


### Nessus

Basic Network Scan

![](../Img/Pasted%20image%2020251204162632.png)


### Mestasploit 

Searching for vulnerabilities with smb got trans2open.

Searching for that in metasploit

![](../Img/Pasted%20image%2020251204164934.png)

Use 1, set rhosts, change payload to shell_reverse_tcp

![](../Img/Pasted%20image%2020251204165055.png)

### SMB Exploit 

Use OpenLuck (https://github.com/heltonWernik/OpenLuck)

