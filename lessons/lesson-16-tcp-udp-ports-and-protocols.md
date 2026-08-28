# Lesson 16 — TCP, UDP, Ports, and Protocols

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain the purpose of the transport layer.
- Compare TCP and UDP.
- Explain source and destination ports.
- Recognize common well-known ports and protocols.
- Explain sockets and client/server conversations at a beginner level.
- Use Windows and PowerShell tools to inspect connections and listening ports.
- Use Wireshark and Packet Tracer to observe TCP and UDP traffic.
- Apply port knowledge during troubleshooting.

---

# The Transport Layer

TCP and UDP operate at the **Transport layer** of the OSI model.

```text
Layer 7 — Application
Layer 6 — Presentation
Layer 5 — Session
Layer 4 — Transport     ← TCP / UDP
Layer 3 — Network       ← IP
Layer 2 — Data Link     ← Ethernet
Layer 1 — Physical
```

IP gets traffic to the correct host.

TCP or UDP helps deliver traffic to the correct application or service on that host.

---

# TCP

**Transmission Control Protocol (TCP)** is connection-oriented.

TCP provides features including:

```text
Connection establishment
Sequencing
Acknowledgments
Retransmission
Flow control
Reliable ordered delivery
```

TCP is commonly used when reliable delivery matters.

Examples include:

```text
HTTPS
SSH
RDP
SMB
Many email protocols
```

---

# TCP Three-Way Handshake

A simplified TCP connection begins:

```text
Client                 Server

SYN  ----------------->
     <------------- SYN-ACK
ACK  ----------------->

Connection established
```

Remember:

```text
SYN
SYN-ACK
ACK
```

---

# UDP

**User Datagram Protocol (UDP)** is connectionless.

UDP has less transport-layer overhead and does not provide TCP-style acknowledgments, retransmission, or ordered delivery.

Common UDP use cases include:

```text
DNS queries
DHCP
Voice/video traffic
Streaming
Some gaming traffic
Network discovery
```

Applications can add their own reliability mechanisms when needed.

---

# TCP vs. UDP

```text
TCP
- Connection-oriented
- Reliable ordered delivery
- More overhead
- Uses acknowledgments

UDP
- Connectionless
- No TCP-style delivery guarantee
- Lower overhead
- Useful for time-sensitive/simple exchanges
```

Do not memorize this as "TCP is good, UDP is bad." Each exists for different requirements.

---

# Ports

A port identifies a service or application endpoint.

Port numbers range from:

```text
0–65535
```

Common groupings:

```text
0–1023      Well-known ports
1024–49151  Registered ports
49152–65535 Dynamic/private ports
```

---

# Source and Destination Ports

A client normally uses a temporary source port while connecting to a server's service port.

Example:

```text
Client
192.168.1.50:53000
        ↓
Server
192.168.1.10:443
```

The server is listening on TCP 443 for HTTPS.

---

# Common Ports

Become familiar with these:

```text
20/21  FTP
22     SSH
23     Telnet
25     SMTP
53     DNS
67/68  DHCP
80     HTTP
110    POP3
123    NTP
143    IMAP
161/162 SNMP
389    LDAP
443    HTTPS
445    SMB
3389   RDP
```

Some protocols can use TCP, UDP, or both depending on the operation.

Port numbers alone do not prove what application traffic actually contains.

---

# Secure vs. Legacy Protocols

Prefer secure alternatives when available.

Examples:

```text
Telnet → SSH
HTTP   → HTTPS
FTP    → Secure alternatives where appropriate
```

Understanding older protocols is still useful for troubleshooting and certification study.

---

# Inspect Connections in Windows

PowerShell:

```powershell
Get-NetTCPConnection
```

Listening TCP ports:

```powershell
Get-NetTCPConnection -State Listen
```

Command Prompt:

```text
netstat -ano
```

---

# Test a TCP Port

PowerShell:

```powershell
Test-NetConnection example.com -Port 443
```

Useful fields include:

```text
RemoteAddress
RemotePort
TcpTestSucceeded
```

A successful ping and a successful TCP service test answer different questions.

---

# Troubleshooting by Layer

Example:

```text
Host reachable by IP
        ↓
TCP 443 fails
```

Possible areas include:

```text
Service not listening
Host firewall
Network firewall
Incorrect port
Application failure
Routing/security policy
```

Do not assume basic IP connectivity means every application should work.

---

# Key Terms

```text
TCP
UDP
Port
Socket
Source Port
Destination Port
Three-Way Handshake
SYN
ACK
Listening Port
Well-Known Port
```

---

# Knowledge Check

1. Which OSI layer is associated with TCP and UDP?
2. What are the three steps of the TCP handshake?
3. Does UDP provide TCP-style acknowledgments?
4. What port is commonly used by HTTPS?
5. What port is commonly used by SSH?
6. Why does a client use a temporary source port?
7. What does `Test-NetConnection -Port` help verify?

---

# Lesson Summary

Think of communication as:

```text
IP Address
    ↓
Correct Host
    ↓
TCP / UDP Port
    ↓
Correct Service
```

---

# Hands-On Lab

➡️ **[Lab 16 — TCP, UDP, Ports, and Protocols](../labs/lab-16-tcp-udp-ports-and-protocols.md)**
