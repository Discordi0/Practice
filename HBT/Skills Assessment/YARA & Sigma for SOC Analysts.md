In this skills assessment section, we'll practice YARA rule development and using Sigma rules to hunt for threats within event logs.

For the initial question, you'll be tasked with developing a YARA rule aimed at identifying the malicious `Seatbelt.exe` file, commonly used by attackers for maintaining operational security.

In the subsequent question, you'll be using a Sigma rule to identify instances of shadow volume deletion - a technique often utilized by ransomware groups.


Q1: The "C:\Rules\yara\seatbelt.yar" YARA rule aims to detect instances of the "Seatbelt.exe" .NET assembly on disk. Analyze both "C:\Rules\yara\seatbelt.yar" and "C:\Samples\YARASigma\Seatbelt.exe" and specify the appropriate string inside the "$class2" variable so that the rule successfully identifies "C:\Samples\YARASigma\Seatbelt.exe". Answer format: L________r

A: LsaWrapper

RDP'ing into the machine, we search for the rule in question.

![](../../Img/Pasted%20image%2020250731155310.png)

$class2 is empty so there's nothing to go from there.
In it's git page i didn't found anything at a quick glance (https://github.com/GhostPack/Seatbelt)
i opened the sample in dnSpy, looking through it for a little while i found this.

![](../../Img/Pasted%20image%2020250731161026.png)

This is what i found in google.

![](../../Img/Pasted%20image%2020250731161522.png)

It seems to be that this is what am looking for.



Q2: Use Chainsaw with the "C:\Tools\chainsaw\sigma\rules\windows\powershell\powershell_script\posh_ps_susp_win32_shadowcopy.yml" Sigma rule to hunt for shadow volume deletion inside "C:\Events\YARASigma\lab_events_6.evtx". Enter the identified ScriptBlock ID as your answer.

A: faaeba08-01f0-4a32-ba48-bd65b24afd28

With the path of the required files and the tools from the previous modules, we craft the query.

.\chainsaw_x86_64-pc-windows-msvc.exe hunt C:\Events\YARASigma\lab_events_6.evtx -s C:\Tools\chainsaw\sigma\rules\windows\powershell\powershell_script\posh_ps_susp_win32_shadowcopy.yml --mapping .\mappings\sigma-event-logs-all.yml

![](../../Img/Pasted%20image%2020250731162420.png)

