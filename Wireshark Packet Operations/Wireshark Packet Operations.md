## Wireshark — Statistics & Traffic Insights 📊

Today I practiced using Wireshark’s **Statistics menu** to analyze captured traffic and extract useful details for security analysis. 🚀  

---

### What I learned today 🎯
- The **Statistics menu** provides a big-picture view of traffic, protocols, endpoints, and conversations.  
- It helps analysts form hypotheses when investigating suspicious activity.  
- Wireshark is not just for sniffing packets — its statistics tools make it easier to spot anomalies and focus on events of interest.  

---

### Resolved Addresses 🌐
- Shows all IP addresses and DNS names from the capture file.  
- Useful for quickly identifying **accessed resources**.  
- Menu path: `Statistics → Resolved Addresses`  

![image](1.png)

✅ **Question:** What is the IP address of the hostname starting with `bbc`?  
**Answer:** `199.232.24.81`

---

### Protocol Hierarchy 🌲
- Breaks down **all protocols** into a hierarchical view.  
- Displays **counters and percentages**, showing overall usage of services.  
- Analysts can right-click → filter on the protocol of interest.  
- Menu path: `Statistics → Protocol Hierarchy`  

![image](2.png)

✅ **Question:** What is the number of IPv4 conversations?  
**Answer:** `435`

---

### Conversations 💬
- Represents **traffic flows** between two specific endpoints.  
- Available in five formats: Ethernet, IPv4, IPv6, TCP, UDP.  
- Analysts can identify conversations and pivot to relevant traffic.  
- Menu path: `Statistics → Conversations`  

![image](3.png)

✅ **Question:** How many bytes (k) were transferred from the "Micro-St" MAC address?  
**Answer:** `7474`

---

### Endpoints 🖧
- Similar to Conversations, but focused on **unique endpoints**.  
- Supports Ethernet, IPv4, IPv6, TCP, UDP.  
- Can resolve **MAC addresses** into vendor names.  
- Menu path: `Statistics → Endpoints`  

Additional features:
- **Name Resolution:** Convert IP, MAC, and port numbers into human-readable names.  
- **GeoIP Mapping:** Show geographic info for source/destination IPs (requires MaxMind DB).  

![image](4.png)

✅ **Question:** What is the number of IP addresses linked with *Kansas City*?  
**Answer:** `4`  

✅ **Question:** Which IP address is linked with *Blicnet* AS Organisation?  
**Answer:** `188.246.82.7`  

---

### Key Takeaways 🧭
- Use **Resolved Addresses** for quick hostname/IP correlation.  
- **Protocol Hierarchy** gives an overview of captured protocols.  
- **Conversations** & **Endpoints** help pivot into specific traffic flows.  
- Enabling **Name Resolution** and **GeoIP** provides richer context.  



-----------------------------------------------------------------------------------------------------------------------------------------
## Wireshark — Protocol Statistics Deep Dive 🔎

In this lesson, I focused on Wireshark’s **protocol-specific statistics** to analyze IPv4/IPv6, DNS, and HTTP traffic. These tools give analysts a structured way to measure protocol activity and spot anomalies. 🚀  

---

### IPv4 & IPv6 Statistics 🌐
- Narrow down statistics by **specific IP version**.  
- Helps list all events linked to either IPv4 or IPv6 in one window.  
- Useful to separate **legacy vs modern traffic** or focus only on the protocol of interest.  
- Menu path: `Statistics → IPvX Statistics`  

![image](5.png)

✅ **Question:** What is the most used IPv4 destination address?  
**Answer:** `10.100.1.33`

---

### DNS Statistics 📡
- Breaks down **all DNS packets** in a tree view with counters & percentages.  
- Shows usage by **rcode, opcode, class, query type, service, query stats**.  
- Great for spotting unusual DNS behavior (like failed lookups or odd record types).  
- Menu path: `Statistics → DNS`  

![image](6.png)

✅ **Question:** What is the max service request–response time of the DNS packets?  
**Answer:** `0.467897`

---

### HTTP Statistics 🌍
- Breaks down **all HTTP packets** in a tree view with counters & percentages.  
- Shows:  
  - Request/Response codes  
  - Original requests  
  - Overall HTTP service usage  
- Menu path: `Statistics → HTTP`  

![image](7.png)

✅ **Question:** What is the number of HTTP requests accomplished by `rad.msn.com`?  
**Answer:** `39`

---

### Key Takeaways 🧭
- **IPvX Stats** let me isolate IPv4 vs IPv6 usage quickly.  
- **DNS Stats** highlight service performance & anomalies in lookups.  
- **HTTP Stats** reveal web traffic activity, request counts, and response codes.  

These protocol-focused views provide a faster way to correlate events with specific services. 🔐  

---