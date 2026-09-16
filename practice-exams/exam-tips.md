# 🎯 CompTIA Network+ N10-009 Exam Tips

Tips for preparing for and taking the **CompTIA Network+ N10-009** exam.

This guide is designed to complement the Networking Fundamentals lessons, labs, projects, glossary, and cheat sheet.

> The goal is not just to memorize networking facts. Learn how to recognize what a question is actually testing.

---

# 🧠 1. Think Like a Network Technician

Network+ questions often present a situation rather than simply asking for a definition.

Instead of:

> What is DNS?

You may see something like:

```text
A user can ping a server by IP address,
but cannot connect using the server's hostname.
```

Think:

```text
IP connectivity works
        +
Name resolution fails
        =
DNS
```

Always use the clues provided.

---

# 🔎 2. Determine the Scope First

When troubleshooting, ask:

> **Who is affected?**

This can eliminate many possible answers.

### One user

Think about:

```text
Device
Cable
Wi-Fi
NIC
IP Configuration
Switch Port
```

### One VLAN

Think about:

```text
VLAN Configuration
Trunk
Gateway
DHCP Scope
Routing
ACL
```

### Entire building

Think about:

```text
Core Switch
Router
Firewall
WAN
Power
ISP
```

### Multiple locations

Think about:

```text
WAN
VPN
Cloud Service
DNS
Provider
```

---

# 🧩 3. Pay Attention to What Still Works

This is one of the most important Network+ habits.

Example:

```text
User cannot open websites.

Can ping gateway:
YES

Can ping 8.8.8.8:
YES

Cannot ping example.com:
NO
```

You already know:

```text
Physical connection
✓

Local network
✓

Gateway
✓

Routing
✓

Internet IP connectivity
✓
```

The strongest clue points toward:

> **DNS**

---

# 🧅 4. Use the OSI Model for Troubleshooting

When you don't know where to start:

```text
Layer 1
Physical
Cable / Signal / Port
      ↓
Layer 2
Data Link
MAC / VLAN / Switching
      ↓
Layer 3
Network
IP / Gateway / Routing
      ↓
Layer 4
Transport
TCP / UDP / Ports
      ↓
Layers 5–7
Sessions / Services / Applications
```

You do not always need to troubleshoot strictly from Layer 1 upward, but the model helps organize your thinking.

---

# 🔌 5. Physical Problems Are Often the Simplest Answer

Do not overlook:

```text
Loose Cable

Bad Cable

Disabled Port

No Power

Wrong Port

Weak Wireless Signal

Damaged Connector
```

If the question describes:

> One device suddenly has no link light.

Investigate Layer 1 before redesigning the routing table.

---

# 🔢 6. Memorize the Private IPv4 Ranges

Know these without thinking:

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

# 🚨 7. Recognize APIPA Immediately

If you see:

```text
169.254.x.x
```

think:

> **The device did not receive normal IPv4 configuration from DHCP.**

Possible causes:

```text
DHCP Server Down

Wrong VLAN

DHCP Relay Problem

Cable / Wi-Fi Problem

Switch Port Problem

DHCP Scope Problem
```

Do not automatically assume the DHCP server itself is broken.

The client may simply be unable to reach it.

---

# 🧮 8. Know the Core Subnet Sizes

These should become automatic:

| CIDR | Mask | Traditional Usable Hosts |
|---:|---|---:|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /29 | 255.255.255.248 | 6 |
| /30 | 255.255.255.252 | 2 |

A quick pattern:

```text
/24 → 256 addresses
/25 → 128
/26 → 64
/27 → 32
/28 → 16
/29 → 8
/30 → 4
```

Each additional prefix bit halves the subnet size.

---

# 🧮 9. Use the Block-Size Trick

For IPv4 subnetting:

```text
256 - interesting mask octet
```

Example:

```text
/27
=
255.255.255.224
```

Therefore:

```text
256 - 224
=
32
```

Subnet boundaries occur every:

```text
32
```

addresses.

---

# 🚪 10. Remember What the Default Gateway Does

A default gateway is used when the destination is:

> **Outside the local subnet.**

Same subnet:

```text
PC
 ↓
Switch
 ↓
PC
```

Different subnet:

```text
PC
 ↓
Switch
 ↓
Default Gateway
 ↓
Router
 ↓
Remote Network
```

---

# 🔍 11. ARP Is Local IPv4 Resolution

Think:

```text
IPv4 Address
      ↓
     ARP
      ↓
MAC Address
```

ARP helps a device determine the Layer 2 destination needed for local IPv4 Ethernet communication.

