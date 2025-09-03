
# Skills Assessment

This module's skills assessment involves identifying malicious activity using Splunk and Zeek logs.

In many instances, the solution can be discovered by simply viewing the events in each index, as the number of events is limited. However, please take the time to refine your Splunk searches to achieve a better understanding.

Q1: Use the "empire" index and the "bro:http:json" sourcetype. Identify beaconing activity by modifying the Splunk search of the "Detecting Beaconing Malware" section and enter the value of the "TimeInterval" field as your answer.

A: 4.680851063829787

The Splunk query given in the "Detecting Beaconing Malware" section of this course is this: 


```shell-session
index="cobaltstrike_beacon" sourcetype="bro:http:json" 
| sort 0 _time
| streamstats current=f last(_time) as prevtime by src, dest, dest_port
| eval timedelta = _time - prevtime
| eventstats avg(timedelta) as avg, count as total by src, dest, dest_port
| eval upper=avg*1.1
| eval lower=avg*0.9
| where timedelta > lower AND timedelta < upper
| stats count, values(avg) as TimeInterval by src, dest, dest_port, total
| eval prcnt = (count/total)*100
| where prcnt > 90 AND total > 10
```

Changing the index and deleting the last 2 lines we can see the answer. 

```shell-session
index="empire" sourcetype="bro:http:json" 
| sort 0 _time
| streamstats current=f last(_time) as prevtime by src, dest, dest_port
| eval timedelta = _time - prevtime
| eventstats avg(timedelta) as avg, count as total by src, dest, dest_port
| eval upper=avg*1.1
| eval lower=avg*0.9
| where timedelta > lower AND timedelta < upper
| stats count, values(avg) as TimeInterval by src, dest, dest_port, total
```


![](../../Img/Pasted%20image%2020250903143536.png)

Q2: Use the "printnightmare" index and the "bro:dce_rpc:json" sourcetype to create a Splunk search that will detect possible exploitation of the PrintNightmare vulnerability. Enter the IP included in the "id.orig_h" field as your answer.

A: 192.168.1.149

Using the index and sourcetype given we get just 5 events.

![](../../Img/Pasted%20image%2020250903143700.png)

Adding the filter to get the ip's.

![](../../Img/Pasted%20image%2020250903143846.png)



Q3: Use the "bloodhound_all_no_kerberos_sign" index and the "bro:dce_rpc:json" sourcetype to create a Splunk search that will detect possible BloodHound activity (https://www.lares.com/blog/active-directory-ad-attacks-enumeration-at-the-network-layer/). Enter the IP included in the "id.orig_h" field as your answer.

A: 192.168.109.105

Again with just the provided info.

![](../../Img/Pasted%20image%2020250903144050.png)

With just the filter to see the ip's.

![](../../Img/Pasted%20image%2020250903144216.png)
