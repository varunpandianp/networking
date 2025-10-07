# 🌟 Linux DNS Configuration Notes

## 📁 1️⃣ `/etc/resolv.conf`
**Purpose:**  
Defines which **DNS servers** your Linux system uses to resolve domain names (e.g., `google.com → 142.250.182.14`).

---

### 🧠 Key Points
- Used by the system resolver when DNS queries are made.  
- Can contain multiple nameserver entries (checked in order).  
- Typically auto-configured by DHCP or NetworkManager.

---

### 📄 Example:
```bash
$ cat /etc/resolv.conf
nameserver 192.168.1.1
nameserver 8.8.8.8
```
➡️ Linux will first query `192.168.1.1`, then `8.8.8.8` if the first fails.

---

### ⚙️ Common Use Cases
| Situation | Use |
|------------|-----|
| Set faster DNS manually | Use `nameserver 8.8.8.8` (Google) or `1.1.1.1` (Cloudflare) |
| Private/internal network | Point to internal DNS (e.g., `10.0.0.2`) |
| Debugging DNS issues | Temporarily change nameserver to test resolution |
| Containers/VMs | Configure internal DNS for service discovery |

---

### 🧮 Command Example
```bash
sudo bash -c 'echo "nameserver 8.8.8.8" > /etc/resolv.conf'
ping google.com
```

---

## 📁 2️⃣ `/etc/hosts`
**Purpose:**  
Local static file for mapping **hostnames → IP addresses**.  
Checked **before DNS queries** are made.

---

### 📄 Example:
```bash
127.0.0.1    localhost
192.168.1.10 myserver.local
127.0.0.1    myapp.dev
```

---

### ⚙️ Common Use Cases
| Situation | Use |
|------------|-----|
| Local testing | Map domains to local apps (e.g., `myapp.dev`) |
| Internal servers | Access private IPs by name (e.g., `myserver.local`) |
| DNS not available | Hardcode IPs for critical hosts |
| Block unwanted sites | Map domains to `127.0.0.1` |

---

### 🧮 Command Example
```bash
sudo nano /etc/hosts
# Add your entries, then test:
ping myserver.local
```

---

## 🔁 Resolution Order
When you access a domain (e.g., `ping example.com`):
1️⃣ Linux checks `/etc/hosts` first.  
2️⃣ If not found → checks DNS server from `/etc/resolv.conf`.  
3️⃣ If still not resolved → error (e.g., “unknown host”).

---

## ✅ Quick Summary Table

| File | Function | Priority | Real-Time Use |
|------|-----------|-----------|----------------|
| `/etc/hosts` | Local static name-to-IP mapping | Checked **first** | Local testing, overrides, blocking |
| `/etc/resolv.conf` | Lists DNS servers for external lookups | Checked **after hosts** | Internet name resolution, DNS config |

---

💡 **Pro Tip:**  
In DevOps or Cloud environments (like AWS, Docker, or Kubernetes):  
- `/etc/hosts` → used for service simulation or overrides  
- `/etc/resolv.conf` → used for internal DNS-based service discovery
