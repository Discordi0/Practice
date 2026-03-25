Hey, do a flip!

Log in as the admin and capture the flag!

If you can...  

The server is listening on port 1337 via TCP . You can connect to it using Netcat or any other tool you prefer.

---

# Questions

## Q1: What is the flag?
### A: 

The attached file it's a python file

I connected to the ip and port and got this

![](../Img/Pasted%20image%2020260325000207.png)

I just press enter and got that, but if we look a the python file provided we can see some similarities

This is what i got

![](../Img/Pasted%20image%2020260325000323.png)

If we enter the provided credentials we would have gotten this

![](../Img/Pasted%20image%2020260325000408.png)

As i see it this file it's the same as the one on the machine

So here it should be the key to this challenge

![](../Img/Pasted%20image%2020260325000509.png)

My knowledge in encryption is literally 0, but as i understand this there is a encryption and decryption of a message in CBC.

And in the decryption side its looking for those credentials.

# Explanation

After a lot of reading i kinda got the idea.

If i give the script something similiar as what it is specting (fdmin instead of admin, as per the source code) and everything else as it should be. It would give me a encrypted cypher text

![](../Img/Pasted%20image%2020260325010358.png)

Now i can take this code and separate it in blocks (as per AES encryption)

Here we can see how the code is structured

![](../Img/Pasted%20image%2020260325010715.png)

So we could assume that our cypher text is like this

`access_username=fdmin&password=sUp3rPaSs1`

As per AES encryption we separate in blocks of 16 (as last block isn't 16 in lenght random is added)

`access_username=`
`fdmin&password=s`
`Up3rPaSs1#######`

We could infer that this is the structure of the cypher text

`304a8537b8b38dc8e87ca80126ac0bbf`

`47997cb18726f313c232b21b4b717736`

`25da7b78323bae0589556de929777e23`

Now in this ways it's easier to understand

What matter to us here it's that CBC will use the previous block to decrypt the current one through XOR

Now if the script is expecting "admin" instead of "fdmin" we would need to use the first letter

We know that 30 it's been used to get 47, so we can say that

30 xor 47 = d

30 being the first letter of block1, 47 being the first letter of block2, and d being the letter that we know it's there bc we sended it in "ddmin"


