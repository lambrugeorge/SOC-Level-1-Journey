# TryHackMe Summit Room 🏔️

## Challenge Overview

![image](0.png)

In this premium TryHackMe room, I participated in a **threat simulation and detection engineering challenge** based on the Pyramid of Pain. The goal was to chase a simulated adversary up the pyramid by detecting and blocking their malware samples, increasing the cost of their operations until they gave up.

### Scenario

![image](1.png)

PicoSecure, after several incident response activities, decided to run a threat simulation. I worked alongside an external penetration tester in a purple-team scenario. The tester tried to execute malware samples on a simulated internal workstation, while I had to configure security tools to detect and prevent the malware from running.

The challenge followed the **Pyramid of Pain**—each level required me to detect and block different indicators of attack, starting from the easiest (hashes) and moving up to more complex indicators.

---

## Task 1: Detecting sample1.exe

- **File:** sample1.exe  
- **Tags:** Trojan.Metasploit.A  
- **MD5:** cbda8ae000aa9cbe7c8b982bae006c2a  
- **SHA256:** 9c550591a25c6228cb7d74d970d133d75c961ffed2ef7180144859cc09efca8c  
- **Behavior:** Detected as malicious (Metasploit), connects to unusual port, reads machine GUID, checks LSA protection, etc.

After configuring the detection tools to block this sample by its hash, I received the first flag:

**Flag 1:**  
`THM{f3cbf08151a11a6a331db9c6cf5f4fe4}`

![image](flag1.png)

---

## Task 2: Detecting sample2.exe

![image](2.png)

- **File:** sample2.exe  
- **Tags:** Trojan.Metasploit.A  
- **MD5:** 4d661bf605d6b0b15915a533b572a6bd  
- **SHA256:** d576245e85e6b752b2fdffa43abaab1b2e1383556b0169fd04924d6cebc1cdf9  
- **Behavior:** Also detected as malicious, but with a new hash. Connects to unusual IP and port, reads machine GUID, checks LSA protection, etc.
- **Network Activity:**  
  - HTTP GET to `http://154.35.10.113:4444/uvLk8YI32`
  - TCP connections to `154.35.10.113:4444` and Microsoft IPs

The adversary simply recompiled the malware to bypass hash-based detection, demonstrating the weakness of relying solely on hashes. I needed to use a new detection method for this sample.

---

## Key Takeaways 📝

- **Hash-based detection** is high-confidence but easy to bypass with minor changes to the file.
- **Adversaries adapt quickly**—detection strategies must evolve beyond simple indicators like hashes.
- The Pyramid of Pain framework helps structure detection efforts, pushing defenders to use more resilient and costly-to-evade indicators.





---

## Task 3: Detecting sample3.exe

For the third test, I analyzed **sample3.exe**:

- **File:** sample3.exe  
- **Tags:** Trojan.Metasploit.A  
- **MD5:** e31f0c62927d9d5a897b4c45e3c64dbc  
- **SHA256:** acb9b1260bcd08a465f9f300ac463b9b1215c097ebe44610359bb80881fe6a05  
- **Behavior:**  
  - Detected as malicious (Metasploit)
  - Downloads executable files from the Internet (e.g., backdoor.exe)
  - Connects to unusual IP addresses and ports
  - Reads machine GUID, checks LSA protection, reads computer name, checks supported languages
  - Multiple HTTP(S) requests, TCP/UDP connections, and DNS requests
  - 
![image](flag3(1).png)

After blocking the domain used by the malware, I received the third flag:

**Flag 3:**  
`THM{4eca9e2f61a19ecd5df34c788e7dce16}`

---

### Key Takeaway 📝

Blocking domains and IPs increased the attacker's cost, forcing them to register new domains and update DNS records. However, the adversary warned that for the next sample, blocking hashes, IPs, or domains won't be enough. I will need to focus on detecting artifacts or changes left by the malware on the host system—moving further up the Pyramid of Pain!

------

## Task 3: Detecting sample3.exe

For the third test, I analyzed **sample3.exe**:

