# Brim 🔍

Brim is an open-source desktop application that processes pcap files and log files, with a primary focus on providing search and analytics capabilities. In this room, I learned how to use Brim to process pcap files and investigate log files to find the needle in the haystack! This room expects familiarity with basic security concepts and processing Zeek log files. I completed the "Network Fundamentals" path and the "Zeek room" before starting this journey.

A VM was attached to this room with a "Split View" feature, and exercise files were located in the folder on the desktop. 
**⚠️ NOTE: I did not directly interact with any domains and IP addresses in this room for safety reasons.**

## What is Brim? 🤔

Brim is an open-source desktop application that processes pcap files and log files, with a primary focus on providing search and analytics. It uses the Zeek log processing format and also supports Zeek signatures and Suricata Rules for detection.

### Input Data Types 📁

Brim can handle two types of data as input:

- **Packet Capture Files**: Pcap files created with tcpdump, tshark, and Wireshark-like applications
- **Log Files**: Structured log files like Zeek logs

### Built on Open-Source Platforms 🏗️

Brim is built on several open-source platforms:

- **Zeek**: Log generating engine
- **Zed Language**: Log querying language that allows performing keyword searches with filters and pipelines
- **ZNG Data Format**: Data storage format that supports saving data streams
- **Electron and React**: Cross-platform UI

## Why Brim? 💡

Ever had to investigate a big pcap file? Pcap files bigger than one gigabyte are cumbersome for Wireshark. Processing big pcaps with tcpdump and Zeek is efficient but requires time and effort. Brim reduces the time and effort spent processing pcap files and investigating the log files by providing a simple and powerful GUI application.

## Brim vs Wireshark vs Zeek ⚖️

While each tool is powerful and useful, it's important to understand their strengths and weaknesses to choose the right tool for the best outcome. As traffic capture analyzers, they have overlapping functionalities, but each has unique value for different situations.

The common best practice is:
- **Wireshark**: Handle medium-sized pcaps
- **Zeek**: Create logs and correlate events
- **Brim**: Process multiple logs
![image](1.png)
| Feature | Brim | Wireshark | Zeek |
|---------|------|-----------|------|
| **Purpose** | Pcap processing; event/stream and log investigation | Traffic sniffing; pcap processing; packet and stream investigation | Pcap processing; event/stream and log investigation |
| **GUI** | ✔️ | ✔️ | ❌ |
| **Sniffing** | ❌ | ✔️ | ✔️ |
| **Pcap processing** | ✔️ | ✔️ | ✔️ |
| **Log processing** | ✔️ | ❌ | ✔️ |
| **Packet decoding** | ❌ | ✔️ | ✔️ |
| **Filtering** | ✔️ | ✔️ | ✔️ |
| **Scripting** | ❌ | ❌ | ✔️ |
| **Signature Support** | ✔️ | ❌ | ✔️ |
| **Statistics** | ✔️ | ✔️ | ✔️ |
| **File Extraction** | ❌ | ✔️ | ✔️ |
| **Handling pcaps over 1GB** | Medium performance | Low performance | Good performance |
| **Ease of Management** | 4/5 | 4/5 | 3/5 |

## Landing Page 🏠

Once you open the application, the landing page loads up with three main sections and a file importing window. It also provides quick info on supported file formats.

### Main Sections 📋

- **Pools**: Data resources, investigated pcap and log files
- **Queries**: List of available queries
- **History**: List of launched queries

## Pools and Log Details 📊

Pools represent the imported files. Once you load a pcap, Brim processes the file and creates Zeek logs, correlates them, and displays all available findings in a timeline.

The timeline provides information about capture start and end dates. Brim also provides information fields - you can hover over fields to get more details. This information helps in creating custom queries. The rest of the log details are shown in the right pane and provide details of the log file fields. You can always export the results using the export function located near the timeline.

## Correlation Features 🔗

You can correlate each log entry by reviewing the correlation section at the log details pane. This section provides information on:

- Source and destination addresses
- Duration
- Associated log files

This quick information helps answer the "Where to look next?" question and find the event of interest and linked evidence.

### Right-Click Menu Options 🖱️

You can right-click on each field to:

- Filter values
- Count fields
- Sort (A-Z and Z-A)
- View details
- Perform whois lookup on IP address
- View the associated packets in Wireshark

## Queries and History 📝

Queries help us correlate findings and find events of interest. History stores executed queries.

### Query Library 📚

The query library lists query names, and once you double-click, it passes the actual query to the search bar. Queries can have names, tags, and descriptions.

You can double-click on a query to execute it easily. Once executed, the actual query appears on the search bar and is listed under the history tab.

### Results Display 📈

Results are shown under the search bar. In my example, I listed all available log sources created by Brim. When I inserted a pcap file, it automatically created nine types of Zeek log files.

### Pre-made Queries 🎯

Brim has 12 premade queries listed under the "Brim" folder. These queries help discover the Brim query structure and accomplish quick searches from templates. You can add new queries by clicking on the "+" button near the "Queries" menu.

## Key Learnings 🎓

Through this room, I learned:

1. **Efficient Pcap Processing**: How Brim handles large pcap files more efficiently than Wireshark
2. **Log Correlation**: The power of correlating different log types to find security events
3. **Query Language**: How to use Brim's query system to search through logs effectively
4. **Tool Selection**: When to use Brim vs Wireshark vs Zeek for different scenarios
5. **GUI Analysis**: How a GUI can make log analysis more accessible and efficient

## Practical Applications 🛠️

Brim is particularly useful for:
- **SOC Analysts**: Quick investigation of security events
- **Incident Responders**: Correlating multiple log sources
- **Threat Hunters**: Searching through large datasets for indicators
- **Security Researchers**: Analyzing captured traffic for patterns

This tool has become an essential part of my security analysis toolkit, especially when dealing with large pcap files and multiple log sources!

