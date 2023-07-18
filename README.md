<h1>Crowdstrike_Falcon_Investigation_PJ</h1>
Objective: To display my ability to investigate an alert in Crowdstrike Falcon within an environment.
<p align="center">
Crowdstrkie Falcon Alert: <br/>
<img src="https://imgur.com/s1z5fcc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p align="center">
Crowdstrkie Falcon Alert: <br/>
<img src="https://imgur.com/1ZESFPB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />  

<h2>Detection Details(s)</h2>
Description: A process has written a suspicious file to disk. Adversaries may write a malicious file to a commonly trusted directory, use a benign name, or a mismatched file extension. This is done for the sake of evading defenses and observation. 

<br>Check the activity and surrounding events are expected in your environment. Detection is based on a high degree of entropy, packing, anti-malware evasion, or other similarity to known malware. A file written to the file system meets the on-sensor machine learning high confidence threshold for malicious files. 
<br>Customer ID: xxx82exxxxa4bxxxxxxxxxxxxx123
<br>Host name: CROWDSTRIKE
<br>File name: explorer.exe
<br>File path: \Device\HarddiskVolumeX\Windows\explorer.exe
<br>Command line: C:\WINDOWS\Explorer.EXE
<br>SHA 256: b6f176e86ded71b8494fad53791367c870318b1e7d9c3e1aee1b0dac6cfac237
<br>MD5 Hash data: 790e65f13eceb64fe297df08eb1c953a
<br>Full detection details: https://falcon.us-2.crowdstrike.com/activity/detections/detail/xxxxxxxxxxxxxx
<br>Platform: Windows
<br>IP address: Host IP address
<br>User name: crowdstrike
<br>Detected: 07-08-2023 11:02:58 local time, (2023-07-08 15:02:58 UTC)
<br>Last behavior: 07-08-2023 11:02:58 local time, (2023-07-08 15:02:58 UTC)

<h2>VirusTotal Hash Value Reputation Check</h2>
VirusTotal Risk Score: 60/71 vendors flagged the IP address as malicious.
<p align="center">
VirusTotal <br/>
<img src="https://imgur.com/JzFJH7k.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h2>Hybrid Analysis Sandbox</h2>
Risk score: 100/100
<p align="center">
Hybrid Analysis Sandbox <br/>
<img src="https://imgur.com/tklaIRh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />  

<h2>Executive Summary</h2>
Crowdstrike Falcon labeled the alert as Suspicious File Written.  The alert was detected on 07-08-2023 11:02:58.  

Based on OSINT research, a malicious zip file was downloaded from a website.  I did a host search to find the URL where the zip file was downloaded and was unable to find it.  Based on our SOP, I would escalate this to our SOC manager for the root cause analysis.  

The user unzipped the file and executed mimikatz.exe.  Crowdstrike policy was set on detect, so the file was not quarantined.  Mimikatz.exe steals passwords on Windows machines, so this is a critical situation.  

The steps I did take to mitigate the malicious activity are:
- I disconnected the endpoint from the network.  
- I have permission to connect to the host to locate the zip file and remove it.  I followed our playbook to remove the zip file (Temp1_mimikatz-master.zip).
- I ran an AV scan on the endpoint to make sure I removed all of the malicious activity from the endpoint.

<br />

<h2>Declaration</h2>
The detection is a true positive because mimikatz.exe was successfully executed.

<h2>Recommendation(s)</h2>
I recommended help desk reset the user’s password.
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