---

# 🔀 12. Switch vs. Router

This distinction should be automatic.

### Switch

Think:

```text
Layer 2

MAC Addresses

Frames

VLANs
```

### Router

Think:

```text
Layer 3

IP Addresses

Packets

Routes

Different Networks
```

---

# 🧱 13. VLAN Questions

Remember:

> **Each VLAN creates a separate Layer 2 broadcast domain.**

Devices in different VLANs require Layer 3 routing to communicate.

Example:

```text
VLAN 10
Employees
     │
     │
   Router
     │
     │
VLAN 20
Servers
```

---

# 🔌 14. Access vs. Trunk

### Access Port

Typically:

> One VLAN for an endpoint.

### Trunk

Typically:

> Multiple VLANs between networking devices.

Remember:

```text
802.1Q
=
VLAN Tagging
```

---

# 📦 15. DHCP = Configuration

When you see:

```text
Automatic IP Address

Subnet Mask

Gateway

DNS Server
```

think:

> **DHCP**

Remember DORA:

```text
Discover
Offer
Request
Acknowledge
```

And:

```text
UDP 67 / 68
```

---

# 📛 16. DNS = Names

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

Remember:

```text
DNS
TCP/UDP 53
```

---

# 🔄 17. NAT vs. PAT

### NAT

Think:

> **Address translation**

### PAT

Think:

> **Many internal devices sharing a public IPv4 address using port information**

PAT is commonly called:

> **NAT overload**

---

# 🚦 18. TCP vs. UDP

### TCP

Think:

```text
Connection-oriented

Reliable

Ordered

Acknowledgments
```

### UDP

Think:

```text
Connectionless

Lower overhead

No TCP-style delivery guarantee
```

Do not assume:

> UDP = fast and TCP = slow

The exam is testing their characteristics, not a universal performance rule.

---

# 📊 19. Bandwidth Is Not Latency

### Bandwidth

> How much data can theoretically be carried.

### Throughput

> How much data is actually transferred.

### Latency

> How long data takes to travel.

### Jitter

> Variation in delay.

### Packet Loss

> Packets fail to arrive.

---

# ☎️ 20. Voice and Video Questions

For:

```text
Choppy Calls

Audio Dropouts

Frozen Video

Delay During Conversation
```

think about:

```text
Latency

Jitter

Packet Loss

Congestion

QoS

Wireless Quality
```

A high-bandwidth connection can still provide terrible VoIP performance.

---

# 📡 21. Remember 2.4 GHz: 1, 6, 11

For traditional 20 MHz 2.4 GHz Wi-Fi planning in the U.S., remember:

```text
1
6
11
```

This is a very useful exam memory item.

---

# 📶 22. Wi-Fi Frequency Basics

### 2.4 GHz

Generally:

```text
Longer Range

More Interference

Fewer Non-Overlapping Channels
```

### 5 GHz

Generally:

```text
More Channels

Higher Potential Performance

Shorter Range than 2.4 GHz
```

### 6 GHz

Generally:

```text
More Available Spectrum

Less Legacy Congestion

Requires Newer Equipment
```

---

# 🔐 23. Wireless Security

If given choices such as:

```text
WEP

WPA

WPA2

WPA3
```

recognize that WEP is obsolete and insecure.

Modern environments should generally use the strongest mutually supported appropriate security configuration.

---

# 🔐 24. Secure Management Protocols

Know these pairs:

```text
Telnet
    ↓
Replace with
    ↓
SSH
```

```text
HTTP Management
    ↓
Replace with
    ↓
HTTPS
```

```text
Older SNMP
    ↓
Prefer where appropriate
    ↓
SNMPv3
```

---

# 🔑 25. AAA

Memorize:

```text
Authentication
Authorization
Accounting
```

Then translate:

```text
Authentication
=
Who are you?
```

```text
Authorization
=
What can you do?
```

```text
Accounting
=
What did you do?
```

---

# 🛡️ 26. CIA Triad

Know:

```text
Confidentiality

Integrity

Availability
```

### Confidentiality

Prevent unauthorized disclosure.

### Integrity

Prevent unauthorized modification.

### Availability

Keep services accessible to authorized users.

---

# 🧱 27. Segmentation Is a Security Tool

Think:

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

Then:

```text
ACL / Firewall
```

controls communication between them.

Remember:

> VLANs create segmentation, but security policy determines what traffic is actually permitted between networks.

---

# 📋 28. ACL = Permit or Deny

ACL means:

> **Access Control List**

Think:

```text
Source

Destination

Protocol

Port

Permit / Deny
```

