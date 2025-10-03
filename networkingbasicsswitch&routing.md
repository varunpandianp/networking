what is switch and routing ? how systems communicate each other

default gateway ,DNS configuration on linux
## What is `/proc/sys/net/ipv4/ip_forward`?

- This file is part of the **Linux kernel parameters** (available via `/proc/sys/`).
- It controls whether the Linux system is allowed to **forward IP packets** between its network interfaces.

👉 In plain words:

- If **`ip_forward = 0`** → Linux will NOT forward packets (default).
- If **`ip_forward = 1`** → Linux will forward packets → your Linux system acts like a **router**.

Edit `/etc/sysctl.conf` and add:

```
net.ipv4.ip_forward=1

```

Apply changes:

```bash
sudo sysctl -p

```
``` BasicCommands``
ip link
ip addr
ip addr and 192.168.1.10/24 dev eth0
ip route
ip route add 192.168.1.0/24 via 192.168.2.1
cat /proc/sys/net/ipv4/ip_forward