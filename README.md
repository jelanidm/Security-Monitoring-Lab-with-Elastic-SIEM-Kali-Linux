# Building a Security Monitoring Lab with Elastic SIEM and Kali VM

## Overview

This project involved setting up a home security monitoring lab using Elastic SIEM and a Kali Linux VM to gain hands-on experience with security event detection, log analysis, and incident response.

---

## Setting Up the Security Lab

### 1. Deploying Elastic SIEM
- Created a free Elastic Cloud account at [Elastic Cloud](https://cloud.elastic.co/registration).
- Selected **Elastic for Security** as the use case.
- Chose **SIEM and Security Analytics** as the security focus.
- Opted to store data on **AWS (N. Virginia region)** and launched the deployment.

![Screenshot of Elastic deployment setup.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/elasticforsecurity.png?raw=true)
![Screenshot of Elastic deployment setup.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/Siemandsecurity.png?raw=true)
![Screenshot of Elastic deployment setup.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/elasticlaunch.png?raw=true)

### 2. Setting Up Kali Linux in VirtualBox
- Downloaded the **Kali Linux ISO** from the official website.
- In **VirtualBox**, clicked **Add** to import the Kali Linux ISO.
- Configured **memory (at least 2GB RAM)** and **storage (minimum 20GB)**.
- Installed Kali Linux and completed the initial system setup.

![Screenshot of Kali Linux running in VirtualBox.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/kaliinvb.png?raw=true)

---

## Configuring Log Collection with Elastic Agent

### 3. Installing Elastic Agent on Kali VM
- Logged into the Elastic SIEM instance and navigated to **Integrations**.
 ![Logged into the Elastic SIEM instance and navigated to Integrations](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/addinteg.png?raw=true)
- Selected **Elastic Defend**, installed the integration, and copied the agent installation command.
![Selected **Elastic Defend**, installed the integration, and copied the agent installation command.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/elasticdefend.png?raw=true)
![Selected **Elastic Defend**, installed the integration, and copied the agent installation command.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/elasticagent.png?raw=true)
- Ran the command in Kali Linux terminal to install and enroll the agent.
  ![Terminal output showing successful Elastic Agent installation.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/kaliagent.png?raw=true)
  ![Terminal output showing successful Elastic Agent installation.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/elasticinstalled.png?raw=true)
- Verified successful installation by confirming logs were being forwarded.
![confirming logs were being forwarded..](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/logs.png?raw=true)

---

## Generating Security Events for Analysis

### 4. Running Nmap Scans on Kali VM
- Used **Nmap** to generate network activity logs:
  - `nmap -p- localhost`
  - `sudo nmap <vm-ip>`
  - `nmap -sS <ip address>`
  - `nmap -sT <ip address>`
- Confirmed that scan results were logged and forwarded to Elastic SIEM.

![Screenshot of Nmap scan results.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/nmapscan.png?raw=true)

### 5. Querying and Analyzing Logs in Elastic SIEM
- Navigated to **Observability > Logs** in the Elastic interface.
- Queried Nmap-related logs using:
  - `process.args: "nmap"`
- Analyzed results to understand security events and system activity.

![Screenshot of log query results in Elastic SIEM.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/nmaplogs.png?raw=true)

---

## Building a Security Dashboard and Alerting System

### 6. Creating a Security Dashboard
- Navigated to **Dashboards > Create Dashboard** in Elastic.
![Navigated to **Dashboards > Create Dashboard** in Elastic.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/createdashboard.png?raw=true)
- Added a **Bar Chart** visualization:
  - Set **Count** as the metric.
  - Used **Timestamp** as the horizontal axis.
- Saved the visualization to track Nmap scan activity over time.

![Screenshot of custom Elastic security dashboard.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/dashboard.png?raw=true)

### 7. Setting Up Alerts for Security Incidents
- Navigated to **Security > Alerts > Manage Rules**.
![Navigated to Security > Alerts > Manage Rules](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/managerules.png?raw=true)
- Created a **Custom Query Rule** with the condition:
  - `process.args: "nmap"`
![Created a Custom Query Rule.]([path/to/image](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/nmapcustomrule.png?raw=true))
- Configured **alert delivery methods** and chose **email notifications**.
  ![Screenshot of email alert settings.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/ruleactions.png?raw=true)
- Entered recipient email addresses and customized the alert message.
- Activated the rule to monitor and detect unauthorized scanning activity.
![Screenshot of email alert settings.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/nmaprule.png?raw=true)

![Screenshot of received email alert.](https://github.com/jelanidm/Security-Monitoring-Lab-with-Elastic-SIEM-Kali-Linux/blob/main/images/email%20alert.png?raw=true)

---

## Results & Key Takeaways

- Successfully deployed and configured **Elastic SIEM** and **Kali Linux VM**.
- Implemented **log forwarding** using Elastic Agent and analyzed security events.
- Created **visual dashboards** and **custom alerts** for real-time monitoring.
- Gained hands-on experience in **security event detection**, **incident analysis**, and **SIEM operations**.

This project reinforced my skills in **threat detection, log analysis, and SIEM management**, key competencies in cybersecurity monitoring and defense.
