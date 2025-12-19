
Ip: 10.0.2.154
php: 7.3.27-1
navigate cms: 2.8

## Nmap

nmap -A -T4 -p- 10.0.2.154

![](../Img/Pasted%20image%2020251219154619.png)

## 80

### First step
http://10.0.2.154/

![](../Img/Pasted%20image%2020251219154750.png)

![](../Img/Pasted%20image%2020251219154848.png)

Not much to see

### Fuzzing

ffuf -w /home/discordio/Wordlists/discovery/directory_list_2.3_small.txt:FUZZ -u http://10.0.2.154/FUZZ


![](../Img/Pasted%20image%2020251219155216.png)

### Checking results

It's a file, download it.

![](../Img/Pasted%20image%2020251219155518.png)

## 53

### dnsrecon

dnsrecon -r 127.0.0.0/24 -n 10.0.2.154 -d qwe

![](../Img/Pasted%20image%2020251219155919.png)

add to /etc/hosts

### Web page

http://blackpearl.tcm

![](../Img/Pasted%20image%2020251219160211.png)

### Fuzzing

ffuf -w /home/discordio/Wordlists/discovery/directory_list_2.3_small.txt:FUZZ -u http://blackpearl.tcm/FUZZ

![](../Img/Pasted%20image%2020251219160538.png)

### /navigate

![](../Img/Pasted%20image%2020251219160438.png)

![](../Img/Pasted%20image%2020251219160647.png)

#### Attacks

search for an exploit on google, i got this easy one (https://www.rapid7.com/db/modules/exploit/multi/http/navigate_cms_rce/)

##### Metasploit

Follow the steps in the rapid7 page, set the parameters and run.

![](../Img/Pasted%20image%2020251219161314.png)

Upgrade the shell.
`python3 -c 'import pty;pty.spawn("/bin/bash")'`

![](../Img/Pasted%20image%2020251219161729.png)

### linpeas

Get linpeas into the machine, change it's permissions and run it.

