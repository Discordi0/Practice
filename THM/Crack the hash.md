
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

#### A: Eternity22

This one was more tricky, it looked like MD5 and i tried to crack it but it didn't work, i tried with the hash in a file, other wordlists, the compressed and uncompressed version on rockyou and nothing. i know it's md4 but hashcat doesn't work.

I then tried with john and nothing again. So Crackstation it is (https://crackstation.net/)

![](../Img/Pasted%20image%2020251010201254.png)

___

## Level 2

This task increases the difficulty. All of the answers will be in the classic [rock you](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt) password list.

You might have to start using hashcat here and not online tools. It might also be handy to look at some example hashes on [hashcats page](https://hashcat.net/wiki/doku.php?id=example_hashes).

### Q1: Hash: F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85

#### A: paule

This one looked like sha-256 `-m 1400`.

![](../Img/Pasted%20image%2020251010201755.png)

___

### Q2: Hash: 1DFECA0C002AE40B8619ECF94819CC1B

#### A: n63umy8lkf4i

This one looked like MD5, it wasn't. So i kept going down and trying until i found it.
NTLM `-m 1000`.

![](../Img/Pasted%20image%2020251010202135.png)

___

### Q3: Hash: $6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.

Salt: aReallyHardSalt
#### A: 

It took me a little bit of time get the correct hash type for this one, in retrospective the $6 was more important that i realized.



### Q4: Hash: e5d8870e5bdd26602cab8dbe07a942c8669e56d6

Salt: tryhackme

#### A: 
