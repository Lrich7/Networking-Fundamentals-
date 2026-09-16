# 🧠 Networking Fundamentals Cheat Sheet

Quick-reference material for the **Networking Fundamentals** course and **CompTIA Network+ N10-009** study.

> Don't memorize everything at once. Learn how the pieces connect.

---

# 🧅 OSI Model

| Layer | Name | Think |
|---:|---|---|
| 7 | Application | User/network services |
| 6 | Presentation | Format, encryption, encoding |
| 5 | Session | Sessions/connections |
| 4 | Transport | TCP/UDP, ports |
| 3 | Network | IP, routing |
| 2 | Data Link | MAC, switching, VLANs |
| 1 | Physical | Cable, radio, signals |

Easy memory aid:

```text
All
People
Seem
To
Need
Data
Processing
```

Top → Bottom:

```text
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

---

# 📦 Encapsulation

```text
APPLICATION
   Data
    ↓
TRANSPORT
 Segment
    ↓
NETWORK
 Packet
    ↓
DATA LINK
 Frame
    ↓
PHYSICAL
  Bits
```

At the receiving device:

```text
Bits
 ↓
Frame
 ↓
Packet
 ↓
Segment
 ↓
Data
```

---

# 🔢 Layer Addressing

```text
Layer 2
MAC Address

Layer 3
IP Address

Layer 4
TCP / UDP Port
```

Think:

```text
IP
= Which device/network?

MAC
= Which local interface?

PORT
= Which service/application?
```

---

# 🖥️ Same-Subnet Communication

PC-A:

```text
192.168.10.10/24
```

PC-B:

```text
192.168.10.20/24
```

Both are in:

```text
192.168.10.0/24
```

Communication:

```text
PC-A
 ↓
ARP
 ↓
PC-B MAC
 ↓
Switch
 ↓
PC-B
```

The default gateway is not required to route this traffic between subnets because both hosts are local.

---

# 🌎 Different-Subnet Communication

PC:

```text
192.168.10.10/24
```

Server:

```text
192.168.20.10/24
```

Communication:

```text
PC
 ↓
Default Gateway
 ↓
Router
 ↓
192.168.20.0/24
 ↓
Server
```

Rule:

> **Local destination → communicate locally**

> **Remote destination → send toward default gateway**

---

# 🏠 Private IPv4 Ranges

Memorize these:

```text
10.0.0.0/8
```

```text
172.16.0.0/12
```

which covers:

```text
172.16.0.0
through
172.31.255.255
```

and:

```text
192.168.0.0/16
```

---

# 🚨 APIPA

```text
169.254.0.0/16
```

If a Windows PC unexpectedly has:

```text
169.254.x.x
```

think:

> **DHCP problem**

Check:

```text
DHCP Server

VLAN

Cable/Wi-Fi

DHCP Relay

Switch Port

Network Connectivity
```

---

# 🔁 Loopback

IPv4:

```text
127.0.0.1
```

IPv6:

```text
::1
```

Useful for testing the local TCP/IP stack.

---

# 🧮 CIDR / SUBNET QUICK TABLE

| CIDR | Mask | Total Addresses | Usable IPv4 Hosts* |
|---:|---|---:|---:|
| /24 | 255.255.255.0 | 256 | 254 |
| /25 | 255.255.255.128 | 128 | 126 |
| /26 | 255.255.255.192 | 64 | 62 |
| /27 | 255.255.255.224 | 32 | 30 |
| /28 | 255.255.255.240 | 16 | 14 |
| /29 | 255.255.255.248 | 8 | 6 |
| /30 | 255.255.255.252 | 4 | 2 |

\*Using traditional IPv4 subnet host calculations.

---

# 🧠 Host Formula

Traditional IPv4 subnet calculation:

```text
2^h - 2
```

where:

```text
h = host bits
```

Example `/26`:

```text
32 - 26
=
6 host bits
```

```text
2^6
=
64 total addresses
```

Traditional usable hosts:

```text
64 - 2
=
62
```

---

# 🧮 Block Size Trick

Use:

```text
256 - subnet mask octet
```

Example:

```text
/27
=
255.255.255.224
```

```text
256 - 224
=
32
```

Networks occur every:

```text
32
```

Addresses:

```text
192.168.1.0

192.168.1.32

192.168.1.64

192.168.1.96

192.168.1.128

192.168.1.160

192.168.1.192

192.168.1.224
```

---

# 🧮 Example `/27`

Subnet:

```text
192.168.1.64/27
```

Block size:

```text
32
```

Next network:

```text
192.168.1.96
```

Therefore:

```text
Network:
192.168.1.64

First Host:
192.168.1.65

Last Host:
192.168.1.94

Broadcast:
192.168.1.95
```

---

# 🌐 IPv6 Quick Reference

IPv6 addresses are:

```text
128 bits
```

Example:

```text
2001:db8:abcd:1::10
```

Common concepts:

```text
::1
Loopback

fe80::/10
Link-local

/64
Common LAN prefix size
```

IPv6 does not use broadcast the way IPv4 does.

It makes extensive use of:

> **Multicast**

---

# 🔄 DHCP

Think:

> **Automatically configure the client.**

Common information:

```text
IP Address

Subnet Mask

Default Gateway

DNS Server
```

DORA:

```text
DISCOVER
   ↓
OFFER
   ↓
REQUEST
   ↓
ACKNOWLEDGE
```

Ports:

```text
UDP 67
UDP 68
```

---

# 📛 DNS

Think:

> **Name → IP**

Example:

```text
intranet.company.local
          ↓
         DNS
          ↓
192.168.20.10
```

Port:

```text
TCP/UDP 53
```

Troubleshooting clue:

```text
IP works
+
Hostname fails
=
Investigate DNS
```

---

# 📬 Common DNS Records

| Record | Purpose |
|---|---|
| A | Name → IPv4 |
| AAAA | Name → IPv6 |
| CNAME | Alias |
| MX | Mail server |
| PTR | Reverse lookup |

---

# 🔍 ARP

Think:

> **IPv4 → local MAC**

Windows:

```text
arp -a
```

---

# 🔀 SWITCHING

A switch primarily operates at:

> **OSI Layer 2**

It learns:

```text
Source MAC Address
        ↓
Incoming Port
```

and builds a:

> **MAC Address Table**

Cisco:

```text
show mac address-table
```

---

# 📢 Broadcast

A Layer 2 broadcast is forwarded throughout the applicable:

> **Broadcast domain**

VLANs divide a switched network into separate broadcast domains.

---

# 🧱 VLAN

Think:

> **One physical switch → multiple logical networks**

Example:

```text
VLAN 10
Employees

VLAN 20
Servers

VLAN 30
Printers

VLAN 50
Guests

VLAN 99
Management
```

---

# 🔌 Access Port vs. Trunk

## Access

Typically carries one VLAN for an endpoint.

```text
PC
 │
 ▼
ACCESS PORT
 │
VLAN 10
```

## Trunk

Carries multiple VLANs.

```text
SWITCH
  ║
  ║ VLAN 10
  ║ VLAN 20
  ║ VLAN 50
  ║ VLAN 99
  ║
SWITCH / ROUTER
```

Standard:

```text
802.1Q
```

---

# 🛣️ ROUTING

Routers connect:

> **Different IP networks**

A router checks its:

> **Routing table**

Cisco:

```text
show ip route
```

Windows:

```text
route print
```

---

# 🚪 Default Gateway

Think:

> **Exit from my subnet**

Example:

```text
PC:
192.168.10.25

Gateway:
192.168.10.1
```

Traffic to:

```text
192.168.10.50
```

is local.

Traffic to:

```text
192.168.20.50
```

needs Layer 3 routing.

---

# 🛣️ Default Route

IPv4:

```text
0.0.0.0/0
```

Think:

> **If I don't know a more-specific route, send it here.**

Cisco example:

```text
ip route 0.0.0.0 0.0.0.0 <next-hop>
```

---

# 🔄 NAT / PAT

Private network:

```text
192.168.10.0/24
```

Internet:

```text
Public IP
```

NAT translates between address spaces.

PAT allows many internal hosts to share a public IPv4 address using port information.

---

# 📡 WI-FI

Common Wi-Fi generations you may encounter:

| IEEE | Wi-Fi Name |
|---|---|
| 802.11n | Wi-Fi 4 |
| 802.11ac | Wi-Fi 5 |
| 802.11ax | Wi-Fi 6 / 6E |
| 802.11be | Wi-Fi 7 |

---

# 📡 2.4 GHz vs. 5 GHz vs. 6 GHz

| | 2.4 GHz | 5 GHz | 6 GHz |
|---|---|---|---|
| Range | Generally longer | Generally shorter than 2.4 | Generally shorter |
| Interference | Often higher | Often lower | Lower legacy-device congestion |
| Channel availability | Limited | More | Much more spectrum |
| Legacy support | Excellent | Good | Requires newer devices |

Actual performance depends on the environment, equipment, channel width, obstacles, interference, and client capabilities.

---

# 📶 2.4 GHz Channels

In the United States, commonly used non-overlapping 20 MHz channels are:

```text
1

6

11
```

Useful memory:

> **1 — 6 — 11**

---

# 📡 SSID

SSID means:

> **Wireless network name**

Example:

```text
Northstar-Corp
```

---

# 🔐 Wireless Security

Prefer modern secure options such as:

```text
WPA2
WPA3
```

where appropriate and supported.

Avoid obsolete/insecure technologies such as:

```text
WEP
```

---

# 🔌 CABLING

Common twisted-pair categories:

| Cable | Common Association |
|---|---|
| Cat 5e | Gigabit Ethernet |
| Cat 6 | Gigabit; higher rates at supported distances |
| Cat 6A | 10 Gigabit Ethernet up to standard channel distances |

Exact supported speeds and distances depend on the Ethernet standard and installation.

---

# 💡 Fiber

Two broad types:

```text
Multimode Fiber
```

and:

```text
Single-Mode Fiber
```

General memory:

```text
Multimode
→ Shorter distances

Single-mode
→ Longer distances
```

---

# ⚡ PoE

PoE means:

> **Power over Ethernet**

Common devices:

```text
Wireless AP

IP Phone

Security Camera
```

Data + power can travel over the Ethernet connection when supported.

---

# 🌎 WAN

Think:

> **Connect networks over distance**

Examples:

```text
Internet

Fiber

Cable

Cellular

Satellite

Dedicated Circuit

Metro Ethernet

MPLS

SD-WAN
```

---

# 🔄 WAN Redundancy

Example:

```text
             Firewall
              /    \
             /      \
          Fiber      5G
          ISP 1     ISP 2
```

If Fiber fails and 5G takes over:

> **Failover**

---

# 🔐 VPN

Two major concepts:

## Site-to-Site

```text
Office A
   │
Firewall
   ║
   ║ VPN
   ║
Firewall
   │
Office B
```

Connects:

> **Networks**

## Remote Access

```text
Laptop
  │
Internet
  │
 VPN
  │
Company
```

Connects:

> **Individual remote users**

---

# 🔀 Split vs. Full Tunnel

## Split Tunnel

```text
Corporate Traffic
      ↓
     VPN

Internet Traffic
      ↓
Local Internet
```

## Full Tunnel

```text
Most / All Traffic
       ↓
      VPN
       ↓
Company Network
```

---

# 📊 NETWORK PERFORMANCE

Memorize the difference:

### Bandwidth

> **Capacity**

### Throughput

> **Actual data transferred**

### Latency

> **Delay**

### Jitter

> **Variation in delay**

### Packet Loss

> **Packets that don't arrive**

---

# ☎️ Voice / Video Problems

If users report:

```text
Choppy Voice

Frozen Video

Dropouts
```

investigate:

```text
Latency

Jitter

Packet Loss

Congestion

Upload Capacity

Wi-Fi Quality
```

Do not look only at download speed.

---

# 🔐 NETWORK SECURITY

Remember the:

> **CIA Triad**

```text
Confidentiality

Integrity

Availability
```

---

# 🧱 Segmentation

Example:

```text
Employees
VLAN 10

Servers
VLAN 20

Guests
VLAN 50

Management
VLAN 99
```

Then control traffic using:

```text
ACLs

Firewall Rules

Routing Policy
```

---

# 📋 ACL

ACL:

> **Access Control List**

Think:

```text
PERMIT

or

DENY
```

---

# 🔑 AAA

```text
Authentication
→ Who are you?

Authorization
→ What can you do?

Accounting
→ What did you do?
```

---

# 🔒 Secure Management

Prefer:

```text
SSH
```

instead of:

```text
Telnet
```

Prefer:

```text
HTTPS
```

instead of unencrypted:

```text
HTTP
```

for management interfaces when supported.

Prefer:

```text
SNMPv3
```

over older SNMP versions when security requirements and device support allow.

---

# 👀 MONITORING

Common things to monitor:

```text
Device Status

Interface Status

Bandwidth

Latency

Packet Loss

CPU

Memory

Errors

WAN Links

VPN Tunnels
```

---

# 📏 Baseline

Think:

> **What does normal look like?**

Example:

```text
Latency:
Normally 20 ms

