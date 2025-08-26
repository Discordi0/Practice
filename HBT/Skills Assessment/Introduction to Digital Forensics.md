
Upon identifying signs of data exfiltration from an unusual process on a system, the SOC manager tasked you with conducting a forensic investigation through `Velociraptor`.

Once you've established a connection to the target of this section via RDP, visit the URL `https://127.0.0.1:8889/app/index.html#/search/all` and log in using the credentials: `admin/password`. After logging in, click on the circular symbol adjacent to `Client ID`. Subsequently, select the displayed `Client ID` and click on `Collected`.

Answer the questions below through Velociraptor collections that gather artifacts similar to the ones presented in this module.

Q1: Using VAD analysis, pinpoint the suspicious process and enter its name as your answer. Answer format: _.exe

A: reverse.exe

Reading this i got more familiar with VAD and Velociraptor (https://docs.velociraptor.app/artifact_references/pages/windows.system.vad/).

After i connected to the machine, i logged in to velociraptor GUI, then i ran the collection for Windows.System.VAD with .* for the regex and Execute, read and write for the protection.

Reading through the .json result i found this weird process.

![](../../Img/Pasted%20image%2020250826192253.png)


Q2: Determine the IP address of the C2 (Command and Control) server and enter it as your answer.

A: 3.19.219.4

I got it by resetting the machine and doing the collection of Windows.Network.Netstat 3 times each. I was tired so no screenshot for this one

Q3: Determine the registry key used for persistence and enter it as your answer.

A: HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run

From other modules i know that this is a common registry address for persistence. I just tried it and it worked lmao

Q4: Determine the folder that contains all Mimikatz-related files and enter the full path as your answer.

A:

Q5: Determine the Microsoft Word document that j0seph recently accessed and enter its name as your answer. Answer format: _.DOCX

A:
