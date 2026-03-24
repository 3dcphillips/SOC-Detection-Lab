# SOC Detection Lab

<p align="center">
  <img src="https://img.shields.io/badge/SIEM-Splunk-blue?style=for-the-badge&logo=splunk" />
  <img src="https://img.shields.io/badge/Telemetry-Sysmon-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Attack%20Simulation-Atomic%20Red%20Team-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Focus-SOC%20Detection-success?style=for-the-badge" />
</p>

---

## Objective

The **SOC Detection Lab** simulates a real-world Security Operations Center (SOC) by building a centralized logging and detection platform using Splunk.

The lab focuses on:
- Ingesting Windows and Sysmon logs
- Generating realistic attack telemetry
- Developing detection rules for suspicious activity
- Investigating alerts like a Tier 1 SOC Analyst

---

## Skills Demonstrated

- SIEM log ingestion, parsing, and analysis  
- Threat detection and alert engineering  
- Windows Event Log & Sysmon analysis  
- Detection of:
  - Brute force attacks
  - PowerShell abuse
  - Suspicious file creation
  - Network anomalies  
- MITRE ATT&CK mapping  
- Incident triage and investigation workflows  
- Security-focused troubleshooting  

---

## Tools & Technologies

| Category | Tools |
|--------|------|
| SIEM | Splunk Enterprise |
| Endpoint Telemetry | Sysmon |
| Log Forwarding | Splunk Universal Forwarder |
| Attack Simulation | Atomic Red Team |
| Network Analysis | Wireshark |
| Virtualization | VirtualBox / VMware |

---

## Detection Use Cases

### Brute Force Detection
- Detects multiple failed login attempts in a short timeframe  
- Identifies credential attack patterns  
- **MITRE ATT&CK:** T1110  

---

### Suspicious PowerShell Execution
- Detects encoded and obfuscated commands  
- Identifies abnormal execution patterns  
- **MITRE ATT&CK:** T1059.001  

---

### Unusual Network Connections
- Flags suspicious outbound connections  
- Detects potential C2 communication  
- **MITRE ATT&CK:** T1071  

---

### Suspicious File Creation
- Uses Sysmon Event ID 11  
- Detects file drops via PowerShell/CMD  
- Identifies potential malware staging  
- **MITRE ATT&CK:** T1105  

---
## Example Splunk Detection

```spl
index=* EventCode=11 
(Image="*powershell.exe" OR Image="*cmd.exe")
| stats count by Image, TargetFilename
```

##Splunk Dashboard
<img width="1270" height="1336" alt="image" src="https://github.com/user-attachments/assets/037929d3-a842-4064-93f8-c426a090a989" />



