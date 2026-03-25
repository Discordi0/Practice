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

After a lot of reading i kinda got the idea

The attack (bit flipping) 