depending on the ACL type and platform.

---

# 👀 29. SNMP vs. Syslog

Easy distinction:

### SNMP

Think:

> **Monitoring / management information**

### Syslog

Think:

> **Event logs**

Example:

```text
SNMP
→ Interface utilization is 92%
```

```text
Syslog
→ Interface went down at 09:14
```

---

# 📏 30. Baselines Matter

If a question asks how to determine whether performance is abnormal:

> **Compare against a baseline.**

Example:

```text
Current Latency:
75 ms
```

Without knowing normal latency, you have limited context.

If normal is:

```text
15 ms
```

then the change becomes meaningful.

---

# 🔌 31. Know PoE

PoE:

> **Power over Ethernet**

Common devices:

```text
Wireless AP

IP Phone

Security Camera
```

If an Ethernet-connected phone stays powered after its separate power adapter is removed:

> Check whether it is receiving PoE.

---

# 🌎 32. Site-to-Site vs. Remote-Access VPN

### Site-to-Site

Connects:

> **Network ↔ Network**

### Remote Access

Connects:

> **User/Device ↔ Organization**

---

# 🔀 33. Split vs. Full Tunnel

### Split Tunnel

Some traffic uses:

```text
VPN
```

while other traffic uses:

```text
Local Internet
```

### Full Tunnel

Most or all traffic is routed through:

```text
VPN
```

according to policy.

---

# 🔄 34. Redundancy vs. Failover

### Redundancy

Having backup resources.

### Failover

Actually moving service to the backup after a failure.

Example:

```text
Primary Fiber
      X
      ↓
Backup 5G
```

The backup connection is:

> **Redundancy**

Switching to it is:

> **Failover**

---

# 🧰 35. Know What the Commands Do

You don't need to become a Cisco engineer for Network+, but recognize common commands.

### IP Configuration

```text
ipconfig /all
```

### Test Connectivity

```text
ping
```

### Trace Path

```text
tracert
```

### DNS

```text
nslookup
```

### ARP Cache

```text
arp -a
```

### Routing Table

```text
route print
```

### Connections

```text
netstat
```

---

# 🔀 36. Recognize Cisco Show Commands

```text
show ip interface brief
```

Think:

> Interfaces and IP/status.

```text
show vlan brief
```

Think:

> VLAN membership.

```text
show interfaces trunk
```

Think:

> Trunks.

```text
show mac address-table
```

Think:

> MAC-to-port mappings.

```text
show ip route
```

Think:

> Routing table.

```text
show running-config
```

Think:

> Current configuration.

---

# 🧠 37. Don't Change Five Things at Once

If troubleshooting methodology appears on the exam:

> Test your theory.

Do not:

```text
Replace cable
Change DNS
Reboot router
Change VLAN
Reset firewall
```

simultaneously.

You need to know:

> **What actually caused and corrected the problem.**

---

# 📝 38. Verify After the Fix

A common trap is assuming troubleshooting ends when the configuration is changed.

It doesn't.

After implementing the solution:

> **Verify full system functionality.**

Check:

```text
Original Problem Fixed?

User Can Work?

Other Services Still Work?

Monitoring Normal?

No New Problem Created?
```

---

# 📚 39. Document the Solution

The final troubleshooting step is:

> **Document findings, actions, outcomes, and lessons learned.**

Documentation helps future technicians solve similar problems faster.

---

# 🧗 40. Know When to Escalate

Escalate when:

```text
You lack permissions

You lack expertise

Vendor support is required

Security incident is suspected

Risk exceeds your authority

Major outage procedures require it
```

Good escalation includes:

```text
Symptoms

Scope

Timeline

Tests

Results

Changes

Suspected Cause
```

---

# ⚠️ 41. Watch for Words Like BEST, FIRST, and MOST LIKELY

These words matter.

### FIRST

The exam wants:

> **The appropriate initial action**

not every possible action.

### MOST LIKELY

Several answers may technically be possible.

Choose the one that:

> **Best fits all the clues.**

### BEST

Look for the answer that satisfies the requirements with the most appropriate technology or procedure.

---

# 🚫 42. Don't Overthink Simple Questions

If:

```text
One PC has no network connection

Link light is off
```

and one answer says:

> Check the Ethernet cable.

That is probably more appropriate than:

> Reconfigure the organization's routing protocol.

Use the scope and symptoms.

---

# 🎯 43. Eliminate Obviously Wrong Answers

If unsure, remove answers that conflict with the clues.

Example:

```text
User can reach the Internet by IP address.
```

That makes:

> Complete physical network failure

very unlikely.

Eliminating even two options can dramatically improve your odds.

---

# 🧪 44. Performance-Based Questions

Network+ may include performance-based questions where you interact with a simulated environment.

Before making changes:

1. Read the entire scenario.
2. Identify the requested end state.
3. Look at all tabs/screens.
4. Record important information.
5. Make deliberate changes.
6. Verify your work.

Your Packet Tracer labs are useful preparation because they teach you to interpret network configurations instead of only recognizing vocabulary.

---

# ⏱️ 45. Manage Your Time

If a question is consuming too much time:

> Flag it and return later if the testing interface allows.

Do not let one difficult subnetting question consume time needed for many easier questions.

---

# 🧮 46. Use Your Scratch Space

If permitted by the testing environment, immediately write down useful memory aids such as:

```text
/24 256
/25 128
/26 64
/27 32
/28 16
/29 8
/30 4
```

and:

```text
OSI

7 Application
6 Presentation
5 Session
4 Transport
3 Network
2 Data Link
1 Physical
```

This reduces the need to repeatedly reconstruct them mentally.

---

# 🎯 47. Know Your Core Ports

Prioritize:

```text
20/21 FTP

22 SSH

23 Telnet

25 SMTP

53 DNS

67/68 DHCP

80 HTTP

110 POP3

123 NTP

143 IMAP

161 SNMP

162 SNMP Trap

443 HTTPS

445 SMB

3389 RDP
```

Learn them in groups rather than as one long sequence.

---

# 🧠 48. Memorize Concepts in Pairs

Pairs make recall easier:

```text
Switch ↔ MAC

Router ↔ IP

DHCP ↔ Configuration

DNS ↔ Names

ARP ↔ IPv4-to-MAC

SSH ↔ Secure CLI

SNMP ↔ Monitoring

Syslog ↔ Logs

VLAN ↔ Segmentation

Trunk ↔ Multiple VLANs

ACL ↔ Permit/Deny

Gateway ↔ Remote Network
```

---

# 🔍 49. Follow the Packet

When completely stuck, visualize:

```text
PC
 ↓
NIC
 ↓
Cable / Wi-Fi
 ↓
Switch Port
 ↓
VLAN
 ↓
Gateway
 ↓
Router / Firewall
 ↓
WAN
 ↓
Remote Network
 ↓
Server
 ↓
Application
```

Then ask:

> **Where is the first place the expected behavior could have failed?**

---

# 🏆 50. Understand More Than You Memorize

The strongest preparation is being able to explain:

```text
Why does a PC need a gateway?

Why does ARP exist?

Why do we need routing?

Why would VLANs be used?

Why does DHCP fail across VLANs without proper support?

Why can DNS fail while Internet connectivity still works?

Why can a fast Internet connection still have poor VoIP quality?

Why should guests be segmented?

Why establish a baseline?
```

If you can answer those questions without looking them up, you are building the kind of understanding Network+ is intended to test.

---

# 📋 Last-Minute Review

Before the exam, make sure you're comfortable with:

- OSI model
- TCP/IP concepts
- IPv4 addressing
- IPv6 basics
- Private IPv4 ranges
- APIPA
- Subnetting
- ARP
- DHCP
- DNS
- NAT/PAT
- TCP vs. UDP
- Common ports
- Ethernet
- Cabling
- Fiber
- PoE
- Switching
- VLANs
- Trunks
- Routing
- Wireless
- WAN technologies
- VPNs
- Network performance
- QoS concepts
- Firewalls
- ACLs
- Segmentation
- AAA
- SNMP
- Syslog
- Monitoring
- Baselines
- Redundancy
- Troubleshooting methodology
- Common troubleshooting commands
- Documentation
- Escalation

---

# 🎓 Exam-Day Mental Model

When you encounter a troubleshooting question:

```text
READ THE SYMPTOMS
       ↓
DETERMINE SCOPE
       ↓
IDENTIFY WHAT WORKS
       ↓
IDENTIFY WHAT FAILS
       ↓
FOLLOW THE PACKET
       ↓
ELIMINATE IMPOSSIBLE ANSWERS
       ↓
CHOOSE THE ANSWER THAT
BEST FITS THE EVIDENCE
```

Don't troubleshoot the network you imagine.

> **Troubleshoot the network described in the question.**

---

# 📚 Course Navigation

➡️ **[Cheat Sheet](cheat-sheet.md)**

➡️ **[Glossary](glossary.md)**

➡️ **[Command Reference](command-reference.md)**

➡️ **[Return to Main README](../README.md)**

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**