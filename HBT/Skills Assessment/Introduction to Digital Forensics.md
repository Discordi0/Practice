
Upon identifying signs of data exfiltration from an unusual process on a system, the SOC manager tasked you with conducting a forensic investigation through `Velociraptor`.

Once you've established a connection to the target of this section via RDP, visit the URL `https://127.0.0.1:8889/app/index.html#/search/all` and log in using the credentials: `admin/password`. After logging in, click on the circular symbol adjacent to `Client ID`. Subsequently, select the displayed `Client ID` and click on `Collected`.

Answer the questions below through Velociraptor collections that gather artifacts similar to the ones presented in this module.

Q1: Using VAD analysis, pinpoint the suspicious process and enter its name as your answer. Answer format: _.exe

A:

Reading this i got more familiar with VAD and Velociraptor (https://docs.velociraptor.app/artifact_references/pages/windows.system.vad/).

In the provided system i couldn't find the volatility tool, but i did find Velociraptor (C:\Users\Administrator\Velociraptor).





Q2: Determine the IP address of the C2 (Command and Control) server and enter it as your answer.

A:

Q3: Determine the registry key used for persistence and enter it as your answer.

A:

Q4: Determine the folder that contains all Mimikatz-related files and enter the full path as your answer.

A:

Q5: Determine the Microsoft Word document that j0seph recently accessed and enter its name as your answer. Answer format: _.DOCX

A:
