# Azure SOC+SIEM Lab-Windows 10 Honeypot + Microsoft Sentinel

In this lab, I deployed a Windows 10 virtual machine inside Microsoft Azure, intentionally exposed it to the public internet, and used  Microsoft Sentinel to collect attack data in real-time. The VM acted as a honeypot, allowing me to observe real-world malicious activity and understand how SIEM monitoring can detect brute force attempts, port scans, and other threats targeting public systems.
The goal of this project was to simulate an exposed asset, implement a Security Information and Event Management (SIEM) solution, and practice the core functions of a Security Operations Center, including log analysis, incident investigation, and identifying critical hardening requirements.

## Lab Overview

| Component        | Role / Purpose |
|-----------------|---------|
|Azure Windows 10 VM   | Public-facing honeypot receiving real attack traffic | 
| Microsoft Sentinel     | SIEM platform used to analyze and visualize attacker activity |
|Log Analytics Workspace| Collected Windows security events and authentication logs  |
| Global Attack Map | Visualizes attacker IPs and country-of-origin using KQL |

## Lab Architecture
<img width="1000" height="500" alt="SIEM Lab Architecture" src="https://github.com/user-attachments/assets/e643a3b6-7b72-4304-b9d4-2ff033c08171" />

# What I Built:

I built a functional security monitoring environment utilizing Microsoft Azure services: <br/>

• Vulnerable Asset: Deployed a Windows 10 Virtual Machine and intentionally exposed it to the public internet to simulate a vulnerable host and attract automated attacks.<br/>
• Data Collection: Connected the VM to an Azure Log Analytics Workspace to facilitate log ingestion.<br/>
• Security Information and Event Management (SIEM): Enabled and configured Azure Sentinel to establish a functional SIEM system for centralized log analysis, detection, and incident investigation.<br/>
• Analytical Tools: Ran KQL queries to filter events, map attacker origins, and extract indicators of brute-force patterns.<br/>
• Visualization: Created a global attack heatmap to demonstrate how analysts quickly spot suspicious trends and abnormal spikes in activity.<br/>

# Steps Performed:

1. Created a Windows 10 virtual machine in Microsoft Azure and assigned it a public IP address so it could be accessed from the internet.

2. Modified the VM’s NSG to allow all inbound traffic from any source, intentionally exposing the system to simulate a publicly accessible endpoint.

3. Created a Log Analytics Workspace and connected the Windows 10 VM to it to begin collecting Windows security event logs.

4. Enabled Microsoft Sentinel on the Log Analytics Workspace to provide SIEM functionality and confirmed that security events were being ingested correctly.

5. With the VM exposed, I observed real-world brute-force attempts almost immediately, resulting in hundreds of security log events.

6. Used KQL to query failed login attempts and extract relevant details such as timestamps and attacker IP addresses.

7. Enriched the log data by mapping attacker IP addresses to geographic locations using Sentinel’s built-in geolocation features.

8. Created a Sentinel workbook that visualizes attack origins on a global map using KQL query results.

9. Analyzed attack patterns and documented the results using screenshots, queries, and visualizations for this lab.

# What I Learned 

This project provided hands-on experience in cloud security monitoring and a realistic look into how quickly exposed systems are attacked on the open internet. By intentionally exposing a Virtual Machine, I experienced firsthand how automated brute-force bots rapidly target vulnerable hosts. Connecting the VM to Log Analytics and enabling Sentinel helped me to better understand the workflow of how logs flow from cloud resources into a SIEM system and how a Security Operations Center leverages these tools to detect malicious activity, enrich logs, and investigate potential threats. 

This is my first practical encounter with data analysis involving running KQL queries. This experience taught me essential analytical techniques necessary for handling large volumes of log data. Specifically, I learned how to use KQL to effectively filter events and extract patterns from the logs. A major benefit of using these queries was the ability to rapidly map attacker origins and identify high-frequency indicators of brute-force behavior. This skill is crucial for understanding the nature of the attack and determining where threats are originating. Ultimately, the practice of running KQL queries was fundamental to strengthening my overall understanding of event analysis and incident investigation within the SIEM environment. Seeing these attacks appear live in Sentinel reinforced the importance of foundational security controls, including proper firewall configurations, patching, network segmentation, and credential hardening. Overall, this project strengthened my understanding of SIEM operations, event analysis, and incident investigation, highlighting how misconfigurations can expose an organization to unnecessary risk.

## SCREENSHOTS

Built VMs
<img width="1000" height="700" alt="Built VMs" src="https://github.com/user-attachments/assets/a078b7d6-8364-4242-9c21-594d6250a35d" />
Ping VM from home machine to check connectivity
<img width="1000" height="700" alt="Ping Vm" src="https://github.com/user-attachments/assets/9d2651d4-6e2e-474d-9459-12a9fee06db7" />
Changed firewall rules to allow all incoming traffic
<img width="1000" height="700" alt="Firewall Turn Off" src="https://github.com/user-attachments/assets/9fffdcbb-4336-4ebc-857e-d3cdd95f3c3b" />
Set up Sentinel and connected logs from windows security events 
<img width="1000" height="700" alt="Setting Up Sentinel" src="https://github.com/user-attachments/assets/73496974-7a4c-4ade-98a6-e531396d5717" />
Messing with the query window, short and expanded detail list
<img width="1000" height="700" alt="Log Query Short" src="https://github.com/user-attachments/assets/bd37122c-f4fb-470a-95e2-23de7036322b" />
<img width="1000" height="700" alt="Log Expand Long" src="https://github.com/user-attachments/assets/205a768b-0cd7-4d0a-a333-62a35ce7bcdc" />
1000 logon attempts in 1hr from the same IP, all 1 second apart from eachother meaning that a bot was used to autmatically brute force
<img width="1000" height="700" alt="KQL query on one IP" src="https://github.com/user-attachments/assets/2c3b5d29-fba4-4e7c-8c2b-31ae09140c03" />

KQL Query to create global attack map of logs generated 
<img width="1000" height="700" alt="KQL Create Map Query" src="https://github.com/user-attachments/assets/5fe46553-cd1b-4c64-9616-f0f999c92811" />
the map 
<img width="1000" height="700" alt="Attack Map" src="https://github.com/user-attachments/assets/2f226d81-45a2-40cb-92db-ee80fef33111" />
















