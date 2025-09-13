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

---

