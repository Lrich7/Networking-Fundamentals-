# 📘 Lesson 10 — TCP, UDP, Ports, and Protocols

Welcome to **Lesson 10 of Networking Fundamentals**.

So far, you've learned how devices:

```text
Connect physically
        ↓
Use MAC addresses
        ↓
Receive IP addresses
        ↓
Determine local vs. remote networks
        ↓
Route traffic between networks
```

But knowing where a device is located isn't enough.

A computer may run many network services at the same time.

For example:

```text
Web Browser
Email
Teams
File Sharing
Remote Desktop
DNS
Cloud Applications
```

How does network traffic reach the correct application?

That's where:

> **TCP, UDP, ports, and application protocols**

become important.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain the purpose of TCP
- Explain the purpose of UDP
- Compare TCP and UDP
- Explain connection-oriented communication
- Understand the TCP three-way handshake
- Explain TCP acknowledgments
- Explain retransmission
- Understand TCP sequence numbers
- Explain ports
- Explain source and destination ports
- Understand ephemeral ports
- Understand sockets conceptually
- Recognize common port ranges
- Recognize common Network+ protocols and ports
- Explain DNS
- Explain DHCP
- Explain HTTP and HTTPS
- Explain SSH
- Explain RDP
- Explain SMB
- Explain SMTP, POP3, and IMAP
- Explain FTP and SFTP
- Explain SNMP
- Explain NTP
- Explain LDAP and LDAPS
- Use port information during troubleshooting

---

# 🎓 Network+ Focus

For **CompTIA Network+ N10-009**, you should know the purpose of common network services and be comfortable recognizing commonly associated ports.

Don't simply memorize:

```text
443 = HTTPS
```

Understand:

```text
HTTPS
    ↓
Secure Web Communication
    ↓
Usually TCP 443
```

That makes the number much easier to remember.

---

# 🧱 Where Are TCP and UDP?

Remember the TCP/IP model:

```text
Application
Transport
Internet
Network Access
```

TCP and UDP operate at the:

> **Transport Layer**

In the OSI model, that's:

> **Layer 4**

---

# 📦 TCP

TCP stands for:

> **Transmission Control Protocol**

TCP is:

> **Connection-oriented**

Before normal application data is exchanged, TCP establishes a logical connection between endpoints.

TCP is designed to provide reliable, ordered delivery.

---

# 🤝 TCP Three-Way Handshake

One of the most important TCP concepts is the:

> **Three-Way Handshake**

It works conceptually like this:

```text
CLIENT                         SERVER

SYN
  ---------------------------->

                    SYN-ACK
  <----------------------------

ACK
  ---------------------------->

       CONNECTION ESTABLISHED
```

Remember:

```text
SYN
SYN-ACK
ACK
```

---

# 🧠 What Does the Handshake Do?

The handshake allows the systems to establish a TCP session and synchronize information needed for communication.

Afterward:

```text
Application Data
      ↓
TCP Segments
      ↓
IP Packets
      ↓
Network
```

---

# 📬 TCP Acknowledgments

TCP can acknowledge received data.

Conceptually:

```text
Sender
   │
   │ Data
   ▼
Receiver
   │
   │ ACK
   ▼
Sender
```

If expected data isn't acknowledged, TCP can retransmit it.

---

# 🔢 TCP Sequence Numbers

TCP uses sequence information to help keep track of data.

Imagine receiving:

```text
Piece 1
Piece 2
Piece 4
Piece 3
```

TCP can help reconstruct the data in the correct order.

---

# 🔄 Retransmission

Suppose a TCP segment is lost.

TCP can detect that expected data hasn't been successfully acknowledged and retransmit it.

Conceptually:

```text
SEGMENT 1 → Received

SEGMENT 2 → LOST

SEGMENT 3 → Received

SEGMENT 2 → Retransmitted
```

This reliability comes with:

> **Additional overhead**

---

# 🌊 Flow and Congestion Control

TCP also includes mechanisms that help regulate how much data is transmitted and react to network conditions.

For Network+ fundamentals, remember:

> TCP prioritizes reliable, ordered delivery rather than simply sending data as quickly as possible.

---

# ⚡ UDP

