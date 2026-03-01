# Honeypot Configuration Notes – Azure Lab

## Lab Architecture & Setup

This document details the architecture, Azure resources, and configuration steps for the honeypot lab.

### Azure Resources

- **Resource Group:** Dedicated group for the lab environment  
- **Virtual Network:** Isolated network for honeypot VM  
- **Windows VM:** Configured intentionally vulnerable for observation and research  
- **Network Security Group (NSG):** Opened multiple ports to simulate exposed services  
- **Host Firewall:** Adjusted to allow external access for testing attacker activity  

### Central Logging

- **Log Analytics Workspace:** Central repository for all security logs  
- **Azure Monitoring Agent:** Installed on the VM to forward logs to Log Analytics  

### Microsoft Sentinel

- **Sentinel Instance:** Connected to the Log Analytics workspace for monitoring and alerting  


### Watchlist Enrichment

- Uploaded a **spreadsheet watchlist** containing IP blocks and geographic metadata  
- Logs are enriched with watchlist data to provide geo-location information for attacker IPs  

### Hunting & Visualization

- **KQL Queries:** Used to detect failed logons and suspicious activity  
- **Data Enrichment:** Joined query results with the watchlist for attacker geo-location  
- **Visualization:** Created a map workbook in Sentinel to display attacker locations globally  



## Lab Notes

- VM is intentionally vulnerable for **educational and research purposes**  
- Alerts were **tested and validated** using simulated attack attempts  
- Demonstrates hands-on SOC skills:
  - Log collection and forwarding  
  - Watchlist enrichment  
  - Threat detection  
  - Visualization and alerting
