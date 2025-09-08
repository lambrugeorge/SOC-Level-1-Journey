## Wireshark — Traffic Analysis Essentials 🚀

Wireshark is an open‑source, cross‑platform network packet analyzer used to sniff live traffic and inspect packet captures (PCAP). Here’s a concise learning note that reflects what I practiced and understood. 💡

### Getting Started ▶️
- A VM is provided with Split View; no SSH/RDP needed.
- Two captures are available: use `http1.pcapng` to follow the screenshots and `Exercise.pcapng` to answer the questions.

**Files used 📁**
- Screenshots simulated with: `http1.pcapng`
![http1](1.png)
- Questions answered with: `Exercise.pcapng`
![exercise](2.png)

### What I learned today 🎯
- Wireshark helps troubleshoot networks, spot security anomalies, and study protocols.
- It doesn’t modify traffic and it’s not an IDS; value comes from the analyst’s investigation skills.

### Wireshark GUI 🖥️
- **Toolbar**: shortcuts for capture, filter, sort, export, merge.
- **Display Filter Bar**: primary place to query/filter packets.
- **Recent Files**: reopen last PCAPs quickly.
- **Capture Filters & Interfaces**: choose network interfaces and set capture filters.
- **Status Bar**: shows profile, capture state, packet counts.

### Loading PCAPs 📦
- Open via File menu, drag‑and‑drop, or double‑click. After loading, Wireshark displays total packets and detailed panes.

### Packet Panes 🔍
- **Packet List**: per‑packet summary (SRC, DST, protocol, info).
- **Packet Details**: hierarchical protocol fields of the selected packet.
- **Packet Bytes**: hex and ASCII; highlights selection from Details.

### Coloring Rules 🎨
- Default coloring highlights protocols and anomalies at a glance. You can toggle and customize via View → Coloring Rules or context menus. Temporary coloring can be applied per conversation.

### Live Capture 🦈
- Start/stop/restart using the shark/red/green buttons. The status bar shows the active interface and packet counters.

### Merge PCAPs 🔗
- File → Merge combines another capture with the one currently open. Remember to save the merged result as a new file before analysis.

### Capture File Properties 📊
- Use Statistics → Capture File Properties (or the PCAP icon bottom‑left) to view file hash, time, comments, interface, and stats.

### Quick Answers from Exercise.pcapng ✅
- **Flag (capture file comments)**: `TryHackMe_Wireshark_Demo`
![flag](3.png)
- **Total number of packets**: `58620`
- **SHA256 of the capture file**: `f446de335565fb0b0ee5e5a3266703c778b2f3dfad7efeaeccb2da5641a6d6eb`
![sha256](4.png)

### Notes I’ll apply next time 🧭
- Use display filters and conversation filters to quickly pivot to flows of interest.
- Consider custom coloring rules to spotlight suspicious protocols/ports.

-------------------------------------------------------------------------------------------------

### Task 3 — Packet Dissection 🔬

Packet dissection (protocol dissection) is the process of decoding protocols and their fields to understand what’s happening inside each packet. Wireshark supports many protocol dissectors, and you can even extend it with custom ones.

Note: This section assumes OSI model familiarity and shows how Wireshark maps fields to OSI layers for analysis.

#### Packet Details View 🧩
- Open details by selecting a packet in the list (double‑click opens a new window).
- Packets typically show 5–7 layers aligned to OSI.
- Clicking any field highlights the corresponding bytes in the Bytes pane.

Key layers you’ll see:
- **Frame (L1)**: Physical‑level framing and the packet you’re viewing.
- **Source/Destination MAC (L2)**: Data Link addresses.
- **Source/Destination IP (L3)**: Network layer addressing (IPv4/IPv6).
- **Protocol (L4)**: Transport info (TCP/UDP), ports, segments, reassembly.
- **Protocol Errors (L4 cont.)**: Indications such as TCP reassembly.
- **Application Protocol (L5+)**: HTTP, FTP, SMB, etc.
- **Application Data**: The decoded application payload.

Images:
- Packet details and bytes highlighting
- Layer breakdown examples

#### Questions from Exercise.pcapng ✅
- View packet 38 — markup language used under HTTP: **eXtensible Markup Language**
![q1](5.png)
- Arrival date (MM/DD/YYYY): **05/13/2004**
![q2](6.png)
- TTL value: **47**
![q3](7.png)
- TCP payload size: **424**
![q4](8.png)
- E‑Tag value (example format 82ecb-6321-9e904585): **9a01a-4696-7e354b00**
![q5](9.png)