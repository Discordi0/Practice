
## Intrusion Detection With Zeek: Detecting Gootkit's SSL Certificate

**PCAP source**: [https://www.malware-traffic-analysis.net/2016/07/08/index.html](https://web.archive.org/web/20230128061716/https://www.malware-traffic-analysis.net/2016/07/08/index.html)

**Attack description and possible detection points**: [https://www.malware-traffic-analysis.net/2016/07/08/index.html](https://web.archive.org/web/20230128061716/https://www.malware-traffic-analysis.net/2016/07/08/index.html) <-- Focus on the SSL certificate parts.

`Neutrino`, a notorious exploit kit, and `Gootkit`, a potent banking trojan, collaborated in the past to perpetrate cyberattacks.

The `Neutrino` exploit kit opened the gate, and then `Gootkit` begun to communicate over the network using SSL/TLS encryption. It's within these encrypted communications that we encountered a particularly striking detail - the SSL certificates used by `Gootkit` contained the Common Name (`CN`) "`My Company Ltd.`".

Cybercriminals frequently employ self-signed or non-trusted CA issued certificates to foster encrypted communication. These certificates often feature bogus or generic details. In this case, the common name `My Company Ltd.` stands out as an anomaly we can use to identify this specific `Gootkit` infection delivered via the `Neutrino` exploit kit.

---

Review the previously referenced resource that discusses the network traces resulting from `Gootkit` communications, and then proceed to address the following question.


Q: There is a file named neutrinogootkit.pcap in the /home/htb-student/pcaps directory, which contains network traffic related to the Neutrino exploit kit sending Gootkit malware. Enter the x509.log field name that includes the "MyCompany Ltd." trace as your answer.

A: certificate.subject

In this question, we don't need to modify a rule, we just need to search for a field.
So, connect with SSH to the machine and use zeek in the pcap file.

![](../../Img/Pasted%20image%2020250615153022.png)

Even though it doesn't have any real format, we can see that the "MyCompany Ltd." it's in the 5th (column?) as it's separated by spaces, and after the #fields (that doesn't count bc of the #) the 5th is certificate subject. (in other cases there could be necessary to format the output of the command to be able to read the answer).