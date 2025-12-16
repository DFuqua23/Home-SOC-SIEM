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
<h2 style="color:red">⚠ WARNING</h2>
<p><strong>This lab was conducted in an isolated VM evironment where the system was intentionally exposed to the public internet for lab and learning purposes ONLY. Do NOT use this configuration in production or on a personal machine.</strong></p>
<em>Ignoring this warning in production is an efficient way to test your incident response plan without asking for permission.</em>

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

This project provided an interesting way to get hands-on experience in cloud security monitoring and a realistic look into how quickly exposed systems are attacked on the open internet. By intentionally exposing a Virtual Machine, I experienced firsthand how automated brute-force bots rapidly target vulnerable hosts. Within the first hour of being online, I had roughly one a thousand brute force attempts and to my surprise they were majorily coming from Poland. Connecting the VM to Log Analytics and enabling Sentinel helped me to better understand the workflow of how logs flow from cloud resources into a SIEM system and how a Security Operations Center leverages these tools to detect malicious activity, enrich logs, and investigate potential threats. 

This is my first practical encounter with data analysis involving running KQL queries. This experience taught me essential analytical techniques necessary for handling large volumes of log data. Specifically, I learned how to use KQL to effectively filter events and extract patterns from the logs. A major benefit of using these queries was the ability to rapidly map attacker origins and identify high-frequency indicators of brute-force behavior. This skill is crucial for understanding the nature of the attack and determining where threats are originating. Ultimately, the practice of running KQL queries was fundamental to strengthening my overall understanding of event analysis and incident investigation within the SIEM environment. Seeing these attacks appear live in Sentinel reinforced the importance of foundational security controls, including proper firewall configurations, patching, network segmentation, and credential hardening. Overall, this project strengthened my understanding of SIEM operations, event analysis, and incident investigation, highlighting how misconfigurations can expose an organization to unnecessary risk.

## SCREENSHOTS

This screenshot shows the Azure resource group containing all the starting core components of the lab environment. It includes the Windows 10 virtual machine, associated public IP address, network security group (NSG), network interface, virtual network, and managed disk. Viewing these resources together highlights how the VM is exposed to the internet and how network traffic and security controls are managed within Azure.
<img width="1000" height="700" alt="Built VMs" src="https://github.com/user-attachments/assets/3c4ba7ce-c01e-4412-ae2e-7d5f7308dc14" />

In Powershell, I pinged the virtual machine’s public IP address from my home system. A successful response confirmed that the VM was reachable from the internet, validating that external hosts and attackers could communicate with the system.
<img width="1336" height="943" alt="Ping Vm" src="https://github.com/user-attachments/assets/cd93e524-4c93-4f43-bf5e-b38af4a0e40e" />

I disabled Windows Defender Firewall on the virtual machine to allow all incoming traffic. This configuration was intentionally used for lab purposes to ensure that attack traffic could reach the system without being blocked at the host level. Disabling the firewall helped simulate a poorly secured endpoint and allowed me to observe real-world attack behavior in the logs.
<img width="1000" height="700" alt="Firewall Turn Off" src="https://github.com/user-attachments/assets/89abf795-b14b-4811-a4ef-60d0db97aebf" />

Windows security event collection was enabled for the virtual machine. By allowing Windows Event logs to be ingested into the Log Analytics Workspace, this step ensures that authentication attempts and security-related activity from the VM are available for analysis in Microsoft Sentinel.
<img width="1000" height="700" alt="Setting Up Sentinel" src="https://github.com/user-attachments/assets/73496974-7a4c-4ade-98a6-e531396d5717" />

I used KQL within Microsoft Sentinel to query Windows security events collected from the virtual machine. The initial query retrieves raw security event data, and the refined query narrows the results to highlight key investigation fields such as time generated, account name, computer name, activity type, and source IP address. This step demonstrates how raw logs can be filtered and structured to support efficient security investigations.
<p align="center">
<img width="900" height="650" alt="Log Expand Long" src="https://github.com/user-attachments/assets/a00a1554-a80e-44dc-9ba7-3c095a422a04" />
<img width="900" height="650" alt="Log Query Short" src="https://github.com/user-attachments/assets/ce1441aa-b931-4642-b404-ae5396f35e18" />

</p>

I set a microsoft Sentinel query filtering security events to a single source IP address with repeated failed logon attempts. The results reveal over 1,000 failed authentication attempts occurring roughly one second apart within a short time window, which is a strong indicator of automated brute-force activity. Ordering the events by time generated helps highlight the consistent attack pattern and confirms the behavior was not caused by a legitimate user.
<img width="1000" height="700" alt="KQL query on one IP" src="https://github.com/user-attachments/assets/2c3b5d29-fba4-4e7c-8c2b-31ae09140c03" />

This screenshot shows the KQL query used to generate the global attack map in Microsoft Sentinel. The query extracts failed authentication events, parses source IP addresses, and enriches the data with geographic information so the results can be visualized on a world map. This demonstrates how raw log data is transformed into actionable security visualizations.
<img width="1000" height="700" alt="KQL Create Map Query" src="https://github.com/user-attachments/assets/5fe46553-cd1b-4c64-9616-f0f999c92811" />
 This is the global attack map generated in Microsoft Sentinel using Windows Security Event ID 4625 (failed logon attempts). The map visualizes the geographic origin of IP addresses repeatedly attempting to authenticate to the exposed virtual machine.The objective was to map all the brute force attempts on the VM by region. The major heat areas on the map indicate that the bulk of the attacks were coming from IP Addresses in Jordanow Poland and Tilburg Netherlands.
<img width="1000" height="700" alt="Attack Map" src="https://github.com/user-attachments/assets/0c2d71f3-21f0-40b2-bd74-459438aede7a" />


















