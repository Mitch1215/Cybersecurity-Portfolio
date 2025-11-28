# Attack Observation Report 2  
**Successful SSH compromise and malware deployment attempt**

## 📌 Summary
An attacker from **8.218.234.50** successfully authenticated into my SSH honeypot using **weak/default credentials (root/123456)**. Once inside, they attempted to download and execute a Linux malware sample linked to the **Dota3 cryptomining botnet**, using both `curl` and `wget`, followed by execution with persistence using `nohup`.

---

## 🎯 Attack Objective
| Goal | Details |
|------|---------|
| Initial access | Weak SSH password exploitation |
| Execution | Download and execute Linux binary (`/tmp/9YkMPjpDqU`) |
| Persistence | Execution via `nohup`, botnet deployment |
| Malware Type | Dota3 botnet – miner, system reconnaissance, persistence |

---

## 🔍 Technique Mapping (MITRE ATT&CK)
| Tactic | Technique |
|--------|-----------|
| Initial Access | Valid Accounts (T1078) |
| Execution | Command and Scripting Interpreter (T1059) |
| Defense Evasion | Obfuscated Files / Malware (T1027) |
| Persistence | Scheduled Task / Background Execution |

---

## 🧪 Key IOCs
| Type | Value |
|------|-------|
| Attacker IP | 8.218.234.50 |
| Malware URL | http://47.242.235.106:66116/Linux |
| File Hash | 4355a46b19d348dc2f57c046f8ef63d4538... |

---

## 🛡 Recommended Mitigations
- Disable root login and enforce strong SSH credentials  
- Restrict SSH access to trusted IPs  
- Deploy **fail2ban** or similar for brute force blocking  
- Monitor for use of `curl`, `wget`, and unauthorized binary execution  
- Application allowlisting for `/tmp` execution prevention

---

📎 Full Report (PDF included in repository)
