
Simple Reversing Challenge

In this challenge, you are asked to solve a simple reversing solution. Download and analyze the binary to discover the password.

_There may be anti-reversing measures in place!_

---

# Questions

## Q1: What is the password?
### A: thm{2@@25$gfsT&@L}

First we download an check the file

![](../Img/Pasted%20image%2020260318135300.png)

That doesn't seem normal, searching the internet i got that this is a common technique of obfuscation to avoid reverse engineering, what we need to do is change the 6th byte

I used hexedit and changed 02 for 01

![](../Img/Pasted%20image%2020260318140103.png)

I open it with ghidra and started searching

![](../Img/Pasted%20image%2020260318141300.png)

This seems hardcoded strings seem important

Specially when latter it does a check in them

![](../Img/Pasted%20image%2020260318141356.png)

Decode them

![](../Img/Pasted%20image%2020260318142133.png)

Order them and check

![](../Img/Pasted%20image%2020260318142202.png)

This is also the flag (THM{the weir string here})

Tags: [HEX Analysis](../Index/HEX%20Analysis.md) [Reverse Engineering](../Index/Reverse%20Engineering.md) 