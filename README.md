# Home-SOC-SIEM
In this lab, I deployed a Windows 10 virtual machine inside Microsoft Azure, intentionally exposed it to the public internet, and used Microsoft Sentinel to collect attack data in real-time. The VM acted as a honeypot, allowing me to observe real-world malicious activity and understand how SIEM monitoring can detect brute force attempts, port scans, and other threats targeting public systems.
The goal of this project was to gain hands-on experience configuring Azure resources, enabling logging, forwarding security events, and building visual analytics inside Sentinel.

## Lab Overview

| Component        | Role / Purpose |
|-----------------|---------|
| Microsoft Azure    | Hypervisor / virtualization platform | 
|Azure Windows 10 VM   | Public-facing honeypot receiving real attack traffic | 
| Microsoft Sentinel     | SIEM platform used to analyze and visualize attacker activity |
|Log Analytics Workspace| Collected Windows security events and authentication logs  |
| Organizational Units (OUs) & Groups | Simulate department based user organization |

## Lab Architecture
<img width="1000" height="500" alt="SIEM Lab Architecture" src="https://github.com/user-attachments/assets/e643a3b6-7b72-4304-b9d4-2ff033c08171" />

# What I Built:

In Microsoft Azure, I set up:
AZ-VM01 – Windows 10 Virtual Machine
Exposed to the public internet
Allowed inbound RDP traffic
Used as a basic honeypot for real-world attacks
Azure Network + Firewall Configuration
Modified NSG rules to allow external connections
Confirmed the VM was reachable publicly
Observed immediate brute-force attempts
Log Analytics Workspace
Connected VM security logs
Enabled ingestion of Windows event data
Microsoft Sentinel
Activated SIEM capabilities
Built an attack map using KQL
Analyzed failed login attempts and attacker locations
