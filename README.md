# Splunk-Zeek-Connection-Log-Analysis
## 🧠 What is Zeek?
- **Zeek (formerly known as Bro) is an open-source network security monitor. It passively analyzes network traffic and generates rich, high-fidelity logs for security monitoring, incident response, and forensics.**
- **Category: Network Security Monitor (NSM) / Intrusion Detection System (IDS)**
- **Developed by: Originally by Vern Paxson, maintained by the Zeek Project**
- **Primary use: Network traffic analysis, protocol parsing, and threat detection**
## Features
- **Protocol Analysis	Understands DNS, HTTP, SSL/TLS, FTP, SSH, and many others at a deep level**
- **Log Generation	Creates comprehensive logs (e.g., conn.log, dns.log, http.log)**
- **Passive Monitoring	No active traffic generation; it observes and analyzes silently**
## 🗂️ Common Log Files in Zeek
- **conn.log	Connection summaries (source/dest IP, port, protocol, duration, etc.)**
- **dns.log	DNS queries and responses**
- **http.log	HTTP requests and responses (method, URI, user-agent, etc.)**
- **ssl.log	SSL/TLS handshake information**
- **files.log	Files transferred over the network**
## ⚙️ How Zeek Works
- **Capture Traffic: Zeek uses packet sniffing (via libpcap or from pcap files).**
- **Parse Protocols: It decodes layers (Ethernet → IP → TCP/UDP → Application Protocols).**
- **Generate Events: Zeek recognizes events (e.g., HTTP request, DNS response).**
 **Script Execution: Events trigger Zeek scripts that generate logs or alerts.**
- **Log Output: Writes results to log files (by default, in /usr/local/zeek/logs**

# 🎯 Objective
- **Learn how to upload and search Zeek connection logs in Splunk.**
- **Find top clients, top servers, and most common services.**
- **Identify large traffic and long connections.**
# 🖥️ Lab Setup
- **✅ Splunk: Already installed and accessible.**
- **✅ Data Source: JSON-formatted Zeek-style connection logs.**
- **🌐 Log File: Download and upload to Splunk using the steps below.**
     https://raw.githubusercontent.com/0xrajneesh/30-Days-SOC-Challenge-Beginner/refs/heads/main/zeek_conn_logs.json
 # ⚙️ Steps to Upload Conn Log into Splunk
- **Go to Splunk Web → Settings > Add Data.**
- **Choose Upload and select zeek_conn_logs.json.**
- **Set Source type: json or create a new one like zeek:conn.**
- **Index: Use main or create a new one called conn_lab.**
- **Complete the upload and check that logs are searchable.**
![Add Data - Select Source _ Splunk 9 4 2 - Google Chrome 03-05-2025 11_34_42](https://github.com/user-attachments/assets/07c096cf-e47f-454d-bc76-0ffe5efc604f)

#🔍 Lab Tasks
 Used the following SPL queries to complete each task:
 
# ✅Task 1: Find the Top 10 Client IPs (id.orig_h)
- **index=conn_lab sourcetype="json"
| stats count by id.orig_h
| sort -count
| head 10**
![Add Data - Select Source _ Splunk 9 4 2 - Google Chrome 03-05-2025 11_35_47](https://github.com/user-attachments/assets/2f1dae79-3abb-46c1-a1af-38e5fe2eb841)

# ✅Task 2: List Most Common Services
- **index=conn_lab sourcetype="json"
| stats count by service
| sort -count**
![Add Data - Select Source _ Splunk 9 4 2 - Google Chrome 03-05-2025 11_37_03](https://github.com/user-attachments/assets/ef04981e-b36b-43e5-8714-78053e20de89)

# ✅Task 3: Find Connections with Duration > 1 Second
- **index=conn_lab sourcetype="json"
| stats count by "id.resp_h"
| sort -count
| head 10**
![Add Data - Select Source _ Splunk 9 4 2 - Google Chrome 03-05-2025 11_41_25](https://github.com/user-attachments/assets/888cccd0-0b92-4958-9108-6269e471c590)

# ✅Task 4: Identify the Most Accessed Internal Servers
- **index=conn_lab sourcetype="json"
| stats count by "id.resp_h"
| sort -count
| head 10**
![Add Data - Select Source _ Splunk 9 4 2 - Google Chrome 03-05-2025 11_43_20](https://github.com/user-attachments/assets/e649f7fc-6032-4b31-ac40-5eeac26248b9)

# CONCLUSION
- **Learned about zeek and how to analyze the zeek log file . Got hands on knowledge about zeek and splunk .**





