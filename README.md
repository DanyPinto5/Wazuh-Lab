### Wazuh-Lab
### Wazuh Detection Lab – Active Directory Environment
Practical SIEM lab built using Wazuh to simulate real-world SOC monitoring in an Active Directory environment.

### Why I Built This Lab
After studying security monitoring and detection engineering, I wanted to apply these concepts in a realistic environment instead of only theoretical learning.

### Wazuh Detection Lab – Active Directory Environment
Practical SIEM lab built using Wazuh to simulate real-world SOC monitoring in an Active Directory environment.

### Why I Built This Lab
After studying security monitoring and detection engineering, I wanted to apply these concepts in a realistic environment instead of only theoretical learning.

### This lab demonstrates my ability to:
Deploy and configure a SIEM (Wazuh)
Collect and analyze Windows Security logs
Simulate attacker behavior
Create custom detection rules
Investigate alerts using a SOC investigation workflow

### Lab Environment
The lab environment includes:
Windows Server (Domain Controller)
Windows 10 (Domain-joined endpoint)
Wazuh OVA (Manager + OpenSearch + Dashboard)
Agents communicate internally using TLS on port 1514.
PowerShell Script Block Logging was enabled to provide deeper visibility into PowerShell activity.

### Lab Architecture
The diagram below shows the architecture of the lab environment and how security events are collected and processed by Wazuh.

![Lab Architecture](/Screenshots/Agents/01_lab_architecture.png)

### Simulated Security Events
The following Windows Security events were generated and analyzed during the lab:
4720 – User account creation (possible persistence)
4728 – User added to Domain Admins (privilege escalation)
4625 – Failed authentication attempts (brute force pattern)
4104 – PowerShell execution (Process Discovery – MITRE T1057)
These events help simulate different stages of a potential attack within an Active Directory environment.

### Custom Detection – Brute Force (Rule ID 110200)
A custom Wazuh correlation rule was created to detect brute force attempts.
Detection logic:
5 failed logons (Event ID 4625)
Occurring within 60 seconds
Severity level 10
Mapped to MITRE ATT&CK – T1110 (Brute Force).
This detection allows early identification of suspicious authentication activity, before an attacker successfully logs in.

### Investigation Approach
For each alert generated in Wazuh, the following investigation process was used:
Identify the actor (subject)
Identify the affected account or group
Assess potential risk and impact
Correlate related events
Validate legitimacy of the activity
Recommend containment or mitigation if necessary

### Evidence
Screenshots from the lab environment are available in the screenshots directory and include:
Wazuh agents connected to the manager
Windows Event Viewer logs
Wazuh alerts generated from simulated activity
Evidence of the brute force detection rule in action

### Custom Rules
Custom Wazuh detection rules used in this lab are available in the rules directory.

### Next Steps
Expand detection coverage for additional security events
Improve alert tuning to reduce false positives
Test Wazuh active response capabilities
