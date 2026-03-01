# Honeypot Azure Lab – Security Detection Project

## Project Overview

This project demonstrates a honeypot deployed on an Azure Windows VM to attract and detect attacker activity. Security logs from the honeypot are forwarded to Microsoft Sentinel for analysis and visualization. The lab simulates SOC-level monitoring and provides hands-on experience with cloud-based threat detection.



## Objectives

- Deploy a vulnerable Windows VM as a honeypot
- Forward logs to Microsoft Sentinel using Azure Monitoring Agent
- Detect and visualize attacker activity globally
- Perform basic alert triage and analysis
- Understand attacker behavior patterns in a controlled lab environment



## Lab Setup

- **Azure Resources:**
  - Resource Group
  - Virtual Network
  - Network Security Group (NSG)
  - Windows VM configured with intentional vulnerabilities
- **Log Forwarding:** Configured via Azure Monitoring Agent to Microsoft Sentinel
- **Enrichment:** Watchlists used to enrich logs
- **Visualization:** KQL queries used to generate maps and charts of attacker activity



## Detection Logic

Example KQL query used in Sentinel:

```kql
SecurityEvent
| where EventID == 4625
| summarize FailedAttempts = count() by Account, Computer, bin(TimeGenerated, 5m)
| where FailedAttempts >= 3
