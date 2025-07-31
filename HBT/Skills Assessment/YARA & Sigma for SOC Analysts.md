In this skills assessment section, we'll practice YARA rule development and using Sigma rules to hunt for threats within event logs.

For the initial question, you'll be tasked with developing a YARA rule aimed at identifying the malicious `Seatbelt.exe` file, commonly used by attackers for maintaining operational security.

In the subsequent question, you'll be using a Sigma rule to identify instances of shadow volume deletion - a technique often utilized by ransomware groups.


Q1: The "C:\Rules\yara\seatbelt.yar" YARA rule aims to detect instances of the "Seatbelt.exe" .NET assembly on disk. Analyze both "C:\Rules\yara\seatbelt.yar" and "C:\Samples\YARASigma\Seatbelt.exe" and specify the appropriate string inside the "$class2" variable so that the rule successfully identifies "C:\Samples\YARASigma\Seatbelt.exe". Answer format: L________r

A: 

Q2: Use Chainsaw with the "C:\Tools\chainsaw\sigma\rules\windows\powershell\powershell_script\posh_ps_susp_win32_shadowcopy.yml" Sigma rule to hunt for shadow volume deletion inside "C:\Events\YARASigma\lab_events_6.evtx". Enter the identified ScriptBlock ID as your answer.

A: 