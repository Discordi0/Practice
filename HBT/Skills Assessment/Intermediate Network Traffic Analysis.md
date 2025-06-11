

As a Security Operations Center (SOC) analyst, you were recently provided with two PCAP (Packet Capture) files named `funky_dns.pcap` and `funky_icmp.pcap`.

Inspect the `funky_dns.pcap` and `funky_icmp.pcap` files, part of this module's resources, to identify if there are certain patterns and behaviors within these captures that deviate from what is typically observed in routine network traffic. Then, answer the questions below.


Q1: Inspect the funky_dns.pcap file, part of this module's resources, and enter the related attack as your answer. Answer format: "DNS Flooding", "DNS Amplification", "DNS Tunneling"

A:

Opening the pcap file we can find 438 packets.

![](../../Img/Pasted%20image%2020250611153310.png)

Filtering for only DNS traffic reduces that to 434.

![](../../Img/Pasted%20image%2020250611153352.png)

Looking at the statistics we can see that all the traffic is a conversation between

Q2: Inspect the funky_icmp.pcap file, part of this module's resources, and enter the related attack as your answer. Answer format: "ICMP Flooding", "ICMP Tunneling", "ICMP SMURF Attack"

A: 