Today:
150 ms
```

The baseline makes the abnormal behavior obvious.

---

# 📡 SNMP

```text
SNMP
=
Simple Network Management Protocol
```

Used for:

> **Network monitoring and management information**

Common ports:

```text
UDP 161
SNMP

UDP 162
SNMP Trap
```

---

# 📝 Syslog

Think:

> **Centralized logs**

Example:

```text
Router ───┐
Switch ───┼──► Syslog Server
Firewall ─┘
```

---

# 🧰 WINDOWS COMMAND CHEAT SHEET

### Full IP Configuration

```text
ipconfig /all
```

### Release DHCP Lease

```text
ipconfig /release
```

### Renew DHCP Lease

```text
ipconfig /renew
```

### Clear DNS Cache

```text
ipconfig /flushdns
```

### Test Local TCP/IP

```text
ping 127.0.0.1
```

### Test Gateway

```text
ping <gateway>
```

### Test Internet IP

```text
ping 8.8.8.8
```

### Continuous Ping

```text
ping 8.8.8.8 -t
```

Stop:

```text
Ctrl + C
```

### Trace Route

```text
tracert 8.8.8.8
```

### Path Analysis

```text
pathping 8.8.8.8
```

### DNS Query

```text
nslookup example.com
```

### ARP Table

```text
arp -a
```

### Routing Table

```text
route print
```

### Connections / Ports

```text
netstat -ano
```

---

# 💻 POWERSHELL QUICK COMMANDS

Network adapters:

```text
Get-NetAdapter
```

IP configuration:

```text
Get-NetIPConfiguration
```

IP addresses:

```text
Get-NetIPAddress
```

Routes:

```text
Get-NetRoute
```

DNS configuration:

```text
Get-DnsClientServerAddress
```

Test connectivity:

```text
Test-NetConnection
```

Example:

```text
Test-NetConnection example.com -Port 443
```

---

# 🔀 CISCO SHOW COMMANDS

Interfaces:

```text
show ip interface brief
```

Interface details:

```text
show interfaces
```

VLANs:

```text
show vlan brief
```

Trunks:

```text
show interfaces trunk
```

MAC table:

```text
show mac address-table
```

Routes:

```text
show ip route
```

Current configuration:

```text
show running-config
```

Saved configuration:

```text
show startup-config
```

---

# 💾 SAVE CISCO CONFIG

```text
copy running-config startup-config
```

Shortcut commonly used:

```text
write memory
```

---

# 🔢 COMMON PORTS

These are worth knowing:

| Port | Protocol | Think |
|---:|---|---|
| 20/21 | FTP | File transfer |
| 22 | SSH | Secure administration |
| 23 | Telnet | Insecure administration |
| 25 | SMTP | Send/relay email |
| 53 | DNS | Name resolution |
| 67/68 | DHCP | Automatic addressing |
| 80 | HTTP | Web |
| 110 | POP3 | Retrieve email |
| 123 | NTP | Time |
| 143 | IMAP | Retrieve/manage email |
| 161 | SNMP | Monitoring |
| 162 | SNMP Trap | Notifications |
| 443 | HTTPS | Secure web |
| 445 | SMB | Windows file sharing |
| 3389 | RDP | Remote Desktop |

---

# 🧠 PORT MEMORY GROUPS

Instead of one giant list:

```text
WEB
80
443
```

```text
REMOTE ADMIN
22 SSH
23 Telnet
3389 RDP
```

```text
EMAIL
25 SMTP
110 POP3
143 IMAP
```

```text
NETWORK SERVICES
53 DNS
67/68 DHCP
123 NTP
```

```text
MONITORING
161 SNMP
162 SNMP Trap
```

---

# 🧰 TROUBLESHOOTING ORDER

When someone says:

> **"The network isn't working."**

Think:

```text
1. PHYSICAL
   ↓
2. LINK
   ↓
3. IP ADDRESS
   ↓
4. SUBNET MASK
   ↓
5. DEFAULT GATEWAY
   ↓
6. ROUTING
   ↓
7. DNS
   ↓
8. PORT / FIREWALL
   ↓
9. APPLICATION
```

---

# 🔍 QUICK TROUBLESHOOTING TEST

Start local and move outward:

```text
127.0.0.1
     ↓
My IP
     ↓
Default Gateway
     ↓
Remote IP
     ↓
DNS Name
     ↓