UDP stands for:

> **User Datagram Protocol**

UDP is:

> **Connectionless**

UDP doesn't perform the TCP three-way handshake.

It has less protocol overhead.

---

# 📦 UDP Communication

Conceptually:

```text
Sender
   │
   │ Datagram
   ▼
Receiver
```

UDP itself doesn't guarantee:

- Delivery
- Ordering
- Retransmission

Applications can add their own reliability mechanisms if needed.

---

# 🏎️ Why Use UDP?

Sometimes:

> **Speed and low overhead**

are more important than TCP-style reliability.

Examples can include:

- Real-time voice/video
- Streaming
- DNS queries
- DHCP
- Online applications
- Certain VPN protocols
- Modern HTTP/3 using QUIC

---

# ⚖️ TCP vs. UDP

| Feature | TCP | UDP |
|---|---|---|
| Connection-oriented | Yes | No |
| Three-way handshake | Yes | No |
| Reliable delivery mechanisms | Yes | No |
| Ordered delivery | Yes | No |
| Retransmission | Yes | No |
| Overhead | Higher | Lower |
| Typical use | Reliability-focused | Low-latency/simple exchanges |

---

# ⚠️ Don't Oversimplify

You'll sometimes hear:

```text
TCP = Reliable
UDP = Fast
```

That's useful as a memory aid, but it's incomplete.

Modern protocols can build reliability, encryption, and session management on top of UDP.

A major example is:

> **QUIC**

which operates over UDP and is used by HTTP/3.

---

# 🚪 What Is a Port?

An IP address identifies:

> **A host/interface**

A port helps identify:

> **A network service or application endpoint**

Think:

```text
IP Address
=
Building Address

Port
=
Door
```

Example:

```text
192.168.10.50:443
```

means conceptually:

```text
Host:
192.168.10.50

Port:
443
```

---

# 🔢 Port Numbers

TCP and UDP port numbers range from:

```text
0 – 65535
```

They are commonly grouped into:

| Range | Name |
|---|---|
| 0–1023 | Well-Known Ports |
| 1024–49151 | Registered Ports |
| 49152–65535 | Dynamic / Private Ports |

---

# 🏷️ Well-Known Ports

Well-known ports are associated with common services.

Examples:

```text
22
SSH

53
DNS

80
HTTP

443
HTTPS
```

---

# 🔀 Source and Destination Ports

Suppose your computer connects to a web server.

The server listens on:

```text
TCP 443
```

Your computer typically uses a temporary high-numbered:

> **Ephemeral source port**

Example:

```text
CLIENT

192.168.10.25:53142

        ↓

SERVER

203.0.113.50:443
```

The client port doesn't need to be 443.

---

# 🔄 Return Traffic

The server responds:

```text
203.0.113.50:443

        ↓

192.168.10.25:53142
```

Notice the ports reverse direction.

---

# 🔌 Socket Concept

A network conversation can be identified using information such as:

```text
Source IP
Source Port
Destination IP
Destination Port
Transport Protocol
```

Example:

```text
TCP

192.168.10.25:53142
        ↓
203.0.113.50:443
```

This combination helps systems keep different network conversations separate.

---

# 🌐 HTTP

HTTP stands for:

> **Hypertext Transfer Protocol**

Common port:

```text
TCP 80
```

HTTP is traditionally used for unencrypted web traffic.

---

# 🔒 HTTPS

HTTPS is HTTP protected using TLS.

Common port:

```text
TCP 443
```

Modern web communication may also use HTTP/3 over QUIC:

```text
UDP 443
```

So don't assume every packet associated with HTTPS-era web browsing must be TCP.

---

# 🌎 DNS

DNS stands for:

> **Domain Name System**

DNS translates names such as:

```text
example.com
```

into IP addresses.

Common port:

```text
53
```

DNS commonly uses:

```text
UDP 53
```

for traditional queries.

DNS can also use:

```text
TCP 53
```

for situations requiring TCP, including certain larger responses and zone-transfer-related operations.

Modern encrypted DNS can also use other transports.

---

# 📡 DHCP

DHCP stands for:

> **Dynamic Host Configuration Protocol**

DHCP can automatically provide:

