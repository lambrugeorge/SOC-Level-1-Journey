# 🚨 Snort Exercise - Network Traffic Analysis Challenge

The room invites you to a challenge to investigate a series of traffic data and stop malicious activity under two different scenarios. Let's start working with Snort to analyze live and captured traffic.

> **💡 Recommendation**: Complete the Snort room first, which will teach you how to use the tool in depth.

## 📁 Exercise Files

Exercise files for each task are located on the desktop as follows:

![Exercise Files](1.png)

---

## 🔍 Task 1: Writing IDS Rules (HTTP)

### Commands Used:
```bash
sudo snort -r snort.log.1753562780 -n 65  
sudo snort -c local.rules -A full -l . -r mx-3.pcap
```

### Local Rules Configuration:
```bash
# ----------------
# LOCAL RULES
# ----------------
# This file intentionally does not come with signatures. Put your local
# additions here.

alert tcp any 80 <> any any (msg:"TCP port 80 found"; sid:100001; rev:1;)
```

---

## 🎯 Challenge: Create IDS Rules for HTTP Traffic!

**Instructions**: Navigate to the task folder and use the given pcap file. Write a rule to detect all TCP packets from or to port 80.

### 📊 Questions & Answers

#### 1️⃣ **What is the number of detected packets you got?**

> **Note**: You must answer this question correctly before answering the rest of the questions.

![Detected Packets](2.png)

**Answer**: `164`

✅ **Correct Answer**

💡 **Hint**: Investigate the log file.

---

#### 2️⃣ **What is the destination address of packet 63?**

![Packet 63 Analysis](3.png)

**Answer**: `216.239.59.99`

✅ **Correct Answer**

💡 **Hint**: Investigate the log file.

---

#### 3️⃣ **What is the ACK number of packet 64?**

**Answer**: `0x2E6B5384`

✅ **Correct Answer**

💡 **Hint**: Investigate the log file.

---

#### 4️⃣ **What is the SEQ number of packet 62?**

**Answer**: `0x36C21E28`

✅ **Correct Answer**

💡 **Hint**: Investigate the log file.

---

#### 5️⃣ **What is the TTL of packet 65?**

![Packet 65 TTL](4.png)

**Answer**: `128`

✅ **Correct Answer**

💡 **Hint**: Investigate the log file.

---

#### 6️⃣ **What is the source IP of packet 65?**

**Answer**: `145.254.160.237`

✅ **Correct Answer**

💡 **Hint**: Investigate the log file.

---

#### 7️⃣ **What is the source port of packet 65?**

![Packet 65 Source Port](5.png)

**Answer**: `3372`

✅ **Correct Answer**

---

## 🎉 Exercise Complete!

You have successfully analyzed network traffic using Snort IDS rules and extracted key packet information including IP addresses, port numbers, sequence numbers, and TTL values.