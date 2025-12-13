# Azure SOC+SIEM Lab-Windows 10 Honeypot + Microsoft Sentinel

In this lab, I deployed a Windows 10 virtual machine inside Microsoft Azure, intentionally exposed it to the public internet, and used Microsoft Sentinel to collect attack data in real-time. The VM acted as a honeypot, allowing me to observe real-world malicious activity and understand how SIEM monitoring can detect brute force attempts, port scans, and other threats targeting public systems.
The goal of this project was to gain hands-on experience configuring Azure resources, enabling logging, forwarding security events, and building visual analytics inside Sentinel.

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

# What I Learned 
This project provided practical, hands-on experience in cloud security monitoring, offering a clear demonstration of how rapidly systems are attacked when exposed to the open internet.
I observed firsthand how automated brute-force bots rapidly target vulnerable hosts. When I intentionally exposed the VM to the internet, there were roughly a thousand brute force attempts wihtin the first hour. Seeing these attack attempts appear live in Sentinel highlighted the absolute necessity of foundational security measures such as proper firewall configurations, regular patching, network segmentation, and using strong security for logins. <br/>


In terms of security analysis, connecting the VM to Log Analytics and enabling Sentinel allowed me to see frist hand how logs flow from cloud resources flow into a SIEM system. This process taught me how a Security Operations Center uses SIEM tools to detect malicious activity, enrich logs, and investigate potential threats. <br/>
This was my frist time really experimenting with KQL and I found it useful to help with filtering through events, extracting attack patterns, mapping the geographical origins of attackers, and identify indicators of frequent brute-force behavior.
Furthermore, I learned the importance of visual communication in security by building visualizations, such as a global attack heatmap. This showed how SOC analysts can quickly spot emerging trends and identify suspicious geographical regions or abnormal spikes in activity.
Overall, this exercise significantly strengthened my understanding of SIEM operations, event analysis, and incident investigation, clarifying how quickly and easily misconfigurations can expose an organization to unnecessary risk




Building visualizations, such as a global attack heatmap, demonstrated how SOC analysts leverage data to quickly spot trends. These visualizations help in identifying suspicious regions or abnormal spikes in activity.
Overall, the project strengthened my understanding of SIEM operations, event analysis, incident investigation, and provided a good demonstration of how misconfigurations can expose an organization to unnecessary risk

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
















