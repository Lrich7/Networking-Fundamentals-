# Lab 16 — TCP, UDP, Ports, and Protocols

## Lab Objective

Inspect TCP connections and ports, test services with PowerShell, and observe TCP/UDP behavior using Wireshark and Packet Tracer.

---

# Part 1 — Inspect TCP Connections

Run:

```powershell
Get-NetTCPConnection
```

Then:

```powershell
Get-NetTCPConnection -State Listen
```

Record several listening ports without publishing sensitive organizational information.

---

# Part 2 — Use Netstat

Run:

```text
netstat -ano
```

Identify:

```text
Local Address
Foreign Address
State
PID
```

What does `LISTENING` mean?

```text
________________________________________
```

---

# Part 3 — Test HTTPS

Run:

```powershell
Test-NetConnection example.com -Port 443
```

Record:

```text
Remote port: __________________
TCP test succeeded: ___________
```

---

# Part 4 — Compare Service Tests

Test:

```powershell
Test-NetConnection example.com -Port 80
Test-NetConnection example.com -Port 443
```

Do not assume every server must accept every port.

Explain why port-specific testing is more useful than ping alone for an application issue.

---

# Part 5 — Port Matching

Match:

```text
SSH       ___
DNS       ___
HTTP      ___
HTTPS     ___
SMB       ___
RDP       ___
```

Ports:

```text
22
53
80
443
445
3389
```

---

# Part 6 — Wireshark Capture

If Wireshark is available, start a capture on your active interface.

Browse to a safe HTTPS site, then stop the capture.

Use a display filter such as:

```text
tcp
```

or:

```text
tcp.port == 443
```

Do not upload captures from a production/company network to a public repository.

---

# Part 7 — Find the Handshake

In an appropriate training capture, locate:

```text
SYN
SYN-ACK
ACK
```

Record the order.

What changed between client and server source/destination ports?

---

# Part 8 — UDP Observation

Use a safe DNS lookup:

```text
nslookup example.com
```

In Wireshark, try:

```text
dns
```

Observe whether UDP appears in the exchange.

---

# Part 9 — Packet Tracer Protocol Observation

Build or reuse a simple Packet Tracer network with a client and server.

Enable a supported service such as HTTP.

Use Simulation Mode to observe the traffic.

Identify:

```text
Layer 3 protocol
Layer 4 protocol
Destination port
```

---

# Part 10 — Troubleshooting Ticket

Ticket:

> "The server responds to ping, but the website does not load."

Create a troubleshooting plan that includes:

```text
DNS
TCP port
Server service
Host firewall
Network firewall
Application
```

---

# Knowledge Check

1. What is TCP port 443?
2. What does a listening port indicate?
3. What is the TCP handshake sequence?
4. Why might ping work while HTTPS fails?
5. Is DNS always UDP-only?

---

# Challenge

Use Windows tools to create a small **port troubleshooting cheat sheet** containing:

```text
Protocol
Default port
TCP/UDP
Useful test command
Likely troubleshooting area
```

Include at least 10 common protocols.

---

# Lab Completion Checklist

- [ ] Inspected TCP connections
- [ ] Inspected listening ports
- [ ] Used netstat
- [ ] Tested TCP services
- [ ] Matched common ports
- [ ] Observed TCP in Wireshark
- [ ] Identified a TCP handshake
- [ ] Observed DNS/UDP
- [ ] Used Packet Tracer Simulation Mode
- [ ] Completed troubleshooting ticket
- [ ] Completed knowledge check
- [ ] Completed challenge

---

# Lab Complete

You have completed **Lab 16 — TCP, UDP, Ports, and Protocols**.

# Next Lesson

➡️ **[Lesson 17 — DNS Fundamentals](../lessons/lesson-17-dns-fundamentals.md)**
