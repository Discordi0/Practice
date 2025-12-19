
## Nmap

nmap -A -T4 -p- 10.0.2.154

![](../Img/Pasted%20image%2020251219154619.png)

## 80

http://10.0.2.154/

![](../Img/Pasted%20image%2020251219154750.png)

![](../Img/Pasted%20image%2020251219154848.png)

Not much to see

### ffuf

ffuf -w /home/discordio/Wordlists/discovery/directory_list_2.3_small.txt:FUZZ -u http://10.0.2.154/FUZZ


![](../Img/Pasted%20image%2020251219155216.png)

