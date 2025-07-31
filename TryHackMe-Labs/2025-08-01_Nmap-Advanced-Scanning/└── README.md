# Nmap Advanced Scanning – TryHackMe

## 🔍 What I Learned

### 1. Advanced TCP Scans
- **Null Scan (`-sN`)**: No flags  
- **FIN Scan (`-sF`)**: Only FIN flag  
- **Xmas Scan (`-sX`)**: FIN + PSH + URG  
> Useful to bypass stateless firewalls.

---

### 2. Firewall Types
- **Stateless**: Single-packet inspection  
- **Stateful**: Tracks connection state  
> Stateful firewalls detect stealth scans.

---

### 3. Packet Fragmentation
- `-f` → 8-byte fragments  
- `-ff` → 16-byte fragments  
- `--mtu <n>` → custom fragment size  
> Evades IDS by splitting payloads.

---

### 4. IP ID & Idle Scan
- **IP ID**: field for reassembly  
- **Idle Scan**: uses a “zombie” host’s IP ID  
> Scans anonymously by monitoring IP ID increments.

---

## 🧠 Skills Gained
- Mastered stealth scan variations  
- Distinguished between firewall types  
- Configured fragmentation to evade IDS  
- Understood and practiced the Idle Scan technique

---

**Room Completed:** Nmap Advanced Scans  
**Date:** 2025-08-01  
