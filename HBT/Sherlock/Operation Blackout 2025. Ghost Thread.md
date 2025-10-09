
##### Sherlock Scenario

Byte Doctor suspects the attacker used a process injection technique to run malicious code within a legitimate process, leaving minimal traces on the file system. The logs reveal Win32 API calls that hint at a specific injection method used in the attack. Your task is to analyze these logs using a tool called API Monitor to uncover the injection technique and identify which legitimate process was targeted.


## Questions: 

### Q1: What process injection technique did the attacker use?

#### A: 

First we need to open the .exe with IDA.

![](../../Img/Pasted%20image%2020251009145856.png)

Having no clue what any of this means i started looking around and found this. (https://unprotect.it/technique/tls-callback/).
Since the question is asking for the technique, i looked for them as well. (https://attack.mitre.org/techniques/T1055/)
Readign through the sub-techniques, this one picked my interest. (https://attack.mitre.org/techniques/T1055/005/).

___

### Q2: Which Win32 API was used to take snapshots of all processes and threads on the system?

#### A: CreateToolhelp32Snapshot

I kept reading through the the sections present and found nothing. Next i looked at the imports tab and found this.

![](../../Img/Pasted%20image%2020251009150412.png)

![](../../Img/Pasted%20image%2020251009150437.png)

___

### Q3: Which process is the attacker's binary attempting to locate for payload injection?

#### A: notepad.exe

I tried to look for it in IDA but a couldn't found the process name.
All i could find is that something is looking(?) for an exe.

![](../../Img/Pasted%20image%2020251009152306.png)

So i had to use API Monitor.
When we select the .apmx64 and go to the module inject.exe we can see what it is looking for.

![](../../Img/Pasted%20image%2020251009162137.png)

___

### Q4: What is the process ID of the identified process?

#### A: 

Looking a

### Q5: What is the size of the shellcode?

#### A: 

### Q6: Which Win32 API was used to execute the injected payload in the identified process?

#### A: 

### Q7: The injection method used by the attacker executes before the main() function is called. Which Win32 API is responsible for terminating the program before main() runs?

#### A: 