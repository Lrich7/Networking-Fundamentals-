# ✅ Networking Fundamentals — Final Exam Answer Key

**Lessons Covered:** 1–20  
**Questions:** 60

Use this answer key only after completing the Final Comprehensive Exam.

---

# 📊 Scoring

Give yourself:

```text
1 point per correct answer
```

Maximum:

```text
60 points
```

Suggested study targets:

| Score | Percentage | Recommendation |
|---:|---:|---|
| 54–60 | 90–100% | Excellent |
| 48–53 | 80–88% | Strong |
| 42–47 | 70–78% | Review weak areas |
| 0–41 | Below 70% | Additional review recommended |

> These are course study targets and not official CompTIA Network+ passing-score equivalents.

---

# 1. B — Switch

Switches primarily forward Ethernet frames using MAC addresses.

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

# 2. C — Layer 3

OSI Layer 3 is the Network layer.

Think:

```text
IP addressing
Routing
Packets
```

---

# 3. C — TCP

TCP provides connection-oriented transport with reliability mechanisms such as sequencing, acknowledgments, and retransmissions.

---

# 4. B — DHCP/connectivity

A Windows address in:

```text
169.254.0.0/16
```

is an APIPA address.

It commonly appears when normal IPv4 configuration cannot be obtained through DHCP.

Investigate DHCP and the path to it.

---

# 5. B — DNS

DNS resolves names to IP addresses.

```text
Hostname
   ↓
  DNS
   ↓
IP Address
```

---

# 6. B — Discover, Offer, Request, Acknowledge

Remember:

```text
DORA

Discover
Offer
Request
Acknowledge
```

---

# 7. B — 172.18.10.25

Private IPv4 ranges include:

```text
10.0.0.0/8

172.16.0.0/12

192.168.0.0/16
```

`172.18.10.25` falls within the private `172.16–31` range.

---

# 8. A — 127.0.0.1

The IPv4 loopback address commonly used for local testing is:

```text
127.0.0.1
```

---

# 9. B — Resolve an IPv4 address to a MAC address

ARP allows an IPv4 host on an Ethernet LAN to discover the MAC address associated with a local IPv4 address.

---

# 10. C — Default gateway

Traffic for a remote subnet is normally sent toward the host's default gateway.

---

# 11. B — 255.255.255.192

Memorize:

```text
/24 = 255.255.255.0
/25 = 255.255.255.128
/26 = 255.255.255.192
/27 = 255.255.255.224
/28 = 255.255.255.240
/29 = 255.255.255.248
/30 = 255.255.255.252
```

---

# 12. B — 30

A `/27` contains:

```text
32 total addresses
```

Traditional usable hosts:

```text
32 - 2
=
30
```

---

# 13. B — 192.168.10.64

For `/27`:

```text
Block size = 32
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

`77` belongs to the `64–95` block.

Therefore:

```text
Network:
192.168.10.64
```

---

# 14. C — 192.168.10.95

The subnet is:

```text
Network:
192.168.10.64

Hosts:
192.168.10.65–94

Broadcast:
192.168.10.95

Next Network:
192.168.10.96
```

---

# 15. B — /26

Need:

```text
50 hosts
```

`/27`:

```text
30 usable
```

Too small.

`/26`:

```text
62 usable
```

Therefore `/26` is the smallest suitable choice.

---

# 16. B — They are on different subnets

A `/26` has 64-address blocks.

PC-A:

```text
192.168.1.50
```

belongs to:

```text
192.168.1.0/26
```

PC-B:

```text
192.168.1.100
```

belongs to:

```text
192.168.1.64/26
```

They require Layer 3 routing to communicate.

---

# 17. B — 10.10.10.17–10.10.10.22

A `/29` contains eight addresses:

```text
Network:
10.10.10.16

Hosts:
10.10.10.17–22

Broadcast:
10.10.10.23
```

---

# 18. B — /28

Traditional host counts:

```text
/27 = 30
/28 = 14
/29 = 6
/30 = 2
```

---

# 19. B — Provide logical Layer 2 segmentation

VLANs create separate logical Layer 2 broadcast domains.

---

# 20. A — Layer 3 routing

Communication between VLANs requires routing.

This may be performed by:

```text
Router

Layer 3 Switch

Firewall
```

depending on the design.

---

# 21. B — Trunk port

A trunk can carry traffic for multiple VLANs.

---

# 22. A — 802.1Q

IEEE 802.1Q is associated with VLAN tagging on Ethernet trunks.

---

# 23. B — `show vlan brief`

This Cisco command provides a quick view of VLANs and assigned access ports:

```text
show vlan brief
```

---

# 24. B — `show interfaces trunk`

Use:

```text
show interfaces trunk
```

to examine trunking information.

---

# 25. B — PoE

Power over Ethernet can provide both network connectivity and electrical power over Ethernet cabling.

Common devices include:

```text
Wireless APs
IP Phones
Cameras
```

---

# 26. B — 1, 6, 11

For traditional 20 MHz 2.4 GHz channel planning in the United States:

```text
1
6
11
```

are commonly used as non-overlapping channels.

---

# 27. A — Wireless interference

Overlapping channels can cause interference and reduce wireless performance.

---

# 28. B — Strong signal does not guarantee good network performance

Signal strength is only one factor.

Other factors include:

```text
Interference
Congestion
Packet loss
Access point load
Client capability
Backhaul performance
```

---

# 29. D — WPA3

Among the listed choices, WPA3 provides the strongest modern Wi-Fi security.

---

# 30. B — Site-to-site VPN

Think:

```text
Network
   ↕
 VPN
   ↕
Network
```

A site-to-site VPN commonly connects offices.

---

# 31. A — Remote-access VPN

Think:

```text
Remote User
     ↓
    VPN
     ↓
Company Network
```

---

# 32. B — Selected traffic uses the VPN while other traffic can use the local Internet connection

That describes split tunneling.

Actual routes depend on the organization's VPN policy.

---

# 33. B — Latency

Latency means:

> Delay.

---

# 34. C — Jitter

Jitter means:

> Variation in packet delay.

This is especially important for real-time traffic.

---

# 35. A — Throughput

Think:

```text
Bandwidth
=
Capacity

Throughput
=
Actual successful transfer
```

---

# 36. C — QoS

Quality of Service can prioritize important or delay-sensitive traffic.

Examples:

```text
Voice
Video
Business-critical applications
```

---

# 37. B — Jitter

High jitter can cause packets to arrive at inconsistent intervals.

That can create:

```text
Choppy voice

Audio gaps

Poor call quality
```

even when sufficient bandwidth exists.

---

# 38. A — Firewall

Firewalls enforce traffic policies between networks or security zones.

---

# 39. A — Access Control List

ACL:

```text
Access Control List
```

ACLs permit or deny traffic according to defined rules.

---

# 40. B — Least privilege

Least privilege means providing only the access necessary to perform legitimate responsibilities.

---

# 41. A — Segmentation

Segmentation can separate:

```text
Employees

Servers

Guests

Printers

IoT

Management
```

Security controls can then limit communication between segments.

---

# 42. A — Authentication, Authorization, Accounting

Remember:

```text
AAA

Authentication
Authorization
Accounting
```

---

# 43. A — Authentication

Authentication asks:

> Who are you?

---

# 44. B — Authorization

Authorization asks:

> What are you allowed to do?

Accounting tracks activity.

---

# 45. B — SSH

SSH provides encrypted remote command-line administration and is generally preferred over Telnet.

---

# 46. C — SNMPv3

SNMPv3 adds stronger security capabilities including authentication and privacy/encryption options.

---

# 47. B — Collecting event and log messages

Syslog is commonly used to centralize event messages.

Example:

```text
Router ──┐
Switch ──┼──→ Syslog Server
Firewall ┘
```

---

# 48. A — It shows what normal performance looks like

A baseline provides a reference.

Example:

```text
Normal latency:
15 ms

Current:
90 ms
```

Now the technician knows current behavior differs substantially from normal.

---

# 49. B — Redundancy

Redundancy means a backup resource exists.

---

# 50. A — Failover

Remember:

```text
Redundancy
=
Backup exists

Failover
=
Backup takes over
```

---

# 51. A — UPS

UPS:

```text
Uninterruptible Power Supply
```

It provides temporary battery power during electrical outages.

---

# 52. A — Physical connection/cable

Important clues:

```text
ONE USER

LINK LIGHT OFF
```

Start at Layer 1.

Check:

```text
Cable
Connector
NIC
Switch port
Power
```

---

# 53. B — DNS

Everything through remote IP connectivity works.

Only name resolution fails.

Think:

```text
IP works
+
Names fail
=
DNS
```

---

# 54. B — `ipconfig /all`

This displays detailed Windows network configuration.

Useful information includes:

```text
IP Address
Subnet Mask
Gateway
DNS
DHCP
MAC Address
Lease Information
```

---

# 55. B — `tracert`

Use:

```text
tracert <destination>
```

to help examine the Layer 3 path toward a remote destination.

---

# 56. B — Sends continuous echo requests until stopped

On Windows:

```text
ping 192.168.1.1 -t
```

continues until stopped, commonly with:

```text
Ctrl + C
```

This is useful when investigating intermittent connectivity.

---

# 57. A — Scope, symptoms, and what changed

Before changing things, determine:

```text
Who is affected?

What is affected?

What still works?

What doesn't?

When did it start?

What changed?
```

The fact that the outage followed a configuration change is particularly important evidence.

---

# 58. B — Test the theory

Once you establish a theory of probable cause:

```text
THEORY
   ↓
TEST
   ↓
RESULT
```

Testing gives you evidence before making larger changes.

---

# 59. A — Verify full functionality and check for unintended effects

Do not stop simply because the original symptom disappears.

Verify:

```text
Original problem fixed?

Users working?

Other systems working?

No new issues?

Monitoring normal?
```

Then document the solution.

---

# 60. A — WAN/network path performance

The clues show:

```text
LAN
✓

DNS
✓

Gateway
✓

Internet Reachability
✓

Packet Loss
HIGH

Latency
HIGH
```

Investigate the WAN/network path, including possibilities such as:

```text
Congestion

ISP problems

Routing path

Circuit issues

Upstream packet loss
```

---

# ⚡ Quick Answer Key

| # | Answer | # | Answer | # | Answer |
|---:|:---:|---:|:---:|---:|:---:|
| 1 | B | 21 | B | 41 | A |
| 2 | C | 22 | A | 42 | A |
| 3 | C | 23 | B | 43 | A |
| 4 | B | 24 | B | 44 | B |
| 5 | B | 25 | B | 45 | B |
| 6 | B | 26 | B | 46 | C |
| 7 | B | 27 | A | 47 | B |
| 8 | A | 28 | B | 48 | A |
| 9 | B | 29 | D | 49 | B |
| 10 | C | 30 | B | 50 | A |
| 11 | B | 31 | A | 51 | A |
| 12 | B | 32 | B | 52 | A |
| 13 | B | 33 | B | 53 | B |
| 14 | C | 34 | C | 54 | B |
| 15 | B | 35 | A | 55 | B |
| 16 | B | 36 | C | 56 | B |
| 17 | B | 37 | B | 57 | A |
| 18 | B | 38 | A | 58 | B |
| 19 | B | 39 | A | 59 | A |
| 20 | A | 40 | B | 60 | A |

---

# 📊 Review Your Performance by Topic

Your overall score matters, but your weak areas matter more.

---

## 🌐 Networking Foundations

Questions:

```text
1–10
```

Review:

```text
Switching

Routing

OSI Model

TCP / UDP

DHCP

DNS

ARP

IPv4

Default Gateway

Private Addressing
```

---

## 🧮 Subnetting

Questions:

```text
11–18
```

If you struggled here, use:

➡️ **[Subnetting Reference](../CheatSheet/subnetting-reference.md)**

You should eventually recognize these quickly:

```text
/24 → 254 hosts

/25 → 126

/26 → 62

/27 → 30

/28 → 14

/29 → 6

/30 → 2
```

And:

```text
/25 → block 128

/26 → block 64

/27 → block 32

/28 → block 16

/29 → block 8

/30 → block 4
```

---

## 🔀 Switching & VLANs

Questions:

```text
19–25
```

Review:

```text
VLANs

Access Ports

Trunks

802.1Q

Inter-VLAN Routing

PoE

Cisco Show Commands
```

---

## 📡 Wireless

Questions:

```text
26–29
```

Review:

```text
2.4 GHz

5 GHz

6 GHz

Channels

Interference

Signal Strength

WPA2 / WPA3
```

---

## 🔐 VPN

Questions:

```text
30–32
```

Know the difference between:

```text
Site-to-Site

Remote Access

Split Tunnel

Full Tunnel
```

---

## 📈 Performance

Questions:

```text
33–37
```

Know:

```text
Bandwidth

Throughput

Latency

Jitter

Packet Loss

QoS
```

Especially:

```text
Bandwidth
≠
Throughput
```

and:

```text
Latency
≠
Jitter
```

---

## 🛡️ Security

Questions:

```text
38–46
```

Review:

```text
Firewall

ACL

Least Privilege

Segmentation

AAA

SSH

SNMPv3
```

---

## 📊 Monitoring & Availability

Questions:

```text
47–51
```

Review:

```text
Syslog

Baselines

Redundancy

Failover

UPS
```

---

## 🧰 Troubleshooting

Questions:

```text
52–60
```

Use this mental model:

```text
IDENTIFY
   ↓
SCOPE
   ↓
WHAT WORKS?
   ↓
WHAT FAILS?
   ↓
THEORY
   ↓
TEST
   ↓
IMPLEMENT
   ↓
VERIFY
   ↓
DOCUMENT
```

---

# 🧠 Build a Weak-Area Scorecard

After grading, record something like:

```text
Foundations:
9 / 10

Subnetting:
6 / 8

Switching/VLANs:
7 / 7

Wireless:
3 / 4

VPN:
3 / 3

Performance:
4 / 5

Security:
8 / 9

Monitoring:
5 / 5

Troubleshooting:
7 / 9
```

Now your study plan becomes obvious.

For example:

```text
Priority 1:
Subnetting

Priority 2:
Troubleshooting

Priority 3:
Performance
```

Review those areas before retaking the exam.

---

# 🎯 Final Review Strategy

If you scored below your goal:

```text
1. Identify weak topics

2. Review the related lessons

3. Repeat the related labs

4. Use the CheatSheet references

5. Practice subnetting by hand

6. Retake Practice Exam 1 or 2

7. Retake this Final Exam
```

Do not simply memorize the answer letters.

The goal is to understand:

> **Why the correct answer is correct and why the other choices are not the best answer.**

---

# 🏆 Before Moving Toward Network+

You should be comfortable explaining these without looking them up:

```text
What does a switch do?

What does a router do?

What is a VLAN?

What is a trunk?

What is a default gateway?

What does DHCP do?

What does DNS do?

What does ARP do?

What is NAT?

What is a VPN?

What is latency?

What is jitter?

What is packet loss?

What is QoS?

What is least privilege?

What is AAA?

What is SNMP?

What is Syslog?

What is redundancy?

What is failover?
```

You should also be able to troubleshoot a basic network path:

```text
DEVICE
   ↓
NIC
   ↓
CABLE / WI-FI
   ↓
SWITCH / AP
   ↓
VLAN
   ↓
GATEWAY
   ↓
ROUTING / FIREWALL
   ↓
WAN / INTERNET
   ↓
DESTINATION
```

And use tools such as:

```text
ping

ipconfig /all

tracert

nslookup

arp -a
```

without having to guess what each tool is testing.

---

# 📚 Course Navigation

➡️ **[Return to Final Exam](final-exam.md)**

➡️ **[Practice Exam 1](practice-exam-1.md)**

➡️ **[Practice Exam 2](practice-exam-2.md)**

➡️ **[Cheat Sheet](../CheatSheet/cheat-sheet.md)**

➡️ **[Exam Tips](../CheatSheet/exam-tips.md)**

➡️ **[Subnetting Reference](../CheatSheet/subnetting-reference.md)**

➡️ **[Command Reference](../CheatSheet/command-reference.md)**

➡️ **[Glossary](../CheatSheet/glossary.md)**

➡️ **[Lessons](../lessons/README.md)**

➡️ **[Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**