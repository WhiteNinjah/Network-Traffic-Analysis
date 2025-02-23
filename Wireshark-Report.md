# 📡 Wireshark Network Traffic Analysis Report

**Date:** [Enter Date]  
**Analyst:** [Your Name]  
**Investigation Scope:** [E.g., Suspicious Network Activity on Company X]  
**Tools Used:** Wireshark, Suricata, Nmap  

---

## Overview of the Investigation
**What is being analyzed?**  
- Captured **network traffic** for [X minutes/hours/days].  
- Purpose: Identify **suspicious/malicious activity** in the traffic.  
- The `.pcap` file contains **X number of packets**.

---

##  Summary of Findings  
**Key Observations:**  
 **High amount of unusual DNS requests** → Possible **Command & Control (C2) communication**  
 **Multiple SYN packets with no ACK responses** → **Potential Port Scan Attack**  
 **Unencrypted HTTP Traffic** → Possible **Credential Leakage**  
 **Suspicious File Download via FTP** → Could be **malware-related**  

---

##  Step-by-Step Wireshark Analysis  
 **How I investigated the traffic:**  
 **Opened the `.pcap` file in Wireshark**  
 **Applied filters to isolate suspicious traffic:**  
   ```plaintext
   http contains password
   tcp.flags.syn == 1 && tcp.flags.ack == 0
   dns.qry.name contains ".onion"
   ip.src == 192.168.1.10

