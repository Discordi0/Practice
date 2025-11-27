
During our penetration test our team found a Windows host running on the network and the corresponding credentials for the Administrator. It is required that we connect to the host and find the `hardcoded password` for the MSSQL service.

## Questions.

### Q1: What is the hardcoded password for the database connection in the MultimasterAPI.dll file?
#### A: D3veL0pM3nT!

RDP into the machine and find this.

![](../../Img/Pasted%20image%2020251127160356.png)

That wasn't the flag.
I just search for it.

![](../../Img/Pasted%20image%2020251127160558.png)

I opened the first with Notepad and found it.

![](../../Img/Pasted%20image%2020251127160655.png)



