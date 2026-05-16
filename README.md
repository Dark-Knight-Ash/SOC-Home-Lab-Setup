#  SOC Home Lab Setup 

##  Overview

This project demonstrates the setup of a personal SOC (Security Operations Center) Home Lab designed to simulate real-world cyberattack and defense scenarios in a controlled virtualized environment.

The lab was built to gain hands-on experience in:

* SIEM Monitoring
* Threat Hunting
* Log Analysis
* Incident Investigation
* Network Monitoring
* Endpoint Visibility
* MITRE ATT&CK Mapping
* Attack Detection & Response

The environment uses the ELK Stack for centralized log collection and visualization, Kali Linux for attack simulation, and Windows as the victim machine.

---

#  Lab Architecture

```text
+-------------------+
|   Kali Linux      |
|  (Attacker VM)    |
+-------------------+
          |
          | Simulated Attacks
          v
+-------------------+
|   Windows 10      |
|   (Victim VM)     |
| Sysmon Installed  |
+-------------------+
          |
          | Winlogbeat Forwarding
          v
+-----------------------------+
| Ubuntu Server               |
| ELK Stack                   |
| - Elasticsearch             |
| - Logstash                  |
| - Kibana                    |
+-----------------------------+
```

---

#  Technologies Used

| Tool          | Purpose                              |
| ------------- | ------------------------------------ |
| Elasticsearch | Log indexing and storage             |
| Logstash      | Log parsing and forwarding           |
| Kibana        | Dashboard visualization and analysis |
| Sysmon        | Endpoint event logging               |
| Winlogbeat    | Forwarding Windows logs              |
| Kali Linux    | Attack simulation                    |
| Ubuntu        | ELK Stack hosting                    |
| Windows 10    | Victim machine                       |

---

#  Features

 Centralized Log Collection
 SIEM-Based Monitoring
 Real-Time Log Analysis
 Threat Hunting Practice
 Brute-Force Detection
 Network Reconnaissance Detection
 Malware Activity Monitoring
 MITRE ATT&CK Technique Mapping
 Security Event Investigation
 Incident Response Workflow Practice

---

#  ELK Stack Setup

## 1. Install Elasticsearch

```bash
sudo apt update
sudo apt install elasticsearch
sudo systemctl enable elasticsearch
sudo systemctl start elasticsearch
```

---

## 2. Install Logstash

```bash
sudo apt install logstash
sudo systemctl enable logstash
sudo systemctl start logstash
```

---

## 3. Install Kibana

```bash
sudo apt install kibana
sudo systemctl enable kibana
sudo systemctl start kibana
```

Access Kibana:

```text
http://<ubuntu-ip>:5601
```

---

#  Windows Logging Setup

## Install Sysmon

Sysmon was installed on the Windows machine for advanced event logging.

### Logs Captured

* Process Creation
* Network Connections
* Registry Changes
* File Activity

---

## Install Winlogbeat

Winlogbeat forwards Windows event logs to the ELK Server.

### Workflow

```text
Windows Logs → Winlogbeat → Logstash → Elasticsearch → Kibana
```

---

#  Attack Simulations

##  Network Reconnaissance

Performed using Nmap from Kali Linux.

```bash
nmap -sV <target-ip>
```

### Detection

* Port scan identification
* Suspicious connection attempts
* Reconnaissance activity visibility

---

##  Brute-Force Login Attempts

Simulated failed login attempts against the Windows machine.

### Detection Indicators

* Event ID 4625
* Multiple failed logins
* Abnormal authentication patterns

### Example Kibana Query

```sql
event.code:4625
```

---

##  Malware Activity Simulation

Simulated suspicious process execution and monitored:

* Process creation
* Registry modifications
* Network callbacks
* Suspicious executable behavior

---

#  Threat Hunting Activities

The lab was used for practical threat hunting exercises such as:

* IOC Identification
* Failed Login Investigation
* Suspicious Process Tracking
* IP Address Investigation
* Event Correlation
* Endpoint Activity Analysis

---

#  MITRE ATT&CK Mapping

| Activity          | Technique ID |
| ----------------- | ------------ |
| Brute-force Login | T1110        |
| Network Scanning  | T1046        |
| Command Execution | T1059        |

---

#  Skills Gained

* SIEM Administration
* ELK Stack Configuration
* Threat Detection
* Log Analysis
* Security Monitoring
* Incident Investigation
* Endpoint Monitoring
* Threat Hunting
* Windows Event Analysis
* Blue Team Operations

---

#  Future Improvements

* Active Directory Integration
* Wazuh Deployment
* Suricata IDS Integration
* Automated Alerting
* Threat Intelligence Feeds
* SOAR Automation

---

#  Learning Outcome

This project provided practical exposure to SOC workflows and real-world cybersecurity monitoring techniques. It improved my understanding of SIEM operations, log analysis, attack detection, and incident response processes used by security analysts.

---

#  Author

Abhijeet Mahendrakar
Cybersecurity Enthusiast | SOC Analyst Aspirant | Blue Team Learner
