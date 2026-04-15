Threat Hunting Case: Suspected Ransomware & DCSync Attack

Overview

This project documents a threat hunting investigation involving suspicious PowerShell execution, system reconnaissance, and abnormal Active Directory replication activity.

The goal was to identify potential attacker behavior using both host-based logs and network traffic analysis.


---

Scenario

A user downloaded a suspicious tool, which led to potential compromise. Investigation was conducted using:

Event Viewer logs

Network packet capture (Wireshark)



---

Host Analysis

Evidence of suspicious script execution using:

PowerShell

Execution flag: ExecutionPolicy Bypass


Observed Behavior:

System log enumeration

Driver and hardware inspection

Virtual environment detection (Xen drivers)


This indicates:

environment reconnaissance



---

 Network Analysis

Wireshark revealed:

RPC communication over port 135

Use of DRSUAPI

NTLM authentication using admin credentials


Suspicious Activity:

Active Directory replication requests from a non-domain controller


This strongly suggests:

DCSync attack



---

 Indicators of Compromise (IOCs)

PowerShell script: superimportant-updated.ps1

Execution with ExecutionPolicy Bypass

Internal communication: 10.0.0.20 → 10.0.0.10

Admin account usage: LAB\admin

Suspicious binary: mimikatz.exe

Hashes extracted from infected computer



---

 Attack Chain

1. User downloads malicious tool


2. PowerShell script executed with bypass


3. System reconnaissance performed


4. Credential harvesting via DCSync technique




---

Impact

Potential credential compromise

Risk of full domain takeover

Possible ransomware deployment



---

Recommendations

Isolate affected system

Reset all privileged credentials

Audit Domain Controller activity

Enable advanced logging (PowerShell & process creation)

Perform full malware scan



---

 Skills Demonstrated

Log analysis (Event Viewer)

Network analysis (Wireshark)

Threat detection & correlation

Understanding of Active Directory attacks

Incident reporting


Author
Christopher Tayo


