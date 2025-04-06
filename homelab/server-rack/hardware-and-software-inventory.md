# Hardware and software inventory

### 🖥️ Home Lab Inventory

#### 🔧 Software Inventory

| System           | OS / Platform                               | Tools / Services Running                         | Purpose                                  |
| ---------------- | ------------------------------------------- | ------------------------------------------------ | ---------------------------------------- |
| **Container**    | Ubuntu 24.04 LTS (x86\_64)                  | Rclone (automated backup to Backblaze B2)        | Cloud backup automation                  |
| VM               | Ubuntu 24.04 LTS (x86\_64)                  | Standard desktop environment                     | Daily use / admin tasks                  |
| **VM**           | Kali Linux Rolling (x86\_64)                | Greenbone Vulnerability Management (GVM)         | Vulnerability scanning                   |
| VM               | Ubuntu 24.04 LTS (x86\_64)                  | Full ELK Stack (Elasticsearch, Logstash, Kibana) | Home network telemetry & monitoring      |
| VM               | pfSense Plus 2.7.x (FreeBSD-based, x86\_64) | Suricata(IDS), Zeek, Squid Proxy                 | Network firewall, IDS/IPS, traffic proxy |
| **VM**           | Windows 10 x64 (FlareVM)                    | Sysinternals Suite, Ghidra, IDA Free, x64dbg     | Malware analysis & reverse engineering   |
| **VM**           | Remnux 2023 (Ubuntu 22.04 LTS x86\_64)      | SANS REMnux toolset                              | Reverse engineering, malware lab         |
| VM               | Ubuntu 24.04 LTS (x86\_64)                  | ELK Stack for test range                         | Controlled test environment              |
| **Raspberry Pi** | Raspbian OS (Debian 12 “Bookworm”)          | Pi-hole DNS sinkhole                             | Ad/tracker blocking for LAN              |

***

#### 🖥️ Hardware Inventory

| Item                                         | Description                                             |
| -------------------------------------------- | ------------------------------------------------------- |
| **Dell PowerEdge R630**                      | Enterprise-grade 1U server for virtualization/workloads |
| **Dell 1U Ready Rail Kit**                   | Rack rails for mounting R630                            |
| **Vevor 12U Open Frame Server Rack**         | 12U rack for lab hardware                               |
| **Cisco SG200-50FP**                         | 50-Port Gigabit PoE Smart Switch                        |
| **CyberPower CPS1215RM**                     | Basic rack-mounted PDU (Power Distribution Unit)        |
| **Raplink 24-Port Cat6 Patch Panel**         | Cable management and network distribution               |
| **Cat6a Slim Patch Cables**                  | High-speed, slim-profile networking cables              |
| **Uctronics 1U Rack Mount for Raspberry Pi** | Rack-mounted Raspberry Pi housing                       |
| **Raspberry Pi 4**                           | Hosting Pi-hole and lightweight services                |
| **AmpliFi Mesh Wi-Fi System**                | Home mesh networking                                    |
| **Linksys AX1800 WiFi 6 Router**             | Dual-band router for high-speed wireless                |