- **File:** sample3.exe  
- **Tags:** Trojan.Metasploit.A  
- **MD5:** e31f0c62927d9d5a897b4c45e3c64dbc  
- **SHA256:** acb9b1260bcd08a465f9f300ac463b9b1215c097ebe44610359bb80881fe6a05  
- **Behavior:**  
  - Detected as malicious (Metasploit)
  - Downloads executable files from the Internet (e.g., backdoor.exe)
  - Connects to unusual IP addresses and ports
  - Reads machine GUID, checks LSA protection, reads computer name, checks supported languages
  - Multiple HTTP(S) requests, TCP/UDP connections, and DNS requests

![image](flag3.png)

After blocking the domain used by the malware, I received the third flag:

**Flag 3:**  
`THM{4eca9e2f61a19ecd5df34c788e7dce16}`

---

### Key Takeaway 📝

Blocking domains and IPs increased the attacker's cost, forcing them to register new domains and update DNS records. However, the adversary warned that for the next sample, blocking hashes, IPs, or domains won't be enough. I will need to focus on detecting artifacts or changes left by the malware on the host system—moving further up the





---

## Task 4: Detecting sample4.exe

For the fourth test, I analyzed **sample4.exe**:

- **File:** sample4.exe  
- **File Size:** 219.46 KB  
- **Tags:** None  
- **MD5:** 5f29ff19d99fe244eaf5835ce01a4631  
- **SHA256:** a80cffb40cea83c1a20973a5b803828e67691f71f3c878edb5a139634d7dd422  
- **Behavior:**  
  - Malicious: Disables Windows Defender Real-time monitoring
  - Downloads executable files from the Internet (e.g., backdoor.exe)
  - Connects to unusual IP addresses and ports
  - Makes changes to the registry
  - Reads machine GUID, checks LSA protection, reads computer name, checks supported languages

**Network Activity:**
- HTTP(S) requests:  
  - `GET http://cranes0ft.iniware.xyz:1337/ab9z83ja`
  - `GET http://cranes0ft.iniware.xyz/backdoor.exe`
- Connections to:  
  - `102.23.20.118:1337` (cranes0ft.iniware.xyz)
  - `102.23.20.118:80` (cranes0ft.iniware.xyz)

**Registry Activity:**
- **Write:**  
  - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Defender\Real-Time Protection`  
    - Name: `DisableRealtimeMonitoring`  
    - Value: `1`
  - `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced`  
    - Name: `EnableBalloonTips`  
    - Value: `1`
- **Read:**  
  - `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.txt`  
    - Name: `Progid`  
    - Value: `txtfile`

![image](flag4.png)

---

### Step 3: Registry Modifications

To detect this attack, I created a Sigma rule to monitor for modifications to the Windows Defender Real-Time Protection registry key:

```yaml
title: Modification of Windows Defender Real-Time Protection
id: windows_registry_defender_disable_realtime
description: |
  Detects modifications or creations of the Windows Defender Real-Time Protection DisableRealtimeMonitoring registry value.
references:
  - https://attack.mitre.org/tactics/TA0005/
tags:
  - attack.ta0005
  - sysmon
detection:
  selection:
    EventID: 4663
    ObjectType: Key
    ObjectName: 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Defender\Real-Time Protection'
    NewValue: 'DisableRealtimeMonitoring=1'
  condition: selection
falsepositives:
  - Legitimate changes to Windows Defender settings.
level: high

