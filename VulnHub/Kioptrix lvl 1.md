
Machine IP: 10.0.2.15
redhat linux
Apache: 1.3.20 (?)
mod_ssl: 2.8.4
OpenSSL: 0.9.6b

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


