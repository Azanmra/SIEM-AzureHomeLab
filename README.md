<h1>SIEM Azure Honeypot Homelab</h1>


<h2>Description</h2>
Project consists of a simple honeypot home lab in azure, honeypots act as decoy systems, purposefully set up to lure and observe malicious activity. This offers deep insights into potential threats and the tactics used by attackers. A SIEM (Security Information and Event Management) system serves as a centralized solution for collecting, analyzing, and responding to security events in real time. With Azure Sentinel—Microsoft’s cloud-native SIEM, the user will gain a unified view of the security landscape, enhanced by automated threat detection and response capabilities. Step into my homelab, where we track live attacks from across the globe and visually display on a world map to show severity.


<br />


<h2>Requirements:</h2>

- <b>Microsoft Azure + Account</b> 
- <b>Azure Services: Sentinel, Log Analytics Workspace, Workbooks, Network Security Groups</b>
- <b>Remote Desktop Protocol</b>


<h2>Objectives:</h2>

- <b>Deploying and configuring multiple Azure components such as Virtual Machines (VMs), Log Analytics Workspaces, and Azure Sentinel.</b>
- <b>Engaging in Microsoft Azure Sentinel, a SIEM (Security Information and Event Management) tool for log management.</b>
- <b>Writing KQL queries to analyze logs.</b>
- <b>Gaining expertise in interpreting Security Event Logs in Windows.</b>
- <b>Creating a interactive maps visualizing attack statistics.</b>


<h2>Overview of Process </h2>

<a href='https://postimg.cc/rKJXJkxC' target='_blank'><img src='https://i.postimg.cc/zGmzqDfM/Blue-Illustrated-Professional-Path-Design-Process-Timeline-Infographic.jpg' border='0' alt='Blue-Illustrated-Professional-Path-Design-Process-Timeline-Infographic'/></a>


<h2>The First Step</h2>

- <b>Creating a Virtual Machine (VM): Set up a secure virtual machine in Azure with a strong login and password (Honeypot).</b>
- <b>Establishing a Resource Group: Create a resource group to configure a network in the cloud, provided by Microsoft.</b>
- <b>Configuring Virtual Network (VNet) and Subnet: Set up a VNet and subnet within the resource group to act as a router for the project’s infrastructure.</b>
- <b>Ensuring that both the resource group and virtual machine are located in the same region (US East 2) for compliance and smooth operation.</b>

<a href='https://postimg.cc/tY0CfpsK' target='_blank'><img src='https://i.postimg.cc/fTytVbDR/Capture3.png' border='0' alt='Capture3'/></a>

<a href='https://postimg.cc/kDC7FwLC' target='_blank'><img src='https://i.postimg.cc/qBhgr5LN/Capture4.png' border='0' alt='Capture4'/></a>


<h2>The Second Step</h2>

- <b>Lowering Network Security: Configure the network group to allow unrestricted access to the virtual machine (honeypot) from the public, with the destination port set to * (any).</b>
- <b>Accessing Internal Firewall: Turn off the internal firewall on the virtual machine, enabling remote desktop access via the public IP address of the honeypot.</b>
- <b>Disabling Windows Defender Firewall: Disable Windows Defender firewall on all profiles to ensure unrestricted access.</b>
- <b>Testing Accessibility: Perform a ping test on the virtual machine to confirm that it is globally accessible.</b>

<a href='https://postimg.cc/hh0dR2m4' target='_blank'><img src='https://i.postimg.cc/ZYGF3gKN/Capture6.png' border='0' alt='Capture6'/></a>

<a href='https://postimg.cc/87xFm324' target='_blank'><img src='https://i.postimg.cc/d0V8wcnb/Capture7.png' border='0' alt='Capture7'/></a>

<a href='https://postimg.cc/bGbZCg8h' target='_blank'><img src='https://i.postimg.cc/xdpLdp4c/Capture8.png' border='0' alt='Capture8'/></a><br /><a href='https://gasstation-nearme.com/'>find gas near me</a><br />


<h2>The Third Step</h2>

- <b>Configuring Log Repository: Set up a log repository for storing logs from the virtual machine.</b>
- <b>Forwarding Logs to Repository: Forward the virtual machine logs to the log repository within Log Analytics Workspace.</b>
- <b>Storing Logs in Workspace: Ensure that the logs from the virtual machine are stored securely in the Log Analytics Workspace for monitoring and analysis.</b>
- <b>Integrating with Microsoft Sentinel: Add the Log Analytics Workspace to Microsoft Sentinel to connect and forward the logs from the virtual machine to Sentinel.</b>
- <b>Event ID Filtering: Configure Sentinel to forward specific Event IDs (such as 4625) for the project, ensuring relevant data is captured.</b>

<a href='https://postimg.cc/5XQ5Jw1P' target='_blank'><img src='https://i.postimg.cc/fRB8xKPh/Capture9.png' border='0' alt='Capture9'/></a>

<a href='https://postimg.cc/qhwywwX7' target='_blank'><img src='https://i.postimg.cc/prbC21mK/Capture10.png' border='0' alt='Capture10'/></a>


<h2>The Fourth Step</h2>

- <b>Configuring Azure Security Events via Azure Monitoring Agent (AMA): Download the necessary content for security event monitoring through the Content Hub and configure the Azure Monitoring Agent to capture the security events from the virtual machine.</b>
- <b>Creating a Data Collection Rule: Set up a data collection rule that enables the SIEM system to access and retrieve the logs forwarded by the Log Analytics Workspace, ensuring data flow and integration.</b>
- <b>Viewing Windows Logs through Query Hub: Utilize the Query Hub and KQL (Kusto Query Language) to run queries that display all security events stored in the database. For example, the SecurityEvent command will show all relevant logs from the virtual machine.</b>
- <b>Tracking Malicious Activity: To monitor attempted attacks or unauthorized login attempts, specifically failed logins from the public internet, run the KQL command: | where EventID == 4625. This will filter the logs for Event ID 4625, which corresponds to failed login attempts.</b>

<a href='https://postimg.cc/Q9jhsJL1' target='_blank'><img src='https://i.postimg.cc/ydZdmLvQ/Capture12.png' border='0' alt='Capture12'/></a>

<a href='https://postimg.cc/DmynM6PK' target='_blank'><img src='https://i.postimg.cc/wxDM3bt3/Capture13.png' border='0' alt='Capture13'/></a>

<a href='https://postimg.cc/XXH4S5sB' target='_blank'><img src='https://i.postimg.cc/PrhxDzZy/Capture14.png' border='0' alt='Capture14'/></a>

<h2>The Fifth and Final step</h2>

creating a watch list on sentinel with a template <instert [here](https://drive.google.com/file/d/13EfjM_4BohrmaxqXZLB5VUBIz2sv9Siz/view)> on microsoft sentinel this will upload geodata location to the SIEM (sort out the network ip, latitudes, longitudes, city names and the country names)
Making a new workbook for the visual attack map with a template <insert here> to show  locations of where the attacks were attempted.
The virtual machine was only online for 24 hours where the attacks on the map image below shows the following
The yellow areas show where minimum amount of attacks were attempted. The orange areas show where a decent amount of attacks were attempted. The red area shows where most of attacks were attempted. 













<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
