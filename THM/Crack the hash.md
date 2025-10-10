
## Level 1.

Can you complete the level 1 tasks by cracking the hashes?

## Questions:

### Q1: 48bb6e862e54f2a795ffc4e541caed4d

#### A: easy

I am going to be comparing each hash with one on the list of hashcat webpage (https://hashcat.net/wiki/doku.php?id=example_hashes). i'm also going to be using the rockyou wordlist with all.
This one looks like MD5 so we use `-m 0`.

![](../Img/Pasted%20image%2020251010190921.png)

___

### Q2: CBFDAC6008F9CAB4083784CBD1874F76618D2A97
#### A: password123 

This one looks like SHA1 so we use `-m 100`

![](../Img/Pasted%20image%2020251010191303.png)

___

### Q3: 1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032

#### A: letmein

Looks like SHA256 so we use `-m 1400`.

![](../Img/Pasted%20image%2020251010191541.png)

___

### Q4: $2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom

#### A: bleh

This one looks like bcrypt so we use `-m 3200`. Hashcat may complain bc of the $ sings, just put the hash inside a .txt file and use that instead. It was also taking a lot of time so i had to create a 4 character list of rockyou.

![](../Img/Pasted%20image%2020251010194608.png)

___

### Q5: 279412f945939ba78ce0758d3fd83daa

#### A: 


## Level 2

This task increases the difficulty. All of the answers will be in the classic [rock you](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt) password list.

You might have to start using hashcat here and not online tools. It might also be handy to look at some example hashes on [hashcats page](https://hashcat.net/wiki/doku.php?id=example_hashes).


### Q1: 
#### A: 


### Q2: 
#### A: 

### Q3: 
#### A: 

### Q4: 
#### A: 