- IP address
- Subnet mask
- Default gateway
- DNS servers
- Other configuration

IPv4 DHCP commonly uses:

```text
UDP 67
UDP 68
```

Remember:

```text
Server = 67
Client = 68
```

---

# 🧠 DHCP DORA

A common IPv4 DHCP process is:

```text
Discover
Offer
Request
Acknowledge
```

Remember:

> **DORA**

---

# 🔐 SSH

SSH stands for:

> **Secure Shell**

Common port:

```text
TCP 22
```

SSH is commonly used for secure remote command-line administration.

Examples:

- Linux servers
- Network devices
- Firewalls
- Switches
- Routers

---

# 🖥️ RDP

RDP stands for:

> **Remote Desktop Protocol**

Common port:

```text
3389
```

RDP is used for remote Windows graphical desktop access.

Modern RDP can use both TCP and UDP on port 3389.

---

# 📁 SMB

SMB stands for:

> **Server Message Block**

Common direct-hosted SMB port:

```text
TCP 445
```

SMB is commonly used for:

- Windows file shares
- Shared folders
- Printer sharing
- Windows network resources

---

# ✉️ SMTP

SMTP stands for:

> **Simple Mail Transfer Protocol**

SMTP is used for:

> **Sending and transferring email**

Common ports you'll encounter include:

```text
TCP 25
TCP 587
```

Port 25 is traditionally associated with server-to-server SMTP.

Port 587 is commonly used for authenticated message submission.

You may also encounter:

```text
TCP 465
```

for implicit TLS SMTP submission.

---

# 📥 POP3

POP3 stands for:

> **Post Office Protocol version 3**

Traditional port:

```text
TCP 110
```

POP3 over TLS commonly uses:

```text
TCP 995
```

---

# 📬 IMAP

IMAP stands for:

> **Internet Message Access Protocol**

Traditional port:

```text
TCP 143
```

IMAP over TLS commonly uses:

```text
TCP 993
```

---

# 📤 FTP

FTP stands for:

> **File Transfer Protocol**

Traditional FTP uses:

```text
TCP 21
```

for control communication.

Traditional active-mode FTP uses:

```text
TCP 20
```

for server-side data connections.

FTP is not considered a secure method for transferring sensitive credentials/data by itself.

---

# 🔐 SFTP

SFTP stands for:

> **SSH File Transfer Protocol**

SFTP normally operates through:

```text
TCP 22
```

because it uses SSH.

---

# ⚠️ FTP vs. SFTP

Don't confuse:

```text
FTP
```

with:

```text
SFTP
```

They are different protocols.

SFTP isn't simply:

> FTP with encryption switched on.

It operates through SSH.

---

# ⏰ NTP

NTP stands for:

> **Network Time Protocol**

Common port:

```text
UDP 123
```

Accurate time is important for:

- Authentication
- Logging
- Certificates
- Kerberos
- Security investigations
- Event correlation

---

# 📊 SNMP

SNMP stands for:

> **Simple Network Management Protocol**

Common ports:

```text
UDP 161
UDP 162
```

Typically:

```text
161
=
Queries / Management

162
=
Traps / Notifications
```

SNMP can be used to monitor:

- Switches
- Routers
- Firewalls
- Printers
- Servers
- UPS devices
- Network equipment

---

# 📖 LDAP

LDAP stands for:

> **Lightweight Directory Access Protocol**

Common port:

```text
389
```

LDAP can use TCP and UDP in some contexts, though TCP is common for directory operations.

---

# 🔒 LDAPS

LDAP over TLS is commonly associated with:

```text
TCP 636
```

Think:

```text
LDAP
389

LDAPS
636
```

---

# 🖧 Telnet

Telnet commonly uses:

```text
TCP 23
```

Telnet provides remote terminal access but doesn't provide modern encrypted protection like SSH.

Prefer:

```text
SSH
TCP 22
```

where possible.

---

# 📋 Important Protocol & Port Table

