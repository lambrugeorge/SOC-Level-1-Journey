# Carnage Exercise — Malicious Network Traffic Analysis 🕵️‍♂️

---

## Scenario 🧩

Eric Fischer from the Purchasing Department at Bartell Ltd received an email from a known contact with a Word document attachment. Upon opening the document, he accidentally clicked on **"Enable Content"**. The SOC Department immediately received an alert from the endpoint agent that Eric's workstation was making suspicious outbound connections. The pcap was retrieved from the network sensor and handed to you for analysis.

**Task:** Investigate the packet capture and uncover the malicious activities.  

*Credit goes to Brad Duncan for capturing the traffic and sharing the pcap packet capture with the InfoSec community.*

---

## Questions & Answers 📌

**Q1: What was the date and time for the first HTTP connection to the malicious IP?**  
✅ **Answer:** `2021-09-24 16:44:38`  
![image](1.png)

**Q2: What is the name of the zip file that was downloaded?**  
✅ **Answer:** `documents.zip`  
![image](2.png)

**Q3: What was the domain hosting the malicious zip file?**  
✅ **Answer:** `attirenepal.com`  
![image](3.png)

**Q4: Without downloading the file, what is the name of the file in the zip file?**  
✅ **Answer:** `chart-1530076591.xls`  
![image](4.png)

**Q5: What is the name of the webserver of the malicious IP from which the zip file was downloaded?**  
✅ **Answer:** `LiteSpeed`  
![image](5.png)

**Q6: What is the version of the webserver from the previous question?**  
✅ **Answer:** `PHP/7.2.34`  
![image](6.png)

**Q7: Malicious files were downloaded to the victim host from multiple domains. What were the three domains involved with this activity?**  
✅ **Answer:** `finejewels.com.au, thietbiagt.com, new.americold.com`  
![image](7.png)
![image](8.png)
![image](9.png)

**Hint:** Which certificate authority issued the SSL certificate to the first domain from the previous question?  
✅ **Answer:** `GoDaddy`  
![image](10.png)

**Q8: What are the two IP addresses of the Cobalt Strike servers? Use VirusTotal (Community tab) to confirm if IPs are identified as Cobalt Strike C2 servers.**  
✅ **Answer:** `185.106.96.158, 185.125.204.174`  
![image](11.png)
![image](12.png)

**Q9: What is the Host header for the first Cobalt Strike IP address from the previous question?**  
✅ **Answer:** `ocsp.verisign.com`  
![image](13.png)

**Q10: What is the domain name for the first IP address of the Cobalt Strike server? You may use VirusTotal to confirm if it's the Cobalt Strike server (Community tab).**  
✅ **Answer:** `survmeter.live`  
![image](14.png)
