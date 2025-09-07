
# 🕵️ Masterminds Challenge - Network Forensics Investigation

## 📋 Scenario Overview
Three machines in the Finance department at Pfeffer PLC were compromised. We suspect the initial source of the compromise happened through a phishing attempt and by an infected USB drive. The Incident Response team managed to pull the network traffic logs from the endpoints. Use Brim to investigate the network traffic for any indicators of an attack and determine who stands behind the attacks.

⚠️ **IMPORTANT NOTE**: DO NOT directly interact with any domains and IP addresses in this challenge.

## 🖥️ Setup Instructions
Deploy the machine attached to this task; it will be visible in the split-screen view once it is ready.

If you don't see a virtual machine load then click the Show Split View button.

## 🎯 Investigation Objectives
Start by loading the Infection1 packet capture in Brim to investigate the compromise event for the first machine. All the PCAPs can be found here: `/home/ubuntu/Desktop/PCAPs`

📝 **Note**: For questions that require multiple answers, please separate the answers with a comma.

---

## 🔍 Investigation Results

### 1️⃣ Victim Identification
**Question**: Provide the victim's IP address.

**Answer**: `192.168.75.249`
![image](1.png)
✅ **Correct Answer**

### 2️⃣ Suspicious Domain Analysis
**Question**: The victim attempted to make HTTP connections to two suspicious domains with the status '404 Not Found'. Provide the hosts/domains requested.

**Answer**: `cambiasuhistoria.growlab.es,www.letscompareonline.com`
![image](2.png)
✅ **Correct Answer**

### 3️⃣ Successful HTTP Connection
**Question**: The victim made a successful HTTP connection to one of the domains and received the response_body_len of 1,309 (uncompressed content size of the data transferred from the server). Provide the domain and the destination IP address.

**Answer**: `ww25.gocphongthe.com,199.59.242.153`
![image](3(1).png)
![image](3(2).png)
✅ **Correct Answer**

### 4️⃣ DNS Request Analysis
**Question**: How many unique DNS requests were made to cab[.]myfkn[.]com domain (including the capitalized domain)?

**Answer**: `7`
![image](4.png)
✅ **Correct Answer**

### 5️⃣ Malicious URI Discovery
**Question**: Provide the URI of the domain bhaktivrind[.]com that the victim reached out over HTTP.

**Answer**: `/cgi-bin/JBbb8/`
![image](5.png)
✅ **Correct Answer**

### 6️⃣ Malware Download Identification
**Question**: Provide the IP address of the malicious server and the executable that the victim downloaded from the server.

**Answer**: `185.239.243.112,catzx.exe`
![image](6.png)
✅ **Correct Answer**

### 7️⃣ Malware Classification
**Question**: Based on the information gathered from the second question, provide the name of the malware using VirusTotal.

**Answer**: `Emotet`
![image](7.png)
✅ **Correct Answer**

---

## 🎓 Key Learning Points

### 🔧 Tools Used
- **Brim**: Network traffic analysis and packet capture investigation
- **VirusTotal**: Malware identification and classification

### 🚨 Attack Indicators Identified
- Suspicious domain connections with 404 responses
- Successful HTTP connections to malicious domains
- Multiple DNS requests to suspicious domains
- Malicious URI patterns (`/cgi-bin/` directories)
- Executable file downloads from suspicious IPs

### 🦠 Malware Analysis
- **Emotet**: A notorious banking trojan and malware-as-a-service (MaaS) platform
- Known for its modular architecture and ability to deliver additional payloads
- Commonly spread through phishing emails and malicious attachments

### 🛡️ Security Implications
This investigation demonstrates the importance of:
- Network traffic monitoring and analysis
- DNS query analysis for threat detection
- File download monitoring from external sources
- Correlation of multiple indicators of compromise (IoCs)


-------------------------------------------------------------------------------------------------

## 🦠 Infection 2 - Advanced Malware Analysis

### 📋 Investigation Overview
Please, navigate to the Infection2 packet capture in Brim to investigate the compromise event for the second machine.

📝 **Note**: For questions that require multiple answers, please separate the answers with a comma.

---

## 🔍 Investigation Results - Second Machine

### 1️⃣ Victim Machine Identification
**Question**: Provide the IP address of the victim machine.

**Answer**: `192.168.75.146`
![image](8.png)
✅ **Correct Answer**

### 2️⃣ POST Connection Analysis
**Question**: Provide the IP address the victim made the POST connections to.

**Answer**: `5.181.156.252`
![image](9.png)
✅ **Correct Answer**

### 3️⃣ POST Connection Frequency
**Question**: How many POST connections were made to the IP address in the previous question?

**Answer**: `3`
![image](10.png)
✅ **Correct Answer**

### 4️⃣ Malicious Domain Discovery
**Question**: Provide the domain where the binary was downloaded from.

**Answer**: `hypercustom.top`
![image](11.png)
✅ **Correct Answer**

### 5️⃣ Malicious Binary Identification
**Question**: Provide the name of the binary including the full URI.

**Answer**: `/jollion/apines.exe`
![image](12.png)
✅ **Correct Answer**

### 6️⃣ Malicious Server IP
**Question**: Provide the IP address of the domain that hosts the binary.

**Answer**: `45.95.203.28`
![image](13.png)
✅ **Correct Answer**

### 7️⃣ Suricata Alert Analysis
**Question**: There were 2 Suricata "A Network Trojan was detected" alerts. What were the source and destination IP addresses?

**Answer**: `192.168.75.146,45.95.203.28`
![image](14.png)
✅ **Correct Answer**

### 8️⃣ Stealer Malware Classification
**Question**: Taking a look at .top domain in HTTP requests, provide the name of the stealer (Trojan that gathers information from a system) involved in this packet capture using URLhaus Database.

**Answer**: `Redline Stealer`
![image](15.png)
✅ **Correct Answer**

---

## 🎓 Key Learning Points - Infection 2

### 🔧 Advanced Tools Used
- **Brim**: Advanced packet capture analysis
- **Suricata**: Network intrusion detection system (NIDS)
- **URLhaus Database**: Malware domain and URL intelligence

### 🚨 Advanced Attack Indicators
- **POST connections** to suspicious IP addresses
- **Multiple connection attempts** (3 POST requests)
- **Malicious domain patterns** (.top domains)
- **Binary downloads** from suspicious servers
- **Suricata alerts** for network trojans
- **Information stealer** malware activity

### 🦠 Redline Stealer Analysis
- **Redline Stealer**: A sophisticated information stealer malware
- **Capabilities**: 
  - Browser credential harvesting
  - Cryptocurrency wallet theft
  - System information gathering
  - File exfiltration
  - Keylogging functionality
- **Distribution**: Often distributed through malicious downloads and phishing campaigns

### 🛡️ Security Implications
This investigation demonstrates:
- **Network monitoring** effectiveness with Suricata
- **POST request analysis** for data exfiltration detection
- **Domain reputation** checking (.top domains often used for malicious purposes)
- **Binary analysis** and malware classification
- **Multi-layered defense** with both network analysis and threat intelligence