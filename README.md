<div align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=600&size=28&pause=1000&color=58A6FF&center=true&vCenter=true&width=800&lines=The+TCP%2FIP+Protocol+Suite;Defensive+Architecture+%26+Analysis;Blue+Team+%7C+SOC+Operations" alt="Animated Title" />
  
  <br>
  <i>A practical, layer-by-layer threat detection reference guide.</i>
  <br><br>

  <img src="https://img.shields.io/badge/Author-Muhammad_Umar_Farhan-0d1117?style=for-the-badge&logo=github" alt="Author" />
  <img src="https://img.shields.io/badge/Focus-Defensive_Security-238636?style=for-the-badge" alt="Focus" />
  <img src="https://img.shields.io/badge/Role-SOC_Analyst-1F6FEB?style=for-the-badge" alt="Role" />
</div>

---

## 📌 Executive Summary

This document serves as a defensive reference, focusing on how network data physically intersects with software services. It explores the protocol layers that form the primary battleground for data exfiltration and web-based exploitation in modern cybersecurity.

---

## 🔬 Core Defensive Concepts (Interactive)

*Click on any layer below to expand the threat analysis and detection strategy.*

<details>
<summary><b>🌐 1. The Application Layer (HTTP/S, SNMP, DNS)</b></summary>
<br>
<ul>
  <li><b>The Threat (DNS Tunneling):</b> Attackers embed stolen data inside DNS queries to bypass egress filtering, as Port 53 is rarely blocked by enterprise firewalls.</li>
  <li><b>SOC Detection Strategy:</b> Analysts must baseline normal volume and monitor for unusually long <code>TXT</code> records or high frequencies of unique subdomains originating from a single host.</li>
</ul>
</details>

<details>
<summary><b>⚙️ 2. The Transport Layer (TCP, UDP)</b></summary>
<br>
<ul>
  <li><b>The Threat (Stealth SYN Scans):</b> Adversaries map networks by dropping the connection immediately after a server responds with a <code>SYN-ACK</code>. This avoids completing the handshake and bypasses older application logs.</li>
  <li><b>SOC Detection Strategy:</b> Utilize precise packet filtering to identify incomplete handshakes.
  <br><br>
  <b>Wireshark Filter:</b>
  <pre><code>tcp.flags.syn == 1 and tcp.flags.ack == 0</code></pre>
  </li>
</ul>
</details>

<details>
<summary><b>🔌 3. The Internet & Network Access Layers (IP, ARP, MAC)</b></summary>
<br>
<ul>
  <li><b>The Threat (ARP Poisoning):</b> The lack of innate ARP authentication allows attackers to flood a local switch with fraudulent replies.</li>
  <li><b>SOC Detection Strategy:</b> Monitor for devices aggressively associating an attacker's MAC address with the Default Gateway's IP address, which establishes a Man-in-the-Middle (MitM) position to intercept LAN traffic.</li>
</ul>
</details>

---

## 📊 SOC Monitoring Priority Matrix

| Protocol | OSI/TCP Layer | Primary Function | SOC Monitoring Priority |
| :--- | :--- | :--- | :--- |
| **HTTP/S** | Application | Web Data Transfer | **High** (Payload inspection, malicious user-agents) |
| **DNS** | Application | Name Resolution | **High** (Data exfiltration, DGA domains) |
| **TCP** | Transport | Reliable Streaming | **Medium** (Anomalous port scans, SYN floods) |
| **ARP** | Network Access | IP to MAC Mapping | **High** (Detecting local MitM positioning) |

---

## 📄 Access the Visual Guide

<div align="center">
  <b><a href="./TCP_IP_SOC_Defensive_Guide-v2.pdf">📥 Click Here to Download / View the Full PDF Guide</a></b>
</div>
