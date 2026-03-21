
John likes to live in a very Internet connected world. Maybe too connected...

John was working on his smart home appliances when he noticed weird traffic going across the network. Can you help him figure out what these weird network communications are?

---

# Questions

## Q1: What is the flag?
### A: flag{18d44fc0707ac8dc8be45bb83db54013}

Seems like this machine it's some type of iot device mitm(?)

We just need to start with an nmap scan

After a lot of tries i got something other that port 22 or just no response

![](../Img/Pasted%20image%2020260321180914.png)

Now, i don't know what this is so google it is (https://mosquitto.org/)

![](../Img/Pasted%20image%2020260321181028.png)

I tried to find some exploit but couldn't, but i got this (https://hacktricks.wiki/en/network-services-pentesting/1883-pentesting-mqtt-mosquitto.html?highlight=mosquitto#1883---pentesting-mqtt-mosquitto)

I tried with the python script from the "pentesting MQTT" section and got it working but no message recieved

![](../Img/Pasted%20image%2020260321183513.png)

So i installed mosquitto and mosquitto-clients

This method did work

![](../Img/Pasted%20image%2020260321183944.png)

Got something

![](../Img/Pasted%20image%2020260321184006.png)

Get it in cyberchef

![](../Img/Pasted%20image%2020260321184046.png)

If i subscribe to pub_topic and send a message to sub_topic we can see the response

![](../Img/Pasted%20image%2020260321184729.png)

This is the message decoded

![](../Img/Pasted%20image%2020260321184759.png)

If i get this correctly i need to base64 encode a message in that parameters and i get RCE(?)

Encoding the message

![](../Img/Pasted%20image%2020260321185133.png)

Sending it

![](../Img/Pasted%20image%2020260321185146.png)

The response

![](../Img/Pasted%20image%2020260321185201.png)

lmao ok

![](../Img/Pasted%20image%2020260321185237.png)

Changing it

Encoding

![](../Img/Pasted%20image%2020260321185307.png)

Sending

![](../Img/Pasted%20image%2020260321185323.png)

Recieving

![](../Img/Pasted%20image%2020260321185337.png)

Ok this is better

![](../Img/Pasted%20image%2020260321185354.png)

Now that we now that works, we need to get the flag

![](../Img/Pasted%20image%2020260321185626.png)

Sending it

![](../Img/Pasted%20image%2020260321185836.png)

Getting it

![](../Img/Pasted%20image%2020260321185853.png)

Decode it

![](../Img/Pasted%20image%2020260321185933.png)

Tags: [MQTT](../Index/MQTT.md) [Nmap](../Index/Nmap.md) 