Threat Hunting Case: Suspected Ransomware & DCSync Attack

  Overview

This project documents a threat hunting investigation involving suspicious PowerShell execution, system reconnaissance, and abnormal Active Directory replication activity.

The goal was to identify potential attacker behavior using both host-based logs and network traffic analysis.


---

  Scenario

A user downloaded a suspicious tool, which led to potential compromise. Investigation was conducted using:

1. Event Viewer logs

2. Network packet capture (Wireshark)



---

  Host Analysis

Evidence of suspicious script execution using:

1. PowerShell

2. Execution flag: ExecutionPolicy Bypass


Observed Behavior

1. System log enumeration

2. Driver and hardware inspection

3. Virtual environment detection (Xen drivers)


This indicates:

environment reconnaissance



---

  Network Analysis

Wireshark revealed:

1. RPC communication over port 135

2. Use of DRSUAPI

3. NTLM authentication using admin credentials


Suspicious Activity:

Active Directory replication requests from a non-domain controller


This strongly suggests:

DCSync attack



---

   Indicators of Compromise (IOCs)

1. PowerShell script: superimportant-updated.ps1

2. Execution with ExecutionPolicy Bypass

3. Internal communication: 10.0.0.20 → 10.0.0.10

4. Admin account usage: LAB\admin

5. Suspicious binary: mimikatz.exe

6. Hashes extracted from infected computer



---

   Attack Chain

1. User downloads malicious tool


2. PowerShell script executed with bypass


3. System reconnaissance performed


4. Credential harvesting via DCSync technique




---

Impact

1. Potential credential compromise

2. Risk of full domain takeover

3. Possible ransomware deployment



---

Recommendations

1. Isolate affected system

2. Reset all privileged credentials

3. Audit Domain Controller activity

4. Enable advanced logging (PowerShell & process creation)

5. Perform full malware scan



---

 Skills Demonstrated

1. Log analysis (Event Viewer)

2. Network analysis (Wireshark)

3. Threat detection & correlation

4. Understanding of Active Directory attacks

5. Incident reporting












Author
Christopher Tayo


