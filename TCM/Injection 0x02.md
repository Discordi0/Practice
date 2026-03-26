
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

If we modify the cookie we got, we can see that we get an error (the length changes)

![](../Img/Pasted%20image%2020260326183842.png)

But if we try a sqli payload in the cookie we can see that it works

![](../Img/Pasted%20image%2020260326183955.png)

Now that we know that this works, we can begin to extract info from the DB

![](../Img/Pasted%20image%2020260326184528.png)

What this payload its doing it using substring() to compare the first character from the info we selected (select version()), to what we think it might be ('7')

As we saw it didn't work, so we try with other number

![](../Img/Pasted%20image%2020260326184731.png)

Now we know that the first number of the mysql version is 8

We can keep searching for the complete version

![](../Img/Pasted%20image%2020260326185029.png)