Application
```

---

# 🚨 COMMON SYMPTOMS

## `169.254.x.x`

Think:

```text
DHCP
```

---

## IP works, hostname doesn't

Think:

```text
DNS
```

---

## Same VLAN works, other VLAN doesn't

Think:

```text
Default Gateway

Routing

Trunk

Router Subinterface

ACL / Firewall
```

---

## One PC fails, everyone else works

Start with:

```text
PC

Cable

Wi-Fi

Switch Port

IP Configuration
```

---

## Entire VLAN fails

Investigate:

```text
VLAN Configuration

Trunk

Gateway

DHCP

Routing
```

---

## Entire office Internet fails

Investigate:

```text
Firewall

WAN Interface

ISP Equipment

ISP

Default Route
```

---

## Internet works, VPN doesn't

Investigate:

```text
VPN Client

Credentials

MFA

VPN Gateway

Certificate

Firewall Policy
```

---

## VPN connects, IP works, hostname doesn't

Think:

```text
DNS
```

---

## Voice is choppy but speed test looks fast

Think:

```text
Latency

Jitter

Packet Loss
```

---

# 🧭 TROUBLESHOOTING METHODOLOGY

Memorize the process:

```text
IDENTIFY
   ↓
THEORY
   ↓
TEST
   ↓
PLAN
   ↓
IMPLEMENT
   ↓
VERIFY
   ↓
DOCUMENT
```

Ask early:

> **Who is affected?**

```text
One User?

One VLAN?

One Building?

Everyone?
```

Scope can dramatically narrow the problem.

---

# ⭐ GOLDEN TROUBLESHOOTING RULES

### 1. Start with the simplest explanation.

### 2. Determine scope.

### 3. Find out what still works.

### 4. Change one meaningful variable at a time.

### 5. Do not assume the user's description identifies the cause.

### 6. Test before and after a change.

### 7. Verify the complete service, not just one ping.

### 8. Document what fixed it.

### 9. Escalate with evidence.

### 10. Follow the packet.

---

# 🧠 FOLLOW THE PACKET

When you're stuck, visualize:

```text
APPLICATION
     │
     ▼
END DEVICE
     │
     ▼
NIC
     │
     ▼
CABLE / WI-FI
     │
     ▼
SWITCH PORT
     │
     ▼
VLAN
     │
     ▼
DEFAULT GATEWAY
     │
     ▼
ROUTER / FIREWALL
     │
     ▼
WAN
     │
     ▼
REMOTE ROUTER
     │
     ▼
REMOTE VLAN
     │
     ▼
SERVER
     │
     ▼
APPLICATION
```

Then ask:

> **Where is the first point that expected behavior stops?**

That is one of the most useful habits you can develop in networking.

---

# 🎓 Network+ Last-Minute Reminders

Know the difference between:

```text
MAC vs IP

Switch vs Router

Access vs Trunk

TCP vs UDP

DHCP vs DNS

Private vs Public IP

Bandwidth vs Throughput

Bandwidth vs Latency

Latency vs Jitter

LAN vs WAN

Site-to-Site vs Remote-Access VPN

Split Tunnel vs Full Tunnel

Authentication vs Authorization

SNMP vs Syslog

Physical Problem vs Logical Problem
```

And when a question gives you several clues:

> **Use every clue.**

Network troubleshooting questions often tell you what is already working so you can eliminate entire portions of the network.

---

# 🏆 The Networking Mental Model

If you remember nothing else, remember this:

```text
DEVICE
   ↓
PHYSICAL CONNECTION
   ↓
SWITCH
   ↓
VLAN
   ↓
IP ADDRESS
   ↓
SUBNET
   ↓
DEFAULT GATEWAY
   ↓
ROUTER
   ↓
FIREWALL
   ↓
WAN
   ↓
REMOTE NETWORK
   ↓
SERVER
   ↓
APPLICATION
```

Supporting everything:

```text
DHCP → Configuration

DNS → Names

ARP → Local IPv4-to-MAC Resolution

ROUTING → Paths

NAT → Address Translation

ACL/FIREWALL → Traffic Control

SNMP → Monitoring

SYSLOG → Events

DOCUMENTATION → Knowledge

TROUBLESHOOTING → Finding where the path broke
```

If you understand that picture, you're no longer just memorizing networking terms.

You're thinking like a network technician.

---

# 📚 Course Navigation

➡️ **[Glossary](glossary.md)**

➡️ **[Return to Main README](../README.md)**

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**