# 📖 Networking Fundamentals Glossary

A quick-reference glossary for the **Networking Fundamentals** course and **CompTIA Network+ N10-009** study.

Use this file when you encounter an unfamiliar networking term or need a quick refresher.

---

# A

### AAA — Authentication, Authorization, and Accounting
A security framework used to control access to network resources.

- **Authentication:** Who are you?
- **Authorization:** What are you allowed to do?
- **Accounting:** What did you do?

### Access Point — AP
A network device that provides wireless devices access to a network.

### Access Port
A switch port normally assigned to a single VLAN and commonly used for endpoint devices.

### ACL — Access Control List
A set of rules used to permit or deny network traffic.

### APIPA — Automatic Private IP Addressing
An IPv4 address automatically assigned by Windows when a DHCP server cannot be reached.

APIPA range:

```text
169.254.0.0/16
```

Seeing a `169.254.x.x` address can be an important DHCP troubleshooting clue.

### ARP — Address Resolution Protocol
Used with IPv4 to discover the MAC address associated with an IP address on the local network.

Think:

```text
IPv4 Address
     ↓
ARP
     ↓
MAC Address
```

### ARP Table
A local cache containing learned IPv4-to-MAC-address mappings.

Windows command:

```text
arp -a
```

### Authentication
The process of verifying identity.

---

# B

### Bandwidth
The amount of data a network connection can theoretically carry over time.

Common measurements:

```text
Mbps
Gbps
```

### Baseline
A record of normal network behavior used for comparison during monitoring and troubleshooting.

Examples:

- Normal latency
- Typical bandwidth usage
- Normal CPU utilization
- Normal packet loss

### Broadcast
Network traffic intended for all devices within a broadcast domain.

### Broadcast Address
The final IPv4 address in a subnet, traditionally used to send traffic to all hosts in that subnet.

### Broadcast Domain
The group of devices that receive the same Layer 2 broadcast traffic.

Routers and VLANs can separate broadcast domains.

---

# C

### Cable Internet
Broadband Internet service delivered over cable-provider infrastructure.

### CIDR — Classless Inter-Domain Routing
A notation for specifying the network portion of an IP address.

Example:

```text
192.168.10.0/24
```

### Client
A device or application that requests a service from another system.

### Collision Domain
A network area in which Ethernet frame collisions could occur.

Modern switches create a separate collision domain for each switch port.

### Default Route
A route used when no more-specific route exists.

IPv4:

```text
0.0.0.0/0
```

### Copper Cable
Networking cable that carries electrical signals.

Common Ethernet examples include twisted-pair cabling.

---

# D

### Default Gateway
The Layer 3 device a host sends traffic to when the destination is outside its local subnet.

### DHCP — Dynamic Host Configuration Protocol
Automatically provides network configuration to clients.

Common information includes:

- IP address
- Subnet mask
- Default gateway
- DNS server

### DHCP Scope / Pool
The range and configuration from which a DHCP server provides addresses to clients.

### DHCP Lease
The temporary assignment of an IP configuration to a DHCP client.

### DHCP DORA
A simplified description of the DHCP process:

```text
Discover
   ↓
Offer
   ↓
Request
   ↓
Acknowledge
```

### DNS — Domain Name System
Translates names into IP addresses.

Example:

```text
server.example.com
        ↓
       DNS
        ↓
192.168.20.10
```

### DNS Record
An entry containing DNS information.

Common types include:

- A
- AAAA
- CNAME
- MX
- PTR

### DoS — Denial of Service
An attack intended to make a system or service unavailable.

### DDoS — Distributed Denial of Service
A denial-of-service attack originating from multiple systems or sources.

### DSL — Digital Subscriber Line
Internet connectivity delivered using telephone-line infrastructure.

### Duplex
Describes how devices transmit and receive data.

**Half-duplex:** One direction at a time.

**Full-duplex:** Both directions simultaneously.

---

# E

### Ethernet
A family of technologies widely used for wired LAN networking.

### Ethernet Frame
The Layer 2 data unit used by Ethernet.

It includes information such as:

- Source MAC
- Destination MAC
- EtherType
- Payload
- Error-detection information

### Encapsulation
The process of adding protocol information as data moves down the networking stack.

Conceptually:

```text
Data
 ↓
Segment
 ↓
Packet
 ↓
Frame
 ↓
Bits
```

### Encryption
Transforms information to protect it from unauthorized reading.

---

# F

### Failover
Automatically or manually moving service to a backup resource when the primary resource fails.

Example:

```text
Fiber ISP
    X
    ↓
5G Backup
```

### Fiber-Optic Cable
Cable that carries information using light.

Advantages can include:

- High bandwidth
- Long distance
- Resistance to electromagnetic interference

### Firewall
A security device or software system that permits or blocks network traffic based on configured rules.

### Full Tunnel VPN
A VPN configuration where most or all client traffic is routed through the VPN according to policy.

### Full-Duplex
Allows sending and receiving simultaneously.

---

# G

### Gateway
A device that connects networks. In normal endpoint configuration, "gateway" often refers to the default gateway.

### Gigabit Ethernet
Ethernet capable of approximately:

```text
1 Gbps
```

---

# H

### Half-Duplex
Communication in which transmission can occur in either direction, but not simultaneously.

### Host
A device with a network address that communicates on a network.

### Hostname
A human-readable name assigned to a device.

### HTTP — Hypertext Transfer Protocol
Protocol used for web communication.

Default port:

```text
TCP 80
```

### HTTPS — Hypertext Transfer Protocol Secure
Encrypted web communication using TLS.

Default port:

```text
TCP 443
```

---

# I

### ICMP — Internet Control Message Protocol
Used for network status and diagnostic messages.

`ping` uses ICMP.

### IEEE
Organization responsible for many networking standards.

Examples include:

```text
802.3 — Ethernet
802.11 — Wi-Fi
802.1Q — VLAN tagging
```

### Interface
A network connection on a device.

Examples:

- Ethernet port
- Wireless adapter
- Router interface
- Virtual interface

### IP Address
A logical address used to identify a device/interface on an IP network.

### IPv4
Internet Protocol version 4.

Uses:

```text
32-bit addresses
```

Example:

```text
192.168.10.25
```

### IPv6
Internet Protocol version 6.

Uses:

```text
128-bit addresses
```

Example:

```text
2001:db8::10
```

### ISP — Internet Service Provider
A company that provides Internet or WAN connectivity.

---

# J

### Jitter
Variation in network packet delay over time.

Especially important for:

- VoIP
- Video calls
- Real-time applications

---

# L

### LAN — Local Area Network
A network covering a relatively limited geographic area.

Examples:

- Office
- Building
- Home
- Campus

### Latency
The delay experienced while network traffic travels between points.

Commonly measured in:

```text
milliseconds — ms
```

### Layer 2
The Data Link layer of the OSI model.

Common concepts:

- MAC addresses
- Ethernet frames
- Switching
- VLANs

### Layer 3
The Network layer of the OSI model.

Common concepts:

- IP addresses
- Routing
- Routers

### Link-Local Address
An address used for communication on the local link.

IPv4 APIPA addresses use:

```text
169.254.0.0/16
```

IPv6 also supports link-local addressing.

### Loopback Address

IPv4:

```text
127.0.0.1
```

Commonly used to test the local TCP/IP stack.

IPv6:

```text
::1
```

---

# M

### MAC Address
A Layer 2 hardware/interface identifier used in Ethernet networking.

Example:

```text
00:1A:2B:3C:4D:5E
```

### MAC Address Table
A table maintained by a switch mapping MAC addresses to switch ports.

Cisco command:

```text
show mac address-table
```

### Malware
Malicious software intended to damage, disrupt, spy on, or gain unauthorized access to systems.

### MAN — Metropolitan Area Network
A network covering an area larger than a typical LAN but smaller than many WAN deployments.

### Metro Ethernet
Provider Ethernet connectivity used to connect locations across a metropolitan or provider network.

### MFA — Multi-Factor Authentication
Authentication using more than one factor.

Example:

```text
Password
+
Authenticator Approval
```

### MIB — Management Information Base
A structured collection of managed information used with SNMP.

### MPLS — Multiprotocol Label Switching
A provider networking technology commonly used for WAN connectivity.

### MTU — Maximum Transmission Unit
The largest packet/frame payload size a network technology can carry without requiring fragmentation or another handling method.

---

# N

### NAT — Network Address Translation
Translates one IP address or set of addresses into another.

