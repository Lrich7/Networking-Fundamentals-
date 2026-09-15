# 🧪 Lab 10 — TCP, UDP, Ports, and Protocols

Welcome to **Lab 10 of Networking Fundamentals**.

This lab connects network theory to something you'll use constantly in IT:

> **Testing whether a network service is actually reachable.**

You'll use:

```text
Command Prompt
+
PowerShell
+
Wireshark
+
Cisco Packet Tracer
```

to investigate:

- TCP
- UDP
- Ports
- DNS
- HTTPS
- TCP connections
- TCP handshakes
- Application services

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- View active TCP connections
- Identify local and remote ports
- Recognize ephemeral ports
- Test TCP ports with PowerShell
- Perform DNS lookups
- Capture TCP traffic
- Capture UDP traffic
- Identify a TCP three-way handshake
- Identify DNS traffic
- Compare TCP and UDP
- Identify application ports
- Configure HTTP and DNS services in Packet Tracer
- Test application connectivity
- Troubleshoot a service failure
- Explain why ping and application tests are different

---

# 🎓 Network+ Focus

This lab reinforces:

- TCP
- UDP
- Port numbers
- TCP handshakes
- DNS
- HTTP/HTTPS
- Client/server communication
- Application troubleshooting
- Wireshark
- `netstat`
- `Test-NetConnection`
- `nslookup`
- `Resolve-DnsName`

---

# ⏱️ Estimated Time

**75–90 minutes**

---

# ⚠️ Safety

Only capture traffic on networks and systems you're authorized to inspect.

Also:

> **Do not upload your personal Wireshark capture to this public GitHub repository.**

Packet captures can contain:

- IP addresses
- MAC addresses
- DNS requests
- Hostnames
- Network information
- Application metadata

---

# 🖥️ PART 1 — VIEW ACTIVE CONNECTIONS

Open Command Prompt.

Run:

```cmd
netstat -ano
```

Look for:

```text
Proto
Local Address
Foreign Address
State
PID
```

---

# Step 1 — Find an Established TCP Connection

Look for:

```text
ESTABLISHED
```

Record one:

```text
Protocol:

____________________________________

Local Address:

____________________________________

Local Port:

____________________________________

Remote Address:

____________________________________

Remote Port:

____________________________________

PID:

____________________________________
```

---

# 🧠 Question

Which side appears to be using the high-numbered temporary port?

```text
____________________________________
```

Usually:

> **The client**

---

# 🌐 PART 2 — CREATE WEB TRAFFIC

Open your browser.

Visit a normal HTTPS website you trust.

Then immediately run:

```cmd
netstat -ano
```

Look for connections using:

```text
:443
```

You may see something conceptually like:

```text
192.168.1.25:53142
142.x.x.x:443
ESTABLISHED
```

---

# 🧠 Identify the Ports

In:

```text
192.168.1.25:53142
        ↓
142.x.x.x:443
```

identify:

```text
Client Port:
53142

Server Port:
443
```

The client port is:

> **Ephemeral**

The destination service port is:

> **HTTPS**

---

# 🔷 PART 3 — TEST A TCP PORT

Open PowerShell.

Run:

```powershell
Test-NetConnection example.com -Port 443
```

Look for:

```text
TcpTestSucceeded
```

Record:

```text
Remote Address:

____________________________________

Remote Port:

____________________________________

TcpTestSucceeded:

____________________________________
```

---

# 🧠 What Did This Test?

This tests whether PowerShell can establish TCP connectivity to:

```text
example.com
```

on:

```text
TCP 443
```

This is more specific than:

```cmd
ping example.com
```

---

# 🧪 Compare Ping vs. Port Test

Run:

```powershell
Test-NetConnection example.com
```

Then:

```powershell
Test-NetConnection example.com -Port 443
```

These test different things.

Conceptually:

```text
Ping
 ↓
ICMP Reachability

Port Test
 ↓
TCP Service Connectivity
```

---

# ⭐ Troubleshooting Principle

Never assume:

```text
PING WORKS
=
APPLICATION WORKS
```

A server can respond to ICMP while a particular application port is unavailable.

The opposite can also happen: an application may work even when ICMP echo is blocked.

---

# 🌎 PART 4 — TEST DNS

Run:

```cmd
nslookup example.com
```

Record:

```text
DNS Server:

____________________________________

Resolved Address:

____________________________________
```

---

# 🔷 PowerShell DNS

Run:

```powershell
Resolve-DnsName example.com
```

Look at the returned records.

You may see:

```text
A
AAAA
```

Remember:

```text
A
=
IPv4

AAAA
=
IPv6
```

---

# 🔬 PART 5 — WIRESHARK

Open Wireshark.

Select your active:

```text
Ethernet
```

or:

```text
Wi-Fi
```

interface.

Start capturing.

---

# Step 1 — Generate DNS Traffic

Open Command Prompt.

Run:

```cmd
nslookup example.com
```

Return to Wireshark.

Stop the capture if desired.

Apply:

```text
dns
```

---

# 📝 Inspect a DNS Packet

Record:

```text
Source IP:

____________________________________

Destination IP:

____________________________________

Transport Protocol:

____________________________________

Source Port:

____________________________________

Destination Port:

____________________________________
```

Traditional DNS commonly uses:

```text
UDP 53
```

but you may observe TCP or encrypted DNS depending on the traffic and system configuration.

---

# 🧠 DNS Observation

Look for:

```text
Standard query
```

and:

```text
Standard query response
```

Conceptually:

```text
CLIENT
   │
   │ DNS Query
   ▼
DNS SERVER
   │
   │ DNS Response
   ▼
CLIENT
```

---

# 🌐 PART 6 — CAPTURE TCP

Start a fresh capture if necessary.

Apply:

```text
tcp
```

Open a website or generate a new TCP connection.

You should see TCP traffic.

---

# Step 1 — Look for SYN

Apply:

```text
tcp.flags.syn == 1
```

Look for packets associated with a newly established TCP connection.

---

# 🤝 Find the Three-Way Handshake

Try to identify:

```text
SYN
 ↓
SYN-ACK
 ↓
ACK
```

Record:

```text
Client IP:

____________________________________

Client Source Port:

____________________________________

Server IP:

____________________________________

Server Destination Port:

____________________________________
```

---

# 🧠 Packet 1

```text
SYN

Client
  ↓
Server
```

---

# 🧠 Packet 2

```text
SYN-ACK

Server
  ↓
Client
```

---

# 🧠 Packet 3

```text
ACK

Client
  ↓
Server
```

At this point:

> **The TCP connection is established.**

---

# 🔄 PART 7 — WATCH THE PORTS REVERSE

Suppose the initial packet is:

```text
192.168.1.25:53000
        ↓
203.0.113.50:443
```

The reply becomes:

```text
203.0.113.50:443
        ↓
192.168.1.25:53000
```

Record one conversation you observe:

```text
Client IP:

____________________________________

Client Port:

____________________________________

Server IP:

____________________________________

Server Port:

____________________________________
```

---

# ⚡ PART 8 — UDP

Apply:

```text
udp
```

You may see:

- DNS
- mDNS
- DHCP
- QUIC
- NTP
- Other application traffic

Pick one UDP packet.

Record:

```text
Source IP:

____________________________________

Destination IP:

____________________________________

Source Port:

____________________________________

Destination Port:

____________________________________
```

---

# 🧠 Compare TCP and UDP

Did you see a:

```text
SYN
SYN-ACK
ACK
```

before the UDP datagram?

> **No**

UDP doesn't use TCP's connection-establishment handshake.

---

# 🌐 PART 9 — PACKET TRACER SERVICE NETWORK

Now open:

> **Cisco Packet Tracer**

Build:

```text
PC-01
   │
   ▼
 SW-01
   │
   ▼
 R-01
   │
   ▼
 SW-02
   │
   ├──── WEB-01
   │
   └──── DNS-01
```

---

# 📍 Network A — Clients

Use:

```text
192.168.10.0/24
```

Router:

```text
192.168.10.1
```

PC-01:

```text
192.168.10.10
255.255.255.0

Gateway:
192.168.10.1
```

---

# 📍 Network B — Servers

Use:

```text
192.168.20.0/24
```

Router:

```text
192.168.20.1
```

WEB-01:

```text
192.168.20.10
255.255.255.0

Gateway:
192.168.20.1
```

DNS-01:

```text
192.168.20.20
255.255.255.0

Gateway:
192.168.20.1
```

---

# 📋 Addressing Table

| Device | IP | Mask | Gateway |
|---|---|---|---|
| PC-01 | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| R-01 Client | 192.168.10.1 | 255.255.255.0 | — |
| R-01 Server | 192.168.20.1 | 255.255.255.0 | — |
| WEB-01 | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 |
| DNS-01 | 192.168.20.20 | 255.255.255.0 | 192.168.20.1 |

---

# 🧪 PART 10 — VERIFY BASIC CONNECTIVITY

From PC-01:

```cmd
ping 192.168.10.1
```

Then:

```cmd
ping 192.168.20.10
```

Then:

```cmd
ping 192.168.20.20
```

All should succeed before continuing.

---

# 🌐 PART 11 — ENABLE HTTP

Open:

```text
WEB-01
```

Go to:

```text
Services
 ↓
HTTP
```

Make sure:

```text
HTTP
=
On
```

---

# 🖥️ Test the Web Server

On PC-01:

```text
Desktop
 ↓
Web Browser
```

Enter:

```text
http://192.168.20.10
```

Record:

```text
PASS / FAIL
```

---

# 🧠 What Just Happened?

Conceptually:

```text
PC-01
192.168.10.10

      ↓

TCP Connection

      ↓

WEB-01
192.168.20.10:80
```

HTTP commonly uses:

```text
TCP 80
```

---

# 🌎 PART 12 — CONFIGURE DNS

Open:

```text
DNS-01
```

Go to:

```text
Services
 ↓
DNS
```

Turn DNS:

> **On**

Create a DNS record:

```text
Name:
www.training.local

Address:
192.168.20.10
```

---

# 🖥️ Configure PC-01 DNS

Set PC-01's DNS server to:

```text
192.168.20.20
```

---

# 🧪 Test Name Resolution

From PC-01:

```cmd
nslookup www.training.local
```

If supported by the Packet Tracer PC command interface, verify the name resolves to:

```text
192.168.20.10
```

---

# 🌐 Test the Website by Name

Open the browser.

Enter:

```text
http://www.training.local
```

Record:

```text
PASS / FAIL
```

---

# 🧠 What Services Were Used?

To reach:

```text
http://www.training.local
```

the PC first needs:

```text
DNS
 ↓
Resolve Name
 ↓
192.168.20.10
```

Then:

```text
HTTP
 ↓
Connect to Web Server
 ↓
TCP 80
```

One simple browser action may involve:

> **Multiple network protocols.**

---

# 🔬 PART 13 — SIMULATION MODE

Switch Packet Tracer to:

> **Simulation Mode**

Filter for protocols such as:

```text
DNS
TCP
HTTP
```

Then visit:

```text
http://www.training.local
```

Use:

> **Capture / Forward**

Observe the sequence.

Try to identify:

```text
DNS Request
      ↓
DNS Response
      ↓
TCP Connection
      ↓
HTTP Request
      ↓
HTTP Response
```

---

# 💥 PART 14 — TROUBLESHOOTING CHALLENGE 1

Turn off:

```text
HTTP
```

on WEB-01.

Now test:

```cmd
ping 192.168.20.10
```

Does ping work?

```text
YES / NO
```

Now try:

```text
http://192.168.20.10
```

Does the website work?

```text
YES / NO
```

---

# ⭐ Important Observation

You should now have a perfect example of:

```text
PING
=
WORKING

APPLICATION
=
NOT WORKING
```

Why?

Because the host is reachable, but:

> **The HTTP service isn't available.**

---

# 🔧 Repair

Turn HTTP:

> **On**

Retest.

---

# 💥 PART 15 — TROUBLESHOOTING CHALLENGE 2

Turn off:

```text
DNS
```

on DNS-01.

Now try:

```text
http://www.training.local
```

Record:

```text
PASS / FAIL
```

Then try:

```text
http://192.168.20.10
```

Record:

```text
PASS / FAIL
```

---

# 🧠 What Does This Tell You?

If:

```text
IP works
```

but:

```text
Hostname fails
```

investigate:

> **DNS**

---

# 🔧 Repair

Turn DNS:

> **On**

Retest:

```text
http://www.training.local
```

---

# 💥 PART 16 — TROUBLESHOOTING CHALLENGE 3

Change PC-01's DNS server from:

```text
192.168.20.20
```

to:

```text
192.168.20.99
```

Try:

```text
www.training.local
```

Then try:

```text
192.168.20.10
```

What changed?

```text
____________________________________

____________________________________
```

Restore:

```text
192.168.20.20
```

---

# 🧠 PART 17 — PORT IDENTIFICATION

Fill these in without looking back.

| Service | Port |
|---|---:|
| FTP Control | |
| SSH | |
| Telnet | |
| SMTP | |
| DNS | |
| DHCP Server | |
| DHCP Client | |
| HTTP | |
| POP3 | |
| NTP | |
| IMAP | |
| SNMP | |
| HTTPS | |
| SMB | |
| LDAP | |
| LDAPS | |
| RDP | |

---

# ✅ Answers

| Service | Port |
|---|---:|
| FTP Control | 21 |
| SSH | 22 |
| Telnet | 23 |
| SMTP | 25 |
| DNS | 53 |
| DHCP Server | 67 |
| DHCP Client | 68 |
| HTTP | 80 |
| POP3 | 110 |
| NTP | 123 |
| IMAP | 143 |
| SNMP | 161 |
| HTTPS | 443 |
| SMB | 445 |
| LDAP | 389 |
| LDAPS | 636 |
| RDP | 3389 |

---

# 🧠 PART 18 — TROUBLESHOOTING PRACTICE

Match the symptom to the first protocol/service you would investigate.

---

### Scenario 1

```text
IP websites work.
Hostnames don't.
```

Answer:

```text
____________________
```

---

### Scenario 2

```text
Server responds to ping.
Windows file share fails.
```

Answer:

```text
____________________
```

---

### Scenario 3

```text
Server responds to ping.
Remote Desktop fails.
```

Answer:

```text
____________________
```

---

### Scenario 4

```text
Computer doesn't receive an IPv4 address automatically.
```

Answer:

```text
____________________
```

---

### Scenario 5

```text
Network device isn't reporting monitoring information.
```

Answer:

```text
____________________
```

---

# ✅ Answers

```text
1. DNS

2. SMB / TCP 445

3. RDP / 3389

4. DHCP / UDP 67–68

5. SNMP / UDP 161–162
```

These are starting points, not guaranteed root causes.

---

# 🎓 NETWORK+ CHALLENGE 1

Which sequence represents a TCP handshake?

### A.

```text
ACK
SYN
FIN
```

### B.

```text
SYN
SYN-ACK
ACK
```

### C.

```text
DNS
ARP
HTTP
```

### D.

```text
UDP
ACK
SYN
```

> **Answer: B**

---

# 🎓 NETWORK+ CHALLENGE 2

Which protocol commonly uses UDP 123?

### A. HTTP
### B. NTP
### C. SMB
### D. SSH

> **Answer: B**

---

# 🎓 NETWORK+ CHALLENGE 3

A packet shows:

```text
Source:
192.168.10.25:54231

Destination:
192.168.20.10:443
```

Which port is probably ephemeral?

> **54231**

Which port represents the server service?

> **443**

---

# 🎓 NETWORK+ CHALLENGE 4

A technician successfully pings a server but can't connect to TCP 443.

Which statement is correct?

### A. The server must be completely offline.
### B. Ping proves HTTPS is working.
### C. Network reachability exists, but TCP 443 still needs investigation.
### D. DNS must be the cause.

> **Answer: C**

---

# 🎓 NETWORK+ CHALLENGE 5

Which service commonly uses TCP 445?

### A. SMB
### B. SSH
### C. DNS
### D. NTP

> **Answer: A**

---

# 📋 Lab Review

In this lab, you:

- Used `netstat`
- Found established TCP connections
- Identified ephemeral ports
- Tested TCP 443
- Used `Test-NetConnection`
- Used `nslookup`
- Used `Resolve-DnsName`
- Captured DNS traffic
- Captured TCP traffic
- Identified TCP SYN packets
- Examined the TCP handshake
- Captured UDP traffic
- Compared TCP and UDP
- Built a client/server network
- Configured a web server
- Configured a DNS server
- Tested HTTP
- Tested DNS
- Used Packet Tracer Simulation Mode
- Broke HTTP while leaving ping functional
- Broke DNS while leaving IP connectivity functional
- Troubleshot incorrect DNS configuration
- Practiced common Network+ ports

---

# 💾 Save Your Packet Tracer Lab

Save as:

```text
lab-10-tcp-udp-ports-protocols.pkt
```

Keep personal Wireshark `.pcapng` captures local.

Don't upload them to a public GitHub repository.

---

# 🏆 PHASE 2 COMPLETE

You've completed:

```text
PHASE 2
ADDRESSING & COMMUNICATION

Ethernet & MAC
      ↓
IPv4
      ↓
Subnetting
      ↓
IPv6
      ↓
TCP / UDP
      ↓
Ports & Protocols
```

At this point, you should be able to look at something like:

```text
192.168.10.25:53142
        ↓
192.168.20.10:443
```

and begin asking:

```text
What are the IP addresses?
        ↓
Are they local or remote?
        ↓
What transport protocol?
        ↓
What ports?
        ↓
What service?
        ↓
Can I reach the host?
        ↓
Can I reach the port?
        ↓
Is DNS involved?
        ↓
Where is the failure?
```

That's a real troubleshooting workflow.

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE

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
✅ Lab 10

        ↓

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES

🟡 NEXT:
Lesson 11 — Switching Fundamentals

⬜ Lab 11 — Switching Fundamentals

⬜ Lesson 12 — VLANs & Network Segmentation

⬜ Lab 12 — VLANs & Network Segmentation

⬜ Lesson 13 — Routing Fundamentals

⬜ Lesson 14 — DHCP

⬜ Lesson 15 — DNS

⬜ Lesson 16 — NAT & Address Translation

        ↓

🏗️ Project 03
Build a Routed Small-Business Network
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 11 — Switching Fundamentals**

Next we'll take the switch concepts you've already seen and go much deeper into:

- MAC address tables
- MAC learning
- Frame forwarding
- Flooding
- Broadcast domains
- Collision domains
- Full duplex
- Speed and duplex
- Managed switches
- Access ports
- Switch CLI
- Spanning Tree introduction
- Loops
- Switching troubleshooting

This will also prepare us directly for:

> **Lesson 12 — VLANs and Network Segmentation**

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**