```

## Task 5: Detecting sample5.exe
![image](flag5.png)

For the fifth test, the adversary changed tactics: all the "heavy lifting" and instructions occurred on their backend server, making it much harder to detect using traditional indicators like hashes, domains, or registry changes. Instead, I had to analyze the outgoing network connections for suspicious patterns.

### Outgoing Connections Analysis

The provided log revealed a very regular pattern:
- Every 30 minutes, the victim machine (`10.10.15.12`) connected to the same remote IP (`51.102.10.19`) on port 443, always sending a small packet (97 bytes).
- There were also some larger, less frequent connections to other IPs and ports.

This regular, low-size beaconing is a classic sign of Command & Control (C2) activity.

---

### Sandbox Analysis

- **File:** sample5.exe  
- **File Size:** 252.46 KB  
- **MD5:** bece9deefe32e2179744d54e36277955  
- **SHA256:** 1fad9b93652f6498f7a4b91159a8c800e2639d035d8b3ddbbde72b762a443558  
- **Behavior:**  
  - Malicious: Downloads executable files from the Internet (beacon.bat)
  - Suspicious: Connects to unusual IP address and port
  - High number of consecutive connections
  - Reads machine GUID, checks LSA protection, reads computer name, checks supported languages

**Network Activity:**
- 402 HTTP(S) requests
- Connections to `bababa10la.cn` (`51.102.10.19`) on multiple ports
- Repeated POST requests from `beacon.bat` to `/keep-alive?hostname=WK102`


![image](flag5(1).png)

---

### Sigma Rule for Detection

To catch this behavior, I created a Sigma rule to alert on




---

## Task 6: Detecting sample6.exe

For the final test, the adversary tried one last trick—moving beyond artifacts or tool detection. This time, I had to focus on something extremely hard for the attacker to change: their techniques and procedures.

### Adversary Communication

Hello again,  
![image](flag6.png)

You managed to detect sample5.exe! I'm very impressed. But also very annoyed! Because now, I need to go back to the drawing board and create a brand new tool to do what I need to do. If I can't find another one quickly, this will be another significant investment. Also, I will need to train myself all over again on how to use it!

I can keep this up one or two times, but there's no way I can continue after this. The reward no longer outweighs the cost, and I would instead find an easier target with detection capabilities much lower on the pyramid.

For my last trick, I have sample6.exe. This time, you will need more than artifacts or tool detection to help you. You'll need to focus on something extremely hard for me to change subconsciously—my techniques and procedures.

I've attached the recorded command logs from all my previous samples to help you understand what actions I tend to perform on my victims to extract info once I have remote access. Good luck!

---

### Command Log Analysis

The attacker’s command log included:
- `dir c:\ >> %temp%\exfiltr8.log`
- `dir "c:\Documents and Settings" >> %temp%\exfiltr8.log`
- `dir "c:\Program Files\" >> %temp%\exfiltr8.log`
- `dir d:\ >> %temp%\exfiltr8.log`
- `net localgroup administrator >> %temp%\exfiltr8.log`
- `ver >> %temp%\exfiltr8.log`
- `systeminfo >> %temp%\exfiltr8.log`
- `ipconfig /all >> %temp%\exfiltr8.log`
- `netstat -ano >> %temp%\exfiltr8.log`
- `net start >> %temp%\exfiltr8.log`

---

### Sandbox Analysis

- **File:** sample6.exe  
- **File Size:** 341.02 KB  
- **MD5:** fc20dd3e92d637cac866c00f26eeb28b  
- **SHA256:** 853a41260626117512efaae7553514b5f96c43ca17440e3f9f2e83ab92463d1a  
- **Behavior:**  
  - Malicious: Downloads executable files from the Internet
  - Suspicious: Connects to unusual IP address and port
  - Reads machine GUID, checks LSA protection, reads computer name, checks supported languages

**Network Activity:**
- HTTP(S) requests:  
  - `GET http://contr0l2hax.info:1499/kwsx92la`
  - `GET https://contr0l2hax.info/sample6.exe`
- Connections to:  
  - `182.44.41.12:1499` (contr0l2hax.info)
  - `182.44.41.12:80` (contr0l2hax.info)
  - `182.44.41.12:443` (contr0l2hax.info)

**Processes:**
- Multiple `cmd.exe` processes spawned by `sample6.exe`
- Creation of `%temp%\exfiltr8.log` containing output from various system commands

![image](flag6(1).png)

---

### Detection Approach

To detect this attack, I focused on identifying the **sequence of commands** and the creation of the exfiltration log file (`%temp%\exfiltr8.log`). This is a strong indicator of attacker behavior and is much harder for them to change compared to simple artifacts.

---

### Final Flag

flag 6

Well, that's it. I have officially given up.

Throughout the engagement, you managed to chase me to the very top of the Pyramid of Pain, and I have to say, it's not fun up here!

You detected my samples file hashes, IPs, domains, host artifacts, tools, and now my own behavioural techniques! To continue, I have no choice but to completely retrain myself and conduct extensive research to figure out how you're catching me. And with that, I don't think you'll ever see me again. Enjoy the final flag; you've earned it!

![image](flag6(2).png)

**Flag 6:**  
`THM{c8951b2ad24bbcbac60c16cf2c83d92c}`

![image](flag6(3).png)

---

### Key Takeaway 📝

By detecting the attacker's techniques and procedures, I reached the very top of the Pyramid of Pain. This level of detection is the most difficult for adversaries to evade and often forces them to give up and move on to easier targets.

---