Frequently used to allow private IPv4 devices to communicate with the Internet.

### Network Address
The first address representing an IPv4 subnet.

Example:

```text
192.168.10.0/24
```

Network address:

```text
192.168.10.0
```

### NIC — Network Interface Card / Controller
Hardware that allows a device to connect to a network.

### NTP — Network Time Protocol
Used to synchronize clocks between networked systems.

Default port:

```text
UDP 123
```

### `nslookup`
A command-line tool used to query DNS.

Example:

```text
nslookup example.com
```

---

# O

### OID — Object Identifier
Identifies a particular managed object in SNMP.

### OSI Model
A seven-layer conceptual networking model.

```text
7 Application
6 Presentation
5 Session
4 Transport
3 Network
2 Data Link
1 Physical
```

---

# P

### Packet
The Layer 3 data unit commonly associated with IP.

### Packet Loss
Occurs when packets fail to reach their intended destination.

### Patch Panel
A passive cabling component used to organize network cable terminations.

### PAT — Port Address Translation
A form of NAT allowing multiple private devices to share a public IPv4 address by using transport-layer port information.

Sometimes called:

> NAT overload

### Phishing
An attempt to trick users into revealing information or performing a harmful action.

### Physical Layer
Layer 1 of the OSI model.

Includes concepts such as:

- Cables
- Connectors
- Signals
- Radio
- Physical interfaces

### Ping
A network diagnostic tool commonly using ICMP echo messages to test reachability and measure round-trip time.

Example:

```text
ping 8.8.8.8
```

### PoE — Power over Ethernet
Provides electrical power over Ethernet cabling to supported devices.

Common examples:

- Wireless APs
- IP phones
- Cameras

### Port — Physical
A physical connection on a network device.

Example:

```text
Switch Ethernet Port
```

### Port — Logical
A TCP or UDP number used to identify a network service/application.

Example:

```text
HTTPS — TCP 443
```

### Private IPv4 Address
An IPv4 address from one of the RFC 1918 private ranges:

```text
10.0.0.0/8

172.16.0.0/12

192.168.0.0/16
```

### Protocol
A defined set of rules used for communication between systems.

### Public IP Address
An IP address that can be globally routable on the public Internet, subject to routing and policy.

---

# Q

### QoS — Quality of Service
Techniques used to classify, prioritize, or manage network traffic.

Often important for:

- Voice
- Video
- Real-time traffic

---

# R

### Redundancy
Using additional devices, connections, or resources so service can continue after a failure.

### RJ45
Common informal name for the modular connector associated with twisted-pair Ethernet cabling.

### Rogue Access Point
An unauthorized wireless access point connected to or impersonating an organization's network.

### Rogue Device
An unauthorized device connected to a network.

### Route
Information describing how to reach a destination network.

### Router
A Layer 3 device that forwards packets between networks.

### Routing Table
A collection of routes used by a router or host to determine where packets should be sent.

Windows:

```text
route print
```

Cisco:

```text
show ip route
```

---

# S

### SD-WAN — Software-Defined Wide Area Network
A WAN approach that can centrally manage and dynamically select between multiple network paths.

### Segment
The Layer 4 data unit commonly associated with TCP.

### Server
A system that provides services to clients.

### SFP — Small Form-factor Pluggable
A modular transceiver used in network equipment for different types of network connections.

### SLA — Service-Level Agreement
An agreement defining service commitments between a provider and customer.

### SNMP — Simple Network Management Protocol
Used to monitor and manage information from network devices.

### SNMP Trap
An unsolicited notification sent from an SNMP-enabled device to a management system.

### SNMPv3
A version of SNMP supporting stronger security features, including authentication and encryption options.

### Split Tunnel
A VPN configuration where selected traffic uses the VPN while other traffic can use the client's local Internet path.

### SSH — Secure Shell
Encrypted remote command-line management protocol.

Default port:

```text
TCP 22
```

### SSID — Service Set Identifier
The name used to identify a wireless network.

### Static IP Address
An IP address manually configured or otherwise intended to remain fixed.

### Static Route
A route manually configured by an administrator.

### Subnet
A logical subdivision of an IP network.

### Subnet Mask
Used with IPv4 to determine which portion of an address represents the network and host.

