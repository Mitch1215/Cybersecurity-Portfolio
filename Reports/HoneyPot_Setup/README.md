# Honeypot Setup Documentation  
**Raspberry Pi-based DShield + Cowrie honeypot with DMZ segmentation**

## Project Overview
This honeypot was deployed as part of an internship with the **SANS Internet Storm Center**, using Cowrie (SSH/Telnet) and DShield for real-time attack logging and malware collection.

---

## Network Architecture
| Component | Details |
|-----------|---------|
| Device | Raspberry Pi 5, 128GB microSD |
| Services | Cowrie SSH/Telnet, DShield sensor |
| Logging | TTY logs, malware capture, log forwarding |
| Isolation | **DMZ zone**, dedicated firewall rules |
| Tools Planned | tcpdump, Wireshark, Snort IDS |

---

## Key Configurations
```bash
# Cowrie enhanced logging
ttylog = true

# DMZ firewall confinement
iptables -A INPUT -p tcp --dport 12222 -s <my.pc.ip> -j ACCEPT
iptables -A INPUT -p tcp --dport 12222 -j DROP
