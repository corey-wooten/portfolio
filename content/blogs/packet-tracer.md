---
title: "Logging Network Activity"
slug: "packet-tracer" 
url: blogs/packet-tracer/
date: 2024-10-05
draft: false
# link: "https://github.com/YOUR-USERNAME/YOUR-REPO"
author: "Corey Wooten"
tags:
  - Networking
  - Cybersecurity
  - Cisco Packet Tracer
  - Syslog
  - FTP
image: /images/projects/misc/packet_650x375.png
description: "A hands-on simulation of FTP traffic and syslog logging using Cisco Packet Tracer."
toc: false
---

#### 🔎 Project's Purpose  
This lab simulation focused on observing and logging network activity in a secure, controlled environment using Cisco Packet Tracer. FTP traffic was created and monitored, and ICMP activity was logged through a syslog server to analyze network behavior and potential vulnerabilities.

#### ⚙️ Tools and Techniques  
The lab featured command-line authentication to an FTP server, file uploads, and ICMP ping tests. Packet captures were used to expose plaintext transmissions, and syslog data was monitored to assess how routers responded to ping events in real-time.

#### 🧪 Key Vulnerability  
FTP login credentials and file data were visible in plaintext, reinforcing the importance of encrypted alternatives like SFTP in production environments.

#### 🧠 Acquired Skills  
  - Network topology simulation and device configuration  
  - FTP and ICMP traffic analysis  
  - Syslog logging and vulnerability detection  
  - Network forensics and CLI diagnostics  
  - Secure protocol awareness and threat mitigation