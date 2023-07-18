<h1>Crowdstrike_Falcon_Investigation_PJ</h1>
Objective: To display my ability to investigate an alert in Crowdstrike Falcon within an environment.
<p align="center">
Crowdstrkie Falcon Alert: <br/>
<img src="https://imgur.com/oZHPL3H.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p align="center">
Crowdstrkie Falcon Alert: <br/>
<img src="https://imgur.com/rdLVB25.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />  
<h2>Executive Summary</h2>
The detection occurred on July 18, 2023 at 9:08 AM.  Splunk labeled the detection as Remote Desktop Network Bruteforce.  The rule that was triggered states this search looks for RDP application network traffic and filters any source/destination pair generating more than twice the standard of the average traffic.  Through the investigation, it was determined the source IP address is malicious.  I queried Splunk to check for previous activity to make sure the attacker was not successful in logging into an endpoint in the environment.  The query displayed a table of the activity and revealed the firewall blocked the attacker from entering the environment.

<br />


<h2>IP(s)</h2>
The source IP is 80.xx.88.2xx and the destination IP is the company’s public IP address.  A threat actor is attempting to brute force the network through RDP.


<h2>Ports </h2>

<b>RDP 3389</b>

<h2>VirusTotal IP Reputation Check</h2>
VirusTotal Risk Score: 13/88 vendors flagged the IP address as malicious.
<p align="center">
VirusTotal <br/>
<img src="https://imgur.com/RswIxfj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h2>abuseIPDB IP Reputation Check</h2>
abuseIPDB risk score: the confidence of abuse is 100%
<p align="center">
abuseIPDB <br/>
<img src="https://imgur.com/kU9Mtam.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />  

In the abuseIPDB reports, people labeled the source IP address as Bruteforce attack RDP server and port scanning. 
<h2>Declaration</h2>
The investigation lead to conclude this detection is a true positive non-issue or it is benign because the firewall blocked the traffic.  There is not recommendation at this time.
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
