# Nmap Post-Scan Techniques – TryHackMe

## 🔍 What I Learned

### 1. Service Detection (`-sV`)
- Detects service names and versions  
- Example: `nmap -sV 10.10.10.5` → “Apache 2.4.18”  

### 2. OS Detection & Traceroute
- OS guessing: `-O`  
- Network path: `--traceroute`  
- Helps map firewalls and routing  

### 3. Nmap Scripting Engine (NSE)
- Run scripts: `--script=<name>`  
- Automate vulnerability checks (`vuln`), data gathering (`http-title`, `smb-os-discovery`)

### 4. Saving Output
- `-oN report.txt`  
- `-oX report.xml`  
- `-oG report.gnmap`  

---

### 📸 Screenshots

![Service Detection](./service-detect.png)  
![Traceroute Output](./traceroute.png)  
![NSE Demo](./nse-demo.png)  

---

**Room Completed:** Nmap Post-Scan Techniques  
**Date:** 2025-08-02  
