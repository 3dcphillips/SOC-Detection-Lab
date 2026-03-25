# SOC Detection Lab

<p align="center">
  <img src="https://img.shields.io/badge/SIEM-Splunk-blue?style=for-the-badge&logo=splunk" />
  <img src="https://img.shields.io/badge/Telemetry-Sysmon-orange?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Attack%20Simulation-Atomic%20Red%20Team-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Focus-SOC%20Detection-success?style=for-the-badge" />
</p>

---

## Overview

The **SOC Detection Lab** is a hands-on security monitoring project built to simulate the workflow of a Tier 1 SOC Analyst. Using **Splunk**, **Sysmon**, **Windows Security logs**, and **Atomic Red Team**, I created a centralized detection lab to ingest telemetry, simulate attacker behavior, build detections, and investigate suspicious activity through a custom SOC dashboard.

This project demonstrates practical experience with:
- Log ingestion and normalization
- Detection engineering
- Alert validation
- Threat investigation
- SOC-style dashboard development

---

## Objective

The goal of this lab was to build a working security monitoring environment that could detect and visualize attacker-like behavior using real endpoint and Windows event telemetry.

Key objectives included:
- Ingesting Sysmon and Windows Security logs into Splunk
- Simulating suspicious activity with Atomic Red Team
- Building detections for common SOC use cases
- Validating telemetry and detections through dashboard panels
- Practicing alert triage and investigation workflows

---

## Lab Architecture

- **SIEM:** Splunk Enterprise
- **Endpoint Telemetry:** Sysmon
- **Windows Logging:** Windows Security Event Logs
- **Log Forwarding:** Splunk Universal Forwarder
- **Attack Simulation:** Atomic Red Team
- **Network Visibility:** Wireshark
- **Virtualization:** VirtualBox / VMware

---

## Skills Demonstrated

- SIEM log ingestion, parsing, and analysis
- Sysmon and Windows event log monitoring
- Splunk search development and dashboard creation
- Detection engineering for suspicious endpoint activity
- Windows authentication event analysis
- MITRE ATT&CK mapping
- Alert validation and investigation
- Security-focused troubleshooting and lab tuning

---

## Dashboard Detection Use Cases

### 1. Suspicious PowerShell Execution
Detects high-risk PowerShell behavior associated with encoded commands, in-memory execution, remote script retrieval, and offensive tooling.

- **Data Source:** Sysmon Event ID 1
- **Examples:** `IEX`, `DownloadString`, `-enc`, `Invoke-Mimikatz`, `SharpHound`
- **MITRE ATT&CK:** `T1059.001 – PowerShell`

### 2. Excessive Failed Logons / Brute Force Activity
Identifies repeated failed authentication attempts that may indicate brute force or password spraying behavior.

- **Data Source:** Windows Security Log
- **Event ID:** 4625
- **MITRE ATT&CK:** `T1110 – Brute Force`

### 3. Successful Logon After Multiple Failures
Highlights a suspicious authentication pattern where repeated failed logons are followed by a successful login.

- **Data Source:** Windows Security Log
- **Event IDs:** 4624, 4625
- **MITRE ATT&CK:** `T1110 – Brute Force`

### 4. Suspicious Process Execution
Surfaces commonly abused Windows binaries and script execution tools often associated with attacker tradecraft.

- **Data Source:** Sysmon Event ID 1
- **Examples:** `cmd.exe`, `powershell.exe`, `wscript.exe`, `cscript.exe`, `rundll32.exe`, `regsvr32.exe`, `mshta.exe`
- **MITRE ATT&CK:** `T1059`, `T1218`

### 5. Suspicious Outbound Connections
Flags network connections initiated by user-driven processes and script interpreters that may indicate command-and-control or external payload retrieval.

- **Data Source:** Sysmon Event ID 3
- **MITRE ATT&CK:** `T1071 – Application Layer Protocol`

### 6. Suspicious File Creation in Sensitive Paths
Detects file creation in locations commonly associated with staging, persistence, or payload delivery.

- **Data Source:** Sysmon Event ID 11
- **Examples:** Temp, AppData, Startup, Public folders
- **MITRE ATT&CK:** `T1105 – Ingress Tool Transfer`

---

## Example Splunk Detection

### Suspicious PowerShell Execution
```spl
index=* EventCode=1 Image="*\\powershell.exe"
(CommandLine="*IEX*" OR CommandLine="*DownloadString*" OR CommandLine="*-enc*" OR CommandLine="*Invoke-Mimikatz*" OR CommandLine="*SharpHound*")
| table _time host User ParentImage Image CommandLine
| sort -_time
```
---

### Validation & Testing

To validate detections, I simulated attack activity and suspicious behaviors in the lab environment using Atomic Red Team and manual authentication testing.

### Validation included:

Running PowerShell-based atomic tests
Confirming Sysmon process creation events in Splunk
Testing failed and successful logon patterns
Reviewing command-line, process, network, and file creation telemetry
Verifying dashboard visibility and SOC-style investigation context
Dashboard

### Dashboard
The dashboard was designed to provide a SOC-style view of endpoint and authentication activity, with panels for:

-Detection activity over time
-Suspicious PowerShell execution
-Failed logons / brute force attempts
-Successful logons after repeated failures
-Suspicious process creation
-Unusual outbound connections
-Suspicious file creation
