
This challenge revolves around subdomain enumeration.

Hello there,  
  
I am the CEO and one of the co-founders of futurevera.. In Futurevera, we believe that the future is in space. We do a lot of space research and write blogs about it. We used to help students with space questions, but we are rebuilding our support.  

Recently blackhat hackers approached us saying they could takeover and are asking us for a big ransom. Please help us to find what they can takeover.  
  
Our website is located at [https://futurevera.](https://futurevera.thm)

---

# Questions

## Q1: What's the value of the flag?
### A: flag{beea0d6edfcee06a59b83fb50ae81b2f}

First we add the domain to our /etc/hosts file

If we visit the page this is what we find

![](../Img/Pasted%20image%2020260326205355.png)

In sub-domain enumeration with ffuf i found this

![](../Img/Pasted%20image%2020260326212220.png)

After adding the sub-domains to the hosts file i tried to access them and got the invalid certificate, only that this time there was something interesting in the certificate

![](../Img/Pasted%20image%2020260326212540.png)

If we try to go to that page we get nothing, but the url is this

![](../Img/Pasted%20image%2020260326212642.png)

Tags: [Fuzzing](../Index/Fuzzing.md) 