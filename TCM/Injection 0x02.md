
If we try with the default credentials

![](../Img/Pasted%20image%2020260326182728.png)

It works

![](../Img/Pasted%20image%2020260326182809.png)

We can see that it give us a cookie

![](../Img/Pasted%20image%2020260326182859.png)

If we try to do sqli into username or password fields, it doesn't work. Even sqlmap say that they seem not injectable

![](../Img/Pasted%20image%2020260326183534.png)

But we can see that the page with the credentials redirects after getting the cookie

![](../Img/Pasted%20image%2020260326183723.png)

If we modify the cookie we got, we can see that we get an error (the )