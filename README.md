# SOC-Detection-Lab

## Objective
The SOC Detection Lab project was designed to simulate a real-world Security Operations Center (SOC) environment by building a centralized logging and detection platform using a SIEM. The lab focuses on ingesting Windows and Sysmon logs, generating realistic attack telemetry, and developing custom detection rules to identify suspicious activity.

This project demonstrates hands-on experience with threat detection, alert validation, and incident investigation—mirroring the workflow of a Tier 1 SOC Analyst.

### Skills Learned
-SIEM log ingestion, normalization, and analysis
-Threat detection and alert development
-Windows Event Log and Sysmon analysis
-Identification of attack patterns (brute force, PowerShell abuse, network anomalies)
-MITRE ATT&CK mapping and adversary behavior understanding
-Incident investigation and alert triage workflows
-Security-focused troubleshooting and analytical thinking

### Tools Used
SIEM Platform: Splunk
Endpoint Telemetry: Sysmon
Log Forwarding: Splunk Universal Forwarder
Attack Simulation: Atomic Red Team
Network Analysis: Wireshark
Virtualization: VirtualBox / VMware

Detection Use Cases
1. Brute Force Login Detection
Identifies multiple failed login attempts within a short timeframe
Detects potential credential attacks

2. Suspicious PowerShell Execution
Detects encoded or obfuscated PowerShell commands
Identifies unusual parent-child process relationships

3. Unusual Network Connections
Flags outbound connections from suspicious processes
Helps identify potential command-and-control activity

## Steps
*Project Steps Go Here*


## Screenshots
Screenshots
Ref 1: Network Diagram

(architecture diagram here)

Ref 2: SIEM Dashboard

(Splunk dashboard screenshot)

Ref 3: Detection in Action

(alert/query results screenshot)

## MITRE ATT&CK Mapping

| Technique | Description                                    |
| --------- | ---------------------------------------------- |
| T1110     | Brute Force                                    |
| T1059     | Command and Scripting Interpreter (PowerShell) |
| T1071     | Application Layer Protocol (C2 Traffic)        |
