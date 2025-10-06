Study Notes  Contain 

OSI model (short notes)

IP, Subnet, Gateway explanation

Public vs private IP

DNS basics

Ports & services

# OSI Model (7 Layers – Think "All People Seem To Need Data Processing")

Physical Layer – Cables, switches, signals, bits (0/1).

Data Link Layer – MAC address, Ethernet, ARP.

Network Layer – IP addresses, routing, ICMP.

Transport Layer – TCP/UDP, port numbers, reliability.

Session Layer – Manages sessions, authentication, check-pointing.

Presentation Layer – Data formatting, encryption, compression.

Application Layer – End-user services (HTTP, FTP, DNS, SSH).

👉 TCP/IP model (practical use) is simplified into 4 layers:

Application, Transport, Internet, Network Access.

# IP, Subnet, Gateway

IP Address – Unique address of a device on a network (e.g., 192.168.1.10).

Subnet Mask – Defines the range of IPs inside the network (e.g., 255.255.255.0 means 256 IPs in the network, 254 usable).

Default Gateway – Router IP used to communicate outside your network (e.g., if your PC is 192.168.1.10, gateway may be 192.168.1.1).

Example:

PC IP: 192.168.1.10
Subnet: 255.255.255.0
Gateway: 192.168.1.1


This means → PC can talk to others in 192.168.1.x directly, but for internet/outside networks, it sends packets to 192.168.1.1.

# Public vs Private IP

Private IP – Used inside home/office networks. Not routable on internet.

IPv4 ranges:

10.0.0.0 – 10.255.255.255

172.16.0.0 – 172.31.255.255

192.168.0.0 – 192.168.255.255

Public IP – Assigned by ISP, unique on internet (e.g., 103.25.200.55).

👉 Private IP → NAT → Public IP → Internet.

# DNS Basics

DNS = Domain Name System – Converts domain names → IP addresses.

Example: www.google.com → 142.250.182.14.

Types of DNS Records:

A record → Domain to IPv4

AAAA record → Domain to IPv6

CNAME → Alias name

MX → Mail server

Works in hierarchy:

Local DNS cache

ISP DNS server

Root → TLD (.com, .org) → Authoritative server

# Ports & Services

Port = Logical door on a device for communication.

Range: 0 – 65535

Well-known ports (0–1023): Common services

Registered ports (1024–49151): Software vendors

Dynamic ports (49152–65535): Temporary sessions

# Common ports:

22 → SSH

80 → HTTP

443 → HTTPS

53 → DNS

25 → SMTP (mail)

3306 → MySQL

5432 → PostgreSQL

6379 → Redis