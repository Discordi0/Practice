

## Hunting For Stuxbot (Round 2)

Recently uncovered details shed light on the operational strategy of Stuxbot's newest iteration.

1. The newest iterations of Stuxbot are exploiting the `C:\Users\Public` directory as a conduit for deploying supplementary utilities.
2. The newest iterations of Stuxbot are utilizing registry run keys as a mechanism to ensure their sustained presence within the infected system.
3. The newest iterations of Stuxbot are utilizing PowerShell Remoting for lateral movement within the network and to gain access to domain controllers.

---

## The Available Data

The cybersecurity strategy implemented is predicated on the utilization of the Elastic stack as a SIEM solution. Through the "Discover" functionality we can see logs from multiple sources. These sources include:

- `Windows audit logs` (categorized under the index pattern windows*)
- `System Monitor (Sysmon) logs` (also falling under the index pattern windows*, more about Sysmon [here](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon))
- `PowerShell logs` (indexed under windows* as well, more about PowerShell logs [here](https://www.splunk.com/en_us/blog/security/hunting-for-malicious-powershell-using-script-block-logging.html))
- `Zeek logs`, [a network security monitoring tool](https://www.elastic.co/guide/en/beats/filebeat/current/exported-fields-zeek.html) (classified under the index pattern zeek*)



`Hunt 1`: Create a KQL query to hunt for ["Lateral Tool Transfer"](https://attack.mitre.org/techniques/T1570/) to `C:\Users\Public`. Enter the content of the `user.name` field in the document that is related to a transferred tool that starts with "r" as your answer.

`Hunt 2`: Create a KQL query to hunt for ["Boot or Logon Autostart Execution: Registry Run Keys / Startup Folder"](https://attack.mitre.org/techniques/T1547/001/). Enter the content of the `registry.value` field in the document that is related to the first registry-based persistence action as your answer.

`Hunt 3`: Create a KQL query to hunt for ["PowerShell Remoting for Lateral Movement"](https://www.ired.team/offensive-security/lateral-movement/t1028-winrm-for-lateral-movement). Enter the content of the `winlog.user.name` field in the document that is related to PowerShell remoting-based lateral movement towards DC1.


## Questions


Q1: Enter your answer for Hunt 1.
A: svc-sql1

My process here was to try to find some "target" field that had `C:\Users\Public` in it as it was said in Hunt 1 that the tool was moved there. But i had no luck with that aproach.
Then i tried to just search for all file in that directory with file.path.

![](../../Img/Pasted%20image%2020250522192231.png)

Having no luck with that either, i searched for the text variant and i got it. (file.path.text:"C:\Users\Public*")

![](../../Img/Pasted%20image%2020250522192355.png)

Q2: Enter your answer for Hunt 2.
A: 

For this one i remembered that we have access to sysmon logs. so i google for the sysmos event id for registry. (https://learn.microsoft.com/es-mx/sysinternals/downloads/sysmon)

![](../../Img/Pasted%20image%2020250522193418.png)

With this i filtered for that ID and got 308 hits.

![](../../Img/Pasted%20image%2020250522193406.png)

Knowing that i have to look for some registry keys 

Enter your answer for Hunt 3.