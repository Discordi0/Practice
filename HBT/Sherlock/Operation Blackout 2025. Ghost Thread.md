
##### Sherlock Scenario

Byte Doctor suspects the attacker used a process injection technique to run malicious code within a legitimate process, leaving minimal traces on the file system. The logs reveal Win32 API calls that hint at a specific injection method used in the attack. Your task is to analyze these logs using a tool called API Monitor to uncover the injection technique and identify which legitimate process was targeted.


## Questions: 

### Q1:What process injection technique did the attacker use?

#### A: 

First we need to open the .exe with IDA.


### Q2: Which Win32 API was used to take snapshots of all processes and threads on the system?

#### A: 

### Q3: Which process is the attacker's binary attempting to locate for payload injection?

#### A: 

### Q4: What is the process ID of the identified process?

#### A: 

### Q5: What is the size of the shellcode?

#### A: 

### Q6: Which Win32 API was used to execute the injected payload in the identified process?

#### A: 

### Q7: The injection method used by the attacker executes before the main() function is called. Which Win32 API is responsible for terminating the program before main() runs?

#### A: 