# Nmap & Host Discovery – TryHackMe

## 🧠 What I Learned

### 🔍 Nmap Scan Types
| Scan Type     | Protocol         | Privileged? | When to Use                              |
|---------------|------------------|-------------|-------------------------------------------|
| ARP Scan      | ARP (Link Layer) | ✅ Yes      | On same subnet/network                    |
| ICMP (Ping)   | ICMP             | ✅ Yes      | Across subnets                            |
| TCP SYN       | TCP              | ✅ Yes      | Remote targets                            |
| TCP Connect   | TCP              | ❌ No       | Without root/admin access                 |

### 🔧 ARP (Address Resolution Protocol)
- Used to map IPs to MAC addresses
- Works only within the same subnet
- Nmap uses ARP to discover devices on local networks

### 🌐 TCP/IP Layers in Scanning
| Layer         | Protocols Used     |
|---------------|--------------------|
| Link Layer    | ARP                |
| Network Layer | ICMP               |
| Transport     | TCP, UDP           |

### 🔐 Privileged vs Unprivileged Scans
- Privileged = Root/Admin → can use ARP, ICMP, SYN scans
- Unprivileged = Can only use TCP Connect (slower, noisier)

## 🧪 Commands Practiced
```bash
nmap 10.0.0.1-10
nmap 10.0.0.1,10.0.0.5,10.0.0.10
nmap 10.0.0.0/24
nmap -iL list.txt
