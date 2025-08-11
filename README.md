
# 📡 wireshark-network-traffic-analysis

## 📌 Overview
This project demonstrates a complete workflow for capturing, analyzing, and interpreting network traffic using **Wireshark**.  
It was developed as part of an internship task to showcase skills in packet capture, protocol analysis, filtering, and troubleshooting.

🔗 **[Read the Full Project Overview](OVERVIEW.md)**

---

## 🛠 Tools & Environment
- **Wireshark** – Packet analysis tool
- **Npcap** – Windows packet capture driver
- **Windows 10/11** – Test environment

---

## 🚀 Steps Performed
1. **Installation & Setup**
   - Installed Wireshark with Npcap.
   - Enabled WinPcap API compatibility for compatibility with other tools.
   - Verified available network interfaces.

2. **Packet Capture**
   - Selected the active network interface (Wi-Fi/Ethernet).
   - Captured ~6,500 packets during normal browsing activity.
   - Saved the capture as `Network_capture.pcapng`.

3. **Protocol Identification**
   - Used Protocol Hierarchy to analyze traffic composition:
     - QUIC: 46.35% (dominant, HTTP/3 over UDP)
     - UDP: 66.65%
     - TCP: 25.87%
     - DNS, TLS, IGMP, ARP in smaller proportions.

4. **Filtering & Troubleshooting**
   - **QUIC Analysis:** Checked Initial, Handshake, and ACK packets.
   - **DNS Analysis:** Confirmed successful lookups with no failures.
   - **TCP Analysis:** Found duplicate ACKs and out-of-order packets (possible Wi-Fi interference).
   - **Port Analysis:** No traffic on non-standard ports.

---

## 📊 Example Filters Used
```wireshark
quic
dns
tcp.analysis.flags
ip.addr == 142.250.143.94
tcp.port != 80 && tcp.port != 443 && udp.port != 53 && udp.port != 443