Example:

```text
255.255.255.0
```

equals:

```text
/24
```

### Switch
A Layer 2 device that forwards Ethernet frames using MAC addresses.

### Syslog
A standard used to generate and centralize event/log messages from systems and network devices.

---

# T

### TCP — Transmission Control Protocol
A connection-oriented transport protocol that provides reliable, ordered delivery.

### TCP/IP
The protocol suite used by modern IP networks and the Internet.

### Telnet
An older remote terminal protocol that does not provide encryption.

Default:

```text
TCP 23
```

Prefer:

> **SSH**

### Throughput
The actual amount of useful data successfully transferred over a connection over time.

### `tracert`
Windows command used to display the path toward a destination.

Example:

```text
tracert 8.8.8.8
```

### Trunk Port
A switch connection configured to carry traffic for multiple VLANs.

### TTL — Time to Live
An IPv4 field that limits how long a packet can continue through routed networks.

### Twisted Pair
Copper cabling in which wire pairs are twisted to help reduce interference.

---

# U

### UDP — User Datagram Protocol
A connectionless transport protocol with lower overhead than TCP but without TCP's built-in reliability mechanisms.

### Unicast
Communication from one sender to one specific destination.

### Uplink
A connection from one network device toward another part of the network, often toward an upstream switch or router.

### Uptime
The amount of time a device or service has remained operational.

---

# V

### VLAN — Virtual Local Area Network
Logically divides a switched network into separate broadcast domains.

Example:

```text
VLAN 10 — Employees

VLAN 20 — Servers

VLAN 50 — Guests
```

### VLAN Tagging
Adds VLAN identification information to Ethernet frames.

Common standard:

```text
IEEE 802.1Q
```

### VLSM — Variable Length Subnet Masking
Using different subnet sizes within the same address space to better match host requirements.

### VoIP — Voice over Internet Protocol
Voice communication carried over IP networks.

### VPN — Virtual Private Network
Creates a protected logical connection over another network such as the Internet.

### Site-to-Site VPN
Connects networks at separate locations.

### Remote-Access VPN
Connects an individual remote client to organizational resources.

---

# W

### WAN — Wide Area Network
A network connecting locations across larger geographic distances.

### Wi-Fi
Wireless LAN technology based on IEEE 802.11 standards.

### WPA2
A wireless security standard commonly used to secure Wi-Fi networks.

### WPA3
A newer wireless security standard providing improvements over WPA2.

### WAP
Wireless Access Point.

Usually shortened to:

> **AP**

---

# 🔢 Common Ports

| Protocol | Port | Transport | Purpose |
|---|---:|---|---|
| FTP | 20/21 | TCP | File transfer |
| SSH | 22 | TCP | Secure remote administration |
| Telnet | 23 | TCP | Insecure remote administration |
| SMTP | 25 | TCP | Email transfer |
| DNS | 53 | TCP/UDP | Name resolution |
| DHCP | 67/68 | UDP | IP configuration |
| HTTP | 80 | TCP | Web |
| POP3 | 110 | TCP | Email retrieval |
| NTP | 123 | UDP | Time synchronization |
| IMAP | 143 | TCP | Email retrieval |
| SNMP | 161 | UDP | Network management |
| SNMP Trap | 162 | UDP | SNMP notifications |
| HTTPS | 443 | TCP | Secure web |
| SMB | 445 | TCP | Windows file sharing |
| RDP | 3389 | TCP/UDP | Remote Desktop |

---

# 🧠 Final Reminder

Do not try to memorize networking as hundreds of unrelated definitions.

Connect the concepts:

```text
DEVICE
  ↓
NIC
  ↓
MAC ADDRESS
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
WAN
  ↓
DESTINATION
```

Then remember the supporting services:

```text
DHCP
→ Gives devices their network configuration

DNS
→ Resolves names

ARP
→ Maps local IPv4 addresses to MAC addresses

ROUTING
→ Finds paths between networks

NAT
→ Translates addresses

FIREWALL / ACL
→ Controls traffic

SNMP
→ Helps monitor devices

SYSLOG
→ Records events
```

Networking becomes much easier when you understand how the pieces fit together instead of memorizing each term in isolation.

---

# 📚 Course Navigation

➡️ **[Return to Main README](../README.md)**

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**