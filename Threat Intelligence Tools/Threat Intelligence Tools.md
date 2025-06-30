# 🌐 Threat Intelligence Tools: What I've Learned

This document summarizes what I've learned about Threat Intelligence and several open-source tools that help in identifying and mitigating cyber threats. 🚨

---

## 🎯 Learning Objectives

- Understand the basics of threat intelligence & its classifications.
- Use UrlScan.io to scan for malicious URLs.
- Track malware and botnet indicators with Abuse.ch.
- Investigate phishing emails using PhishTool.
- Gather intel with Cisco's Talos Intelligence platform.

---

## 🕵️‍♂️ What is Threat Intelligence?

Threat Intelligence is the process of analyzing data to find patterns and insights that help defend against current or emerging threats targeting organizations, industries, or governments.

### Key Questions to Ask:
- Who is attacking?
- What is their motivation?
- What are their capabilities?
- What indicators of compromise (IOCs) should you look for?

---

## 🗂️ Threat Intelligence Classifications

- **Strategic Intel**: High-level overview of threat landscapes and risks for business decisions.
- **Technical Intel**: Evidence and artifacts of attacks, useful for incident response teams.
- **Tactical Intel**: Focuses on adversary tactics, techniques, and procedures (TTPs) to improve security controls.
- **Operational Intel**: Looks at adversary motives and intent, helping to protect critical assets.

---

## 🛠️ Abuse.ch Platforms

Abuse.ch is a project from the Institute for Cybersecurity and Engineering at Bern University of Applied Sciences, Switzerland. It provides several platforms to track malware and botnets:

- **Malware Bazaar**: Upload and hunt for malware samples. Analysts can set alerts based on tags, YARA rules, and more.
- **Feodo Tracker**: Database of botnet C&C servers (e.g., Dridex, Emotet, TrickBot). Provides IP and IOC blocklists.
- **SSL Blacklist**: Identifies malicious SSL certificates and JA3/JA3s fingerprints to block botnet C2 communications.
- **URLhaus**: Shares malicious URLs used for malware distribution. Search by domain, URL, hash, or filetype.
- **Threat Fox**: Search, share, and export IOCs in multiple formats (MISP, Suricata, CSV, etc.).

---

## 📝 My Answers

### 1️⃣ The IOC `212.192.246.30:5555` is identified under which malware alias name on ThreatFox?
![image](1.png)
**Answer:** Katana

---

### 2️⃣ Which malware is associated with the JA3 Fingerprint `51c64c77e60f3980eea90869b68c58a8` on SSL Blacklist?
![image](2.png)
**Answer:** Dridex

---

### 3️⃣ From the statistics page on URLHaus, what malware-hosting network has the ASN number `AS14061`?
![image](3.png)
**Answer:** DIGITALOCEAN-ASN

---

### 4️⃣ Which country is the botnet IP address `178.134.47.166` associated with according to FeodoTracker?
![image](4.png)
**Answer:** Georgia

---

> ✅ I've learned how to use these tools and understand the different types of threat intelligence. This knowledge helps me better identify, analyze, and respond to cyber threats! 🚀
