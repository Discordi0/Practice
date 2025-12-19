
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

