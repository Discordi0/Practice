
## Suricata Rule Development Exercise: Detecting WMI Execution (Through [WMIExec](https://github.com/fortra/impacket/blob/master/examples/wmiexec.py))

**PCAP source**: [https://github.com/elcabezzonn/Pcaps](https://github.com/elcabezzonn/Pcaps)

**Attack description and possible detection points**: [https://labs.withsecure.com/publications/attack-detection-fundamentals-discovery-and-lateral-movement-lab-5](https://labs.withsecure.com/publications/attack-detection-fundamentals-discovery-and-lateral-movement-lab-5)

`Windows Management Instrumentation (WMI)` is a powerful feature in the Windows operating system that allows for management tasks, such as the execution of code or management of devices, both locally and remotely. As you might expect, this can be a very enticing tool for attackers who are seeking to execute malicious activities remotely.

To detect WMI execution (through `wmiexec`) over the network, we need to focus on the `SMB (Server Message Block)` and `DCOM (Distributed Component Object Model)` protocols, which are the primary means by which remote WMI execution is accomplished.

One method an attacker might use is to create a `Win32_Process` via the WMI service. In this instance, the attacker would create an instance of `Win32_ProcessStartup`, set its properties to control the environment of the new process, then call the `Create` method to start a new process such as `cmd.exe` or `powershell.exe`.

---

Review the previously referenced resource that discusses the network traces resulting from WMI execution, and then proceed to address the following question.


Q: There is a file named pipekatposhc2.pcap in the /home/htb-student/pcaps directory, which contains network traffic related to WMI execution. Add yet another content keyword right after the msg part of the rule with sid 2024233 within the local.rules file so that an alert is triggered and enter the specified payload as your answer. Answer format: C____e

A: 

First we have to connect to the machine, use SSH for that.

I first opened the file to see what keyword is already in the rule.

![](../../Img/Pasted%20image%2020250615141919.png)

Now that we know what keyword is already in use, i read the article provided to see if i can find something. I also downloaded the .pcap file to my machine to check it.

