# Building a Security Monitoring Lab with Elastic SIEM and Kali VM  

## Overview  
This project involved setting up a home security monitoring lab using Elastic SIEM and a Kali Linux VM to gain hands-on experience with security event detection, log analysis, and incident response.  

---

## Setting Up the Security Lab  

### 1. Deploying Elastic SIEM  
- Created a free [Elastic Cloud](https://cloud.elastic.co/) account  
- Started a new deployment with Elasticsearch  
- Configured region and deployment size  
  ![Elastic Deployment](assets/elastic-deployment.png)  

### 2. Setting Up Kali Linux in VirtualBox  
- Installed Oracle VirtualBox and Kali Linux ISO  
- VM Configuration:  
  - 2GB RAM | 20GB storage  
  - Debian (64-bit) OS type  
  - Dynamic VDI allocation  
  ![Kali VM](assets/kali-vm.png)  

---

## Configuring Log Collection with Elastic Agent 