| Protocol | Port | Transport | Purpose |
|---|---:|---|---|
| FTP Data | 20 | TCP | Traditional active FTP data |
| FTP Control | 21 | TCP | FTP control |
| SSH / SFTP | 22 | TCP | Secure remote access/file transfer |
| Telnet | 23 | TCP | Unencrypted remote terminal |
| SMTP | 25 | TCP | Mail transfer |
| DNS | 53 | UDP/TCP | Name resolution |
| DHCP Server | 67 | UDP | DHCP server |
| DHCP Client | 68 | UDP | DHCP client |
| HTTP | 80 | TCP | Web |
| POP3 | 110 | TCP | Mail retrieval |
| NTP | 123 | UDP | Time |
| IMAP | 143 | TCP | Mail access |
| SNMP | 161 | UDP | Network management |
| SNMP Trap | 162 | UDP | Notifications |
| LDAP | 389 | TCP/UDP | Directory services |
| HTTPS | 443 | TCP | Secure web |
| SMB | 445 | TCP | Windows file sharing |
| SMTP Submission | 587 | TCP | Mail submission |
| LDAPS | 636 | TCP | LDAP over TLS |
| IMAPS | 993 | TCP | Secure IMAP |
| POP3S | 995 | TCP | Secure POP3 |
| RDP | 3389 | TCP/UDP | Remote Desktop |

---

# 🧠 Port Memory Groups

Instead of memorizing random numbers, group them.

### Remote Administration

```text
22  SSH
23  Telnet
3389 RDP
```

### Web

```text
80   HTTP
443  HTTPS
```

### Email

```text
25   SMTP
587  SMTP Submission
110  POP3
995  POP3S
143  IMAP
993  IMAPS
```

### Infrastructure

```text
53   DNS
67   DHCP Server
68   DHCP Client
123  NTP
161  SNMP
162  SNMP Trap
```

### Directory / File

```text
389  LDAP
636  LDAPS
445  SMB
```

---

# 🖥️ Windows — View Connections

Run:

```cmd
netstat -ano
```

You may see:

```text
Local Address
Foreign Address
State
PID
```

Example:

```text
192.168.10.25:53142
203.0.113.50:443
ESTABLISHED
```

This tells you:

```text
Local Port:
53142

Remote Port:
443

State:
ESTABLISHED
```

---

# 🔷 PowerShell — Test a Port

PowerShell provides:

```powershell
Test-NetConnection
```

Example:

```powershell
Test-NetConnection example.com -Port 443
```

Look for:

```text
TcpTestSucceeded
```

---

# ⭐ Troubleshooting Value

Suppose:

```powershell
Test-NetConnection example.com -Port 443
```

returns:

```text
TcpTestSucceeded : False
```

That doesn't automatically tell you the exact cause.

Possibilities include:

- Server isn't listening
- Firewall blocks the connection
- Routing problem
- Proxy/security filtering
- Service outage
- Incorrect destination
- Local network restriction

The result is:

> **A clue**

not the entire diagnosis.

---

# 🧪 DNS Testing

Use:

```cmd
nslookup example.com
```

or PowerShell:

```powershell
Resolve-DnsName example.com
```

If:

```text
ping 8.8.8.8
```

works but:

```text
nslookup example.com
```

fails, investigate:

> **DNS**

---

# 🔬 Wireshark Filters

Useful filters include:

```text
tcp
```

```text
udp
```

```text
dns
```

```text
tcp.port == 443
```

```text
udp.port == 53
```

```text
tcp.flags.syn == 1
```

---

# 🛠️ Troubleshooting Scenario 1

A user can ping a server.

But:

```text
https://server
```

doesn't work.

Does successful ping prove HTTPS is working?

> **No**

Ping tests ICMP reachability.

HTTPS depends on an application service and transport connectivity, commonly TCP 443.

---

# 🛠️ Troubleshooting Scenario 2

A file server responds to ping.

Users can't access:

```text
\\FILESERVER\Shared
```

What should you investigate?

Among other things:

```text
SMB
TCP 445
```

---

# 🛠️ Troubleshooting Scenario 3

A Windows server responds to ping.

Remote Desktop fails.

Potential area to investigate:

```text
RDP
3389
```

along with:

- Firewall
- RDP service/configuration
- Permissions
- Routing
- Security policy

---

# 🛠️ Troubleshooting Scenario 4

Users can reach websites by IP address but not hostname.

