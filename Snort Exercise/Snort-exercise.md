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


---

## 🛡️ Exercise 2: Writing IDS Rules (FTP)

Let's create IDS Rules for FTP traffic! 🚦

**Instructions:**
- Navigate to the task folder.
- Use the given pcap file for analysis.

---

### 1️⃣ Write a rule to detect all TCP port 21 traffic in the given pcap

**What is the number of detected packets?**

![Detected Packets](6.png)
![Snort Output](7.png)

**Answer:** `307`

✅ **Correct Answer**

💡 **Hint:** Investigate the log file.

---

### 2️⃣ What is the FTP service name?

**Answer:** `Microsoft FTP Service`

![FTP Service Name](8.png)

✅ **Correct Answer**

💡 **Hint:** Clear the previous log and alarm files.

📝 *Tip: Deactivate or comment out the old rules before proceeding!*

---

### 3️⃣ Write a rule to detect failed FTP login attempts in the given pcap

**What is the number of detected packets?**

![Failed FTP Logins](9.png)

**Answer:** `41`

✅ **Correct Answer**

💡 **Hint:** Clear the previous log and alarm files.

📝 *Tip: Deactivate or comment out the old rule before proceeding!*

---

### 4️⃣ Write a rule to detect successful FTP logins in the given pcap

**What is the number of detected packets?**

![Successful FTP Logins](10.png)

**Answer:** `1`

✅ **Correct Answer**

💡 **Hint:** Clear the previous log and alarm files.

📝 *Tip: Deactivate or comment out the old rule before proceeding!*

---

### 5️⃣ Write a rule to detect FTP login attempts with a valid username but no password entered yet

**What is the number of detected packets?**

![Valid User, No Password](11.png)

**Answer:** `42`

✅ **Correct Answer**

💡 **Hint:** Clear the previous log and alarm files.

📝 *Tip: Deactivate or comment out the old rule before proceeding!*

---

### 6️⃣ Write a rule to detect FTP login attempts with the "Administrator" username but no password entered yet

**What is the number of detected packets?**

![Administrator, No Password](12.png)

**Answer:** `7`

✅ **Correct Answer**

💡 **Hint:** Clear the previous log and alarm files.

📝 *Tip: Deactivate or comment out the old rule before proceeding!*

---

## 📝 Useful Commands & Rule Examples

```bash
# Navigate to the exercise folder
cd /home/ubuntu/Desktop/Exercise-Files/TASK-3\ (FTP)/
ls -l

# Run Snort with your rules
sudo snort -c local.rules -r ftp-png-gif.pcap -A console

# Example rule to detect all TCP port 21 traffic
alert tcp any any <> any 21 (msg: "TCP port 21 Found"; sid: 1000001; rev:1;)

grep "TCP port 21 Found" alert
grep -c "TCP port 21 Found" alert

# Find Administrator logins
strings ftp-png-gif.pcap | grep -i "Administrator" | wc -l

# Rule for valid user, waiting for password
alert tcp any any -> any 21 (msg:"FTP valid user - waiting password"; content:"331 Password"; sid:1000004; rev:1;)

# Rule for Administrator login, waiting for password
alert tcp any any -> any 21 (msg:"FTP login Administrator waiting password"; content:"Administrator"; content:"331 Password"; sid:1000006; rev:1;)

grep "FTP login Administrator waiting password" alert | wc -l
tcpdump -nn -r ftp-png-gif.pcap | grep Administrator

# Output files
> alert
> snort.log.*
```
