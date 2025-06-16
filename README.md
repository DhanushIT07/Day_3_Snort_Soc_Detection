# 🛡️ Snort SOC Detection Lab – Network Threat Simulation

This lab project simulates real-world network threats and monitors them using Snort IDS. It covers ICMP pings, TCP SYN scans, HTTP GET requests, and SSH brute-force attacks.

-----

🧱 Lab Components

| Component       | Description                               |
|----------------|-------------------------------------------|
| **Ubuntu Server** | Target server (Snort + Apache + SSH)       |
| **Kali Linux**  | Attacker machine (ping, curl, hydra)      |
| **Snort IDS**   | Detects network traffic based on rules    |

---

📌 Detection Modules Implemented

✅ ICMP Ping Detection
- **Rule**: Detects incoming ICMP echo (ping) requests.
- **Tools Used**: `ping` from Kali
- **Snort Rule File**: `rules/icmp.rules`

 ✅ TCP SYN Scan Detection
- **Rule**: Alerts on suspicious TCP SYN packets.
- **Tools Used**: `nmap -sS` from Kali
- **Snort Rule File**: `rules/tcp_syn.rules`

✅ HTTP GET Detection
- **Rule**: Monitors for HTTP GET requests to Apache server.
- **Tools Used**: `curl http://<server-ip>` from Kali
- **Snort Rule File**: `rules/http.rules`

✅ SSH Brute-force Detection
- **Rule**: Detects rapid SSH connection attempts (brute-force).
- **Tools Used**: `hydra -l user -P passlist.txt ssh://<server-ip>`
- **Snort Rule File**: `rules/ssh_bruteforce.rules`


# To Start the Snort is IDS

sudo snort -A console -q -c /etc/snort/snort.conf -i eth0


---

 📂 Folder Overview

| Folder          | Description                                       |
|-----------------|---------------------------------------------------|
| `rules/`        | Contains Snort rule files for each attack type    |
| `screenshots/`  | Screenshots showing alerts triggered in Snort     |
| `attack-scripts/` | Sample test commands for each simulation         |
| `notes/`        | Reference commands and setup instructions         |

---

🛠 Sample Rules

ICMP Detection (icmp.rules)
snort
alert icmp any any -> any any (msg:"ICMP Ping Detected"; sid:1000001; rev:1;)
