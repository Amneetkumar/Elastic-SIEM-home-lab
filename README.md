# Elastic-SIEM-home-lab
This repository provides a step-by-step guide to setting up a home lab for Elastic Stack SIEM using the Elastic Cloud portal and a Kali Linux VM. It covers configuring an Elastic Agent to forward security events, querying and analyzing logs in the SIEM, creating dashboards for visualization, and setting up alerts for threat detection.
# Elastic Stack SIEM Home Lab

## Overview
This project sets up a home lab using the Elastic Stack Security Information and Event Management (SIEM) system with a Kali Linux VM. The lab involves generating security events on Kali, setting up an Elastic Agent, and analyzing logs within the Elastic SIEM environment. This project is useful for learning cybersecurity monitoring and incident response techniques.

## Prerequisites
- VirtualBox or VMware
- Basic Linux and virtualization knowledge
- An Elastic Cloud account ([Sign up here](https://cloud.elastic.co/registration))

## Setup Steps

### 1. Create an Elastic Cloud Account
1. Register for a free trial on [Elastic Cloud](https://cloud.elastic.co)
2. Deploy an **Elasticsearch** instance
3. Note the **Kibana URL** and **Elastic credentials**

### 2. Set Up a Kali Linux VM
1. Download Kali Linux from [here](https://www.kali.org/get-kali/#kali-virtual-machines)
2. Import it into VirtualBox/VMware and start the VM
3. Log in with `kali/kali`

### 3. Install and Configure Elastic Agent
1. In Kibana, go to **Integrations** → Search for **Elastic Defend** → Install
<img src="https://i.imgur.com/8zt3Az2.png" height="80%" width="80%"/>
2. Copy the installation command for Linux
<img src="https://i.imgur.com/er2CFiP.png" height="80%" width="80%"/>
3. In Kali, execute the command in the terminal
 <img src="https://i.imgur.com/q35Rz0J.png" height="80%" width="80%"/>  
4. Verify with: `sudo systemctl status elastic-agent.service`

### 4. Generate Security Events
1. Run Nmap scans:
   ```bash
   sudo nmap <target-ip>
   sudo nmap -sS <target-ip>
   sudo nmap -p- <target-ip>
   ```
<img src="https://i.imgur.com/pHvpRAG.png" height="80%" width="80%"/> 

2. Perform privilege escalation attempts (with caution)

### 5. Analyze Security Events
1. Open Kibana → **Observability** → **Logs**
2. Query security logs:
   ```
   event.action: "nmap_scan"
   process.args: "sudo"
   ```
3. Create visual dashboards under **Analytics** → **Dashboards**

### 6. Set Up Alerts
1. Navigate to **Security** → **Alerts**
2. Create a new rule for `event.action: "nmap_scan"`
3. Define severity and notification actions

## Conclusion
This lab enhances practical skills in SIEM monitoring, log analysis, and security event detection. It is a valuable addition to cybersecurity experience and job discussions.