Investigate:

```text
DNS
Port 53 / configured DNS path
```

---

# 🛠️ Troubleshooting Scenario 5

A switch should send monitoring data to your network management system.

Which protocol might be involved?

> **SNMP**

Commonly:

```text
UDP 161
UDP 162
```

---

# 🧠 Knowledge Check

### 1.

Which transport protocol uses the three-way handshake?

### 2.

What are the three steps?

### 3.

Which transport protocol is connectionless?

### 4.

What port is commonly associated with HTTPS?

### 5.

What port is commonly associated with SSH?

### 6.

What port is commonly associated with DNS?

### 7.

What ports are used by IPv4 DHCP?

### 8.

What port is commonly associated with SMB?

### 9.

What port is commonly associated with RDP?

### 10.

What port is commonly associated with NTP?

---

# ✅ Answers

1. **TCP**
2. **SYN → SYN-ACK → ACK**
3. **UDP**
4. **443**
5. **22**
6. **53**
7. **UDP 67 and 68**
8. **TCP 445**
9. **3389**
10. **UDP 123**

---

# 🎓 Network+ Challenge 1

A technician needs secure command-line access to a router.

Which should be used?

### A. TCP 23
### B. TCP 22
### C. UDP 53
### D. TCP 445

> **Answer: B — SSH / TCP 22**

---

# 🎓 Network+ Challenge 2

A client can't obtain an IPv4 address automatically.

Which ports may be relevant?

### A. 67/68
### B. 80/443
### C. 20/21
### D. 161/162

> **Answer: A — DHCP**

---

# 🎓 Network+ Challenge 3

A user can't access a Windows file share.

Which port is especially relevant?

### A. 22
### B. 53
### C. 445
### D. 3389

> **Answer: C — TCP 445**

---

# 🎓 Network+ Challenge 4

Which protocol is connectionless?

### A. TCP
### B. UDP

> **Answer: B — UDP**

---

# 🎓 Network+ Challenge 5

A packet capture shows:

```text
Client: 192.168.10.25:52741
Server: 203.0.113.20:443
```

Which port is probably the client's temporary source port?

> **52741**

Which is the server's service port?

> **443**

---

# 🎓 Network+ Challenge 6

Which protocol commonly uses UDP 123?

### A. DNS
### B. NTP
### C. HTTPS
### D. LDAP

> **Answer: B — NTP**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- TCP and UDP operate at the transport layer.
- TCP is connection-oriented.
- UDP is connectionless.
- TCP uses SYN → SYN-ACK → ACK.
- TCP provides reliability mechanisms such as acknowledgments and retransmissions.
- UDP has less transport-layer overhead.
- Ports identify application/service endpoints.
- Client applications commonly use ephemeral source ports.
- Port numbers range from 0–65535.
- DNS commonly uses port 53.
- DHCP uses UDP 67/68.
- HTTP commonly uses TCP 80.
- HTTPS commonly uses TCP 443.
- SSH uses TCP 22.
- SMB commonly uses TCP 445.
- RDP uses port 3389.
- NTP commonly uses UDP 123.
- SNMP commonly uses UDP 161/162.
- LDAP is associated with 389.
- LDAPS is associated with TCP 636.
- Port information is an important troubleshooting clue.
- Successful ping doesn't prove an application is working.

---

# 🧪 Next Step — Lab 10

Now you'll inspect real TCP/UDP connections, test ports, capture traffic in Wireshark, and configure network services in Packet Tracer.

➡️ **[Lab 10 — TCP, UDP, Ports, and Protocols](../labs/lab-10-tcp-udp-ports-protocols.md)**

---

# 📍 Course Progress

```text
🔵 PHASE 2 — ADDRESSING & COMMUNICATION

✅ Lesson 06 — Ethernet & MAC Addressing
✅ Lab 06

✅ Lesson 07 — IPv4 Addressing
✅ Lab 07

✅ Lesson 08 — Subnetting Fundamentals
✅ Lab 08

✅ Lesson 09 — IPv6 Fundamentals
✅ Lab 09

✅ Lesson 10 — TCP, UDP, Ports & Protocols
        ↓
🟡 NEXT: Lab 10
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**