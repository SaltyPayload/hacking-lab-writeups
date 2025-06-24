# 🌐 Networking Fundamentals – Comprehensive Notes

> Combined insights from TryHackMe + Hack The Box Academy

---

## 🧱 Network Basics

### ❓ What Is a Network?

* A group of connected devices that share data/resources.
* Includes LANs, WANs, the internet, etc.

### 🖧 LAN vs WAN

* **LAN (Local Area Network):** Short-range (e.g., office, home)
* **WAN (Wide Area Network):** Long-range, connects multiple LANs

### 🌐 IP Addressing

* Every device has an **IP Address** (like a phone number).
* **IPv4:** 32-bit (e.g., 192.168.0.1)
* **IPv6:** 128-bit (e.g., `fe80::1ff:fe23:4567:890a`) – more space

### 🎯 Public vs Private IPs

* **Public IPs:** Seen on the internet, assigned by ISPs
* **Private IPs:** Local use only (192.168.x.x, 10.x.x.x, 172.16–31.x.x)
* Use `ip a` or `ifconfig` to view your IP

### 🔁 MAC Address

* Hardware identifier for NICs
* Format: `00:11:22:33:44:55`
* Used at the data link layer

---

## 🧮 Subnetting & Addressing

### 🧠 Subnet Masks & CIDR

* Define how many addresses belong to a network
* `/24` = 255.255.255.0 → 256 total addresses (254 usable)
* `/16` = 255.255.0.0 → 65,536 total (65,534 usable)

### 🔢 Binary Breakdown

* Convert IP/subnet to binary to calculate networks
* First IP = network address; Last = broadcast address

### 🛠 Useful Commands

```bash
ipcalc 192.168.1.0/24
nmap -sn 192.168.1.0/24  # Ping sweep
```

---

## ⚙️ Networking Devices

| Device       | Function                                 |
| ------------ | ---------------------------------------- |
| Router       | Connects networks (LAN → WAN)            |
| Switch       | Connects devices in a LAN (MAC-aware)    |
| Hub          | Broadcasts all traffic to all ports      |
| Modem        | Modulates digital → analog (ISP link)    |
| Firewall     | Filters traffic (inbound/outbound rules) |
| Access Point | Wireless LAN coverage                    |

---

## 📬 OSI Model (7 Layers)

1. **Application** – User access (HTTP, SSH)
2. **Presentation** – Formats data (encryption, compression)
3. **Session** – Establishes/ends connections
4. **Transport** – TCP/UDP, ports, reliability
5. **Network** – Routing, IP addressing
6. **Data Link** – MAC addressing, switches
7. **Physical** – Cables, NICs, bits on the wire

**Mnemonic**: "Please Do Not Throw Sausage Pizza Away"

Also know: **TCP/IP model (4 layers)** – Application, Transport, Internet, Link

---

## 🌊 Protocols

### 💬 Common Protocols

| Protocol | Port  | Use                        |
| -------- | ----- | -------------------------- |
| TCP      | —     | Reliable, connection-based |
| UDP      | —     | Unreliable, fast           |
| ICMP     | —     | Ping, diagnostics          |
| HTTP     | 80    | Unencrypted web traffic    |
| HTTPS    | 443   | Encrypted web traffic      |
| SSH      | 22    | Remote terminal access     |
| FTP      | 21    | File transfer              |
| DNS      | 53    | Domain resolution          |
| DHCP     | 67/68 | Dynamic IP assignment      |

### 🧠 Protocol Concepts

* **Three-way handshake** (TCP): SYN → SYN-ACK → ACK
* **UDP**: No handshake, used in streaming/games
* **Ports**: Numbered endpoints (0–65535)

  * 0–1023 = well-known
  * 1024–49151 = registered
  * 49152–65535 = dynamic/private

---

## 🛠️ Network Tools

### 🔎 Connectivity

```bash
ping <host>        # ICMP test
traceroute <host>  # Path taken to host
whois <domain>     # Domain info
```

### 🌐 DNS

```bash
dig example.com +short  # Get IP quickly
nslookup example.com    # Alt DNS tool
```

### 🛡 Port Scanning

```bash
nmap -sS -p- <target>        # Full TCP scan
nmap -sV -A <target>         # Detect services, OS
netstat -tuln                # Listening ports
ss -tuln                     # Faster alternative
```

### 🔬 Packet Capture

* Tool: **Wireshark**, **tcpdump**
* Filters:

  * `ip.addr == 10.10.10.10`
  * `tcp.port == 80`
  * `http.request`

---

## 🧪 Exploitable Concepts

### ⚠️ Attacks

* **MITM** – Intercepts traffic between devices
* **ARP Spoofing** – Fake MAC/IP resolution
* **DNS Poisoning** – Redirect domains
* **Sniffing** – Capture unencrypted data (Wireshark)
* **Port Knocking** – Hidden service activation

### 🛡 Defense

* Use HTTPS, SSH
* VPN for secure tunneling
* DNS over HTTPS (DoH)
* MAC filtering
* Disable unused services/ports

---

## 🧰 Practical Examples

### 🔐 SSH

```bash
ssh user@ip -p 22
ssh -i id_rsa user@ip
```

### 📤 SCP File Transfer

```bash
scp file.txt user@ip:/path/to/destination
scp -i id_rsa file user@ip:/path
```

### 🧱 Editing Hosts File (Linux)

```bash
sudo nano /etc/hosts
# 127.0.0.1 mycoolsite.local
```

### 🔥 Firewall Rules (ufw)

```bash
sudo ufw enable
sudo ufw allow 22/tcp
sudo ufw status verbose
```

### 🛠 Curl & Wget

```bash
curl -s https://site.com
wget https://site.com/file.zip
```

### 📁 Mounting Shares

```bash
sudo mount -t nfs 10.10.10.10:/mnt/share /mnt
sudo mount -t cifs //<IP>/share /mnt -o user=guest
```

---

## 📌 Cheat Sheet Summary

* `ping`, `traceroute`, `nmap`, `whois`, `dig`, `netstat`, `ss`
* OSI & TCP/IP model fluency
* TCP vs UDP differences
* Port numbers and common services
* DNS, DHCP, ARP essentials
* SSH & SCP syntax
* Firewall basics (ufw)
* Wireshark filters
* Subnet masks and CIDR logic
* MITM, ARP spoofing, DNS spoofing defense

Let me know if you'd like this turned into a printable reference or linked to your GitHub learning journal.
