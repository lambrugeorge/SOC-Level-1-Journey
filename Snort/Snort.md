# Snort

## 🚀 What is Snort?
Snort is an open-source, rule-based Network Intrusion Detection and Prevention System (NIDS/NIPS) developed by Martin Roesch and maintained by Cisco Talos. It analyzes live and captured network traffic using rules to detect malicious activity and generate alerts. 

---

## 🖥️ Lab Setup & Navigation
- All exercises are in the **Task-Exercises** folder on the Desktop.
- Two subfolders:
  - **Config-Sample:** Example config and rule files (for practice, not used by Snort directly)
  - **Exercise-Files:** Folders for each task, with pcap, log, and rule files ready to use

---

## ⚡ Traffic Generator
- The VM is offline, but you can generate traffic using `traffic-generator.sh`.
- Run it with `sudo ./traffic-generator.sh`.
- Choose the exercise type and watch the output in a new terminal window.
- Each traffic type is designed for a specific exercise—make sure Snort is running before starting!

---

## 📝 Quick Exercise: Easy Mode
Navigate to the **Task-Exercises** folder and run:
```bash
./.easy.sh
```
Check the output for results! (See image below)

![image](1.png)

---

## 🎯 What I Learned
- How to navigate Linux and use the terminal for network analysis
- The basics of Snort and its role as an IDS/IPS
- How to generate and analyze network traffic in a safe lab environment
- How to run scripts and interpret their output

---

> **Snort is a powerful tool for learning network security and intrusion detection!** 🛡️ 


# 📝 Reflection: What I Learned from the Snort Lesson

## Checking Snort Version and Configuration ⚙️
I practiced verifying the installed Snort version using `snort -V`, which displays detailed version and build information. I also learned how to validate the Snort configuration file with `sudo snort -c /etc/snort/snort.conf -T`, ensuring that the setup is correct before running Snort in production or lab environments. Understanding the meaning of key parameters like `-V`, `-c`, `-T`, and `-q` is essential for proper configuration and troubleshooting.

## Running Snort in Different Modes 🖥️
### Sniffer Mode
- I explored Sniffer Mode, which allows real-time packet inspection similar to tcpdump.
- I learned the use of parameters:
  - `-v`: Verbose output (shows TCP/IP info)
  - `-d`: Displays packet data (payload)
  - `-e`: Shows link-layer headers
  - `-X`: Full packet details in HEX
  - `-i`: Specify network interface
- I practiced combining these flags (e.g., `-v -d -e`) to get different levels of detail.
![image](2.png)
### Logger Mode
- I learned how to use Logger Mode to save captured packets to disk for later analysis.
- The `-l` parameter sets the log output directory (default is `/var/log/snort`).
- By default, logs are in binary (tcpdump) format, but using `-K ASCII` creates human-readable, categorized logs in folders named after IP addresses.
- I saw how to navigate and interpret these logs, and the difference between binary and ASCII formats.
![image](3.png)
![image](4.png)
### Reader Mode
- I practiced reading and analyzing previously captured logs with `-r` (e.g., `sudo snort -r snort.log.1638459842`).
- I learned that Snort can process binary logs, and that tools like tcpdump and Wireshark can also be used for deeper analysis.
- I discovered how to use BPF (Berkeley Packet Filter) expressions to filter traffic by protocol or port, and how to limit the number of packets processed with `-n` (e.g., `snort -dvr logname.log -n 10`).

## Traffic Generation and Analysis 🚦
- I used a traffic generator script to simulate different types of network traffic for Snort to analyze.
- This hands-on approach helped me understand how Snort captures, logs, and displays real network events.

## Log File Ownership and Permissions 🔒
- I learned that log files created by Snort (when run with `sudo`) are owned by root, so elevated privileges are needed to view or analyze them.
- I practiced using `sudo` or changing ownership with `chown` to access these files as a regular user.

## Using Additional Tools 🧑‍💻
- I discovered that tcpdump can read Snort's binary log files for quick command-line analysis.
- I also learned that Wireshark can open these logs for advanced, graphical packet inspection.

## Practical Skills and Takeaways 🚀
- I now understand the core concepts of intrusion detection and prevention with Snort.
- I can confidently run Snort in different modes, interpret its output, and analyze network traffic.
- I know how to handle log files, manage permissions, and use additional tools for deeper analysis.
- This lesson gave me practical, hands-on experience that is directly applicable to real-world network security monitoring and incident response.

## 🧪 Practical Snort Traffic Analysis (ASCII Mode)

Let's investigate network traffic using Snort's default configuration in ASCII mode! This hands-on exercise will help you understand how Snort logs and analyzes packets step by step.

1. **Start Snort in ASCII Logging Mode:**
   ```bash
   sudo snort -dev -K ASCII -l .
   ```
   - `-d` : Show packet data (payload)
   - `-e` : Show link-layer headers
   - `-v` : Verbose output
   - `-K ASCII` : Log in human-readable format
   - `-l .` : Log to the current directory

2. **Generate Traffic:**
   Run the traffic generator script and select the "TASK-6 Exercise":
   ```bash
   sudo ./traffic-generator.sh
   ```
   Wait for the traffic to finish, then stop Snort (Ctrl+C).

3. **Analyze the Output:**
   After running the exercise, you will see new log folders in your current directory. For example, navigate to the folder named after the IP address (e.g., `145.254.160.237`).

   - Here, you can inspect the log files to find details such as the source port used to connect to port 53 (DNS), the IP ID of specific packets, HTTP referers, ACK numbers, and more.

4. **Read the Log File with Snort:**
   You can use Snort to read and analyze the generated log file. For example, to view the first 10 packets:
   ```bash
   snort -r snort.log.1640048004 -n 10
   ```
   ![image](5.png)
   - This command helps you inspect packet details, such as IP IDs, HTTP referers, and ACK numbers.

5. **Count TCP Port 80 Packets:**
   By analyzing the log, you can determine how many packets were sent to TCP port 80 (HTTP). This is a great way to practice filtering and counting specific types of traffic.

---

## 🛡️ Snort in IDS/IPS Mode

Snort's capabilities go beyond just sniffing and logging traffic. In IDS/IPS mode, Snort helps you manage and control network traffic based on user-defined rules, making it a powerful tool for intrusion detection and prevention!

> ![image](6.png)

### Key NIDS Mode Parameters

| Parameter | Description |
|-----------|-------------|
| `-c`      | Specify the configuration file. |
| `-T`      | Test the configuration file. |
| `-N`      | Disable logging. |
| `-D`      | Run Snort in the background (daemon mode). |
| `-A`      | Alert modes (see below). |

#### 🚨 Alert Modes (`-A`)

- **full**: Full alert mode, providing all possible information about the alert. This is the default mode if you use `-A` without specifying a mode.
- **fast**: Fast mode shows the alert message, timestamp, source and destination IP, and port numbers.
- **console**: Provides fast-style alerts directly on the console screen.
- **cmg**: CMG style, basic header details with payload in hex and text format.
- **none**: Disables alerting.