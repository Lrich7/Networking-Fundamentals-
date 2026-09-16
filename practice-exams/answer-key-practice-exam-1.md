# ✅ Networking Fundamentals — Practice Exam 1 Answer Key

**Lessons Covered:** 1–10  
**Questions:** 40

Use this answer key **after completing Practice Exam 1**.

Each answer includes a short explanation so you can identify the concept being tested.

---

# 📊 Scoring

Give yourself:

```text
1 point
```

for each correct answer.

Maximum:

```text
40 points
```

Suggested study targets:

| Score | Percentage | Recommendation |
|---:|---:|---|
| 36–40 | 90–100% | Excellent |
| 32–35 | 80–87.5% | Strong |
| 28–31 | 70–77.5% | Review weak areas |
| 0–27 | Below 70% | Review Lessons 1–10 |

> These are course study targets and are not official CompTIA passing-score equivalents.

---

# 1. B — Switch

A switch primarily forwards Ethernet frames based on:

```text
MAC addresses
```

Think:

```text
Switch
=
Layer 2
=
MAC
=
Frames
```

---

# 2. C — Router

Routers forward packets between different IP networks.

Think:

```text
Router
=
Layer 3
=
IP
=
Packets
```

---

# 3. B — LAN

A:

```text
LAN
```

or Local Area Network generally covers a relatively small geographic area such as:

- Home
- Office
- Building
- Campus area

---

# 4. C — WAN

A Wide Area Network connects geographically separated networks or locations.

Example:

```text
Springfield Office
       │
       │ WAN
       │
Kansas City Office
```

---

# 5. C — Layer 3

The Network layer is:

```text
OSI Layer 3
```

It handles concepts such as:

```text
IP addressing

Routing

Packets
```

---

# 6. B — Data Link

OSI Layer 2 is the:

```text
Data Link Layer
```

Think:

```text
MAC Addresses

Ethernet Frames

Switching

VLANs
```

---

# 7. C — Layer 4

TCP and UDP operate at:

```text
Layer 4
=
Transport
```

---

# 8. B — TCP

TCP provides:

```text
Connection-oriented communication

Acknowledgments

Sequencing

Retransmission

Reliable delivery mechanisms
```

---

# 9. C — Connectionless with relatively low overhead

UDP does not establish a TCP-style connection before sending data.

Think:

```text
UDP
=
Connectionless

Lower overhead

No TCP-style guaranteed delivery
```

---

# 10. B — Resolve an IPv4 address to a MAC address

ARP helps devices determine the MAC address associated with an IPv4 address on the local network.

Think:

```text
IPv4 Address
      ↓
     ARP
      ↓
MAC Address
```

---

# 11. C — The workstation did not obtain normal IPv4 configuration from DHCP

An address beginning with:

```text
169.254.x.x
```

is an APIPA address on Windows.

This commonly indicates that normal DHCP configuration was not obtained.

Possible causes include:

```text
DHCP unavailable

Wrong VLAN

DHCP relay problem

Switch port problem

Cable problem

Wi-Fi problem
```

---

# 12. B — DHCP

DHCP can automatically provide:

```text
IP Address

Subnet Mask

Default Gateway

DNS Servers
```

---

# 13. B — Discover, Offer, Request, Acknowledge

Remember:

```text
D
O
R
A
```

which stands for:

```text
Discover
Offer
Request
Acknowledge
```

---

# 14. B — DNS

DNS translates names into IP addresses.

Example:

```text
server01.example.local
        ↓
       DNS
        ↓
192.168.10.25
```

---

# 15. B — DNS

The user can reach a public IP address.

That tells you basic IP connectivity exists.

But hostname access fails.

Think:

```text
IP works
+
Name fails
=
Investigate DNS
```

---

# 16. C — Forward traffic destined for remote networks

The default gateway is used when traffic needs to reach a destination outside the local subnet.

Think:

```text
Local Network
     ↓
Default Gateway
     ↓
Remote Network
```

---

# 17. C — Default gateway

The PC is:

```text
192.168.10.25/24
```

The destination is:

```text
192.168.20.50
```

These are different `/24` networks.

The PC therefore sends the traffic toward its:

```text
Default Gateway
192.168.10.1
```

---

# 18. B — 172.20.10.5

Private IPv4 ranges are:

```text
10.0.0.0/8

172.16.0.0/12

192.168.0.0/16
```

`172.20.10.5` falls within:

```text
172.16.0.0
through
172.31.255.255
```

---

# 19. A — 172.16.0.0 through 172.31.255.255

Memorize the three RFC1918 private ranges:

```text
10.0.0.0/8

172.16.0.0/12

192.168.0.0/16
```

Be careful with the `172` range.

Not every `172.x.x.x` address is private.

---

# 20. B — 127.0.0.1

The IPv4 loopback address commonly used for local testing is:

```text
127.0.0.1
```

Example:

```cmd
ping 127.0.0.1
```

---

# 21. B — 255.255.255.0

```text
/24
=
255.255.255.0
```

This is one of the most important subnet masks to recognize immediately.

---

# 22. B — 62

A `/26` provides:

```text
64 total addresses
```

Traditionally:

```text
64 - 2
=
62 usable host addresses
```

The two excluded addresses are the:

```text
Network Address

Broadcast Address
```

---

# 23. B — 255.255.255.224

Memorize:

```text
/25 = 128

/26 = 192

/27 = 224

/28 = 240

/29 = 248

/30 = 252
```

Therefore:

```text
/27
=
255.255.255.224
```

---

# 24. C — 192.168.1.64

For:

```text
192.168.1.70/27
```

`/27` has a block size of:

```text
32
```

Boundaries:

```text
0
32
64
96
128
160
192
224
```

`70` falls between:

```text
64–95
```

Therefore:

```text
Network
=
192.168.1.64
```

---

# 25. C — 192.168.1.95

From Question 24:

```text
Network:
192.168.1.64

Next Network:
192.168.1.96
```

The broadcast address is one before the next network:

```text
192.168.1.95
```

Host range:

```text
192.168.1.65
through
192.168.1.94
```

---

# 26. B — /27

Need:

```text
25 hosts
```

A `/28` provides:

```text
14 traditional usable hosts
```

Too small.

A `/27` provides:

```text
30 traditional usable hosts
```

Therefore `/27` is the smallest option that satisfies the requirement.

---

# 27. B — They are on different subnets

A `/25` divides the `/24` into:

```text
192.168.10.0–127

192.168.10.128–255
```

PC-A:

```text
192.168.10.20
```

belongs to:

```text
192.168.10.0/25
```

PC-B:

```text
192.168.10.200
```

belongs to:

```text
192.168.10.128/25
```

Therefore they are on different subnets.

---

# 28. B — 10.0.0.17–10.0.0.22

Given:

```text
10.0.0.16/29
```

A `/29` contains:

```text
8 addresses
```

The subnet is:

```text
Network:
10.0.0.16

First Host:
10.0.0.17

Last Host:
10.0.0.22

Broadcast:
10.0.0.23
```

Therefore the traditional usable host range is:

```text
10.0.0.17–10.0.0.22
```

---

# 29. B — Create logical Layer 2 network segmentation

VLANs logically separate Layer 2 networks.

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
```

Each VLAN forms a separate Layer 2 broadcast domain.

---

# 30. A — Layer 3 routing

Different VLANs are separate Layer 2 networks.

Communication between them requires:

```text
Layer 3
```

This can be provided by devices such as:

```text
Router

Layer 3 Switch

Firewall
```

depending on the network design.

---

# 31. C — Trunk port

A trunk normally carries traffic for multiple VLANs.

Think:

```text
Access
=
Typically one VLAN for an endpoint
```

```text
Trunk
=
Multiple VLANs
```

---

# 32. A — 802.1Q

IEEE:

```text
802.1Q
```

is associated with VLAN tagging on Ethernet trunks.

---

# 33. B — `show vlan brief`

Use:

```text
show vlan brief
```

to quickly view:

```text
VLAN IDs

VLAN Names

Status

Assigned Access Ports
```

---

# 34. A — `show interfaces trunk`

Use:

```text
show interfaces trunk
```

to examine trunking information.

This can help verify:

```text
Trunk interfaces

Native VLAN

Allowed VLANs

Active VLANs
```

---

# 35. B — PoE

PoE means:

```text
Power over Ethernet
```

Common PoE-powered devices include:

```text
Wireless Access Points

IP Phones

Security Cameras
```

---

# 36. B — Ethernet cable and physical connection

The strongest clues are:

```text
One user affected

Link light OFF
```

Start at Layer 1.

Check:

```text
Cable

Connector

Switch port

NIC

Power
```

before investigating organization-wide routing or DNS.

---

# 37. B — Send continuous echo requests until stopped

On Windows:

```cmd
ping 192.168.1.1 -t
```

continues sending echo requests until stopped.

Typically stop it with:

```text
Ctrl + C
```

This can help observe intermittent connectivity.

---

# 38. C — `ipconfig /all`

Use:

```cmd
ipconfig /all
```

to view detailed Windows network configuration.

Look for:

```text
IPv4 Address

Subnet Mask

Gateway

DHCP

DNS

MAC Address

Lease Information
```

---

# 39. A — `tracert`

Windows:

```cmd
tracert <destination>
```

helps identify the Layer 3 path toward a destination where intermediate devices respond.

Example:

```cmd
tracert 8.8.8.8
```

---

# 40. C — DNS problem

Look at what works:

```text
Loopback
✓

Own IP
✓

Gateway
✓

Remote IP
✓
```

But:

```text
Name Resolution
X
```

This strongly points toward:

```text
DNS
```

The key troubleshooting lesson is:

> Pay attention to what **still works**, not only what is broken.

---

# 📊 Quick Answer Key

| # | Answer | # | Answer |
|---:|:---:|---:|:---:|
| 1 | B | 21 | B |
| 2 | C | 22 | B |
| 3 | B | 23 | B |
| 4 | C | 24 | C |
| 5 | C | 25 | C |
| 6 | B | 26 | B |
| 7 | C | 27 | B |
| 8 | B | 28 | B |
| 9 | C | 29 | B |
| 10 | B | 30 | A |
| 11 | C | 31 | C |
| 12 | B | 32 | A |
| 13 | B | 33 | B |
| 14 | B | 34 | A |
| 15 | B | 35 | B |
| 16 | C | 36 | B |
| 17 | C | 37 | B |
| 18 | B | 38 | C |
| 19 | A | 39 | A |
| 20 | B | 40 | C |

---

# 🎯 Review by Topic

If you missed questions:

### Networking Foundations

Review Questions:

```text
1–4
```

Review the early networking fundamentals lessons.

---

### OSI / TCP-IP

Review Questions:

```text
5–10
```

Focus on:

```text
OSI Layers

TCP

UDP

ARP

Frames

Packets
```

---

### DHCP / DNS / Addressing

Review Questions:

```text
11–20
```

Focus on:

```text
DHCP

DORA

DNS

APIPA

Default Gateway

Private IPv4

Loopback
```

---

### Subnetting

Review Questions:

```text
21–28
```

Use:

➡️ **[Subnetting Reference](../CheatSheet/subnetting-reference.md)**

Practice until these become automatic:

```text
/24

/25

/26

/27

/28

/29

/30
```

---

### Switching / VLANs

Review Questions:

```text
29–35
```

Focus on:

```text
VLAN

Access Port

Trunk

802.1Q

Inter-VLAN Routing

PoE

Cisco Show Commands
```

---

### Troubleshooting

Review Questions:

```text
36–40
```

Focus on:

```text
Physical Layer

ping

ipconfig /all

tracert

DNS Troubleshooting
```

---

# 🧠 What Your Score Should Tell You

Don't only look at:

```text
TOTAL SCORE
```

Look at:

```text
WHICH QUESTIONS
YOU MISSED
```

Example:

```text
Score:
34 / 40
```

looks good.

But if all six missed questions were subnetting questions, then subnetting is clearly an area to review.

The goal of these practice exams is to identify:

> **Where your understanding is weakest before the real exam does.**

---

# 📚 Course Navigation

➡️ **[Return to Practice Exam 1](practice-exam-1.md)**

➡️ **[Subnetting Reference](../CheatSheet/subnetting-reference.md)**

➡️ **[Exam Tips](../CheatSheet/exam-tips.md)**

➡️ **[Command Reference](../CheatSheet/command-reference.md)**

➡️ **[Cheat Sheet](../CheatSheet/cheat-sheet.md)**

➡️ **[Lessons](../lessons/README.md)**

➡️ **[Labs](../labs/README.md)**

➡️ **[Return to Main README](../README.md)**