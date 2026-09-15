# 🧪 Lab 09 — IPv6 Fundamentals

Welcome to **Lab 09 of Networking Fundamentals**.

In Lesson 09, you learned the fundamentals of IPv6.

Now you'll work with IPv6 using:

```text
Windows
+
PowerShell
+
Cisco Packet Tracer
```

You'll discover that IPv6 may already be operating on your computer even if you've never intentionally configured it.

Then you'll build:

> **Two IPv6 networks connected by a router**

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Find IPv6 addresses on Windows
- Identify IPv6 link-local addresses
- Identify IPv6 loopback
- Use `ipconfig`
- Use PowerShell to inspect IPv6
- Inspect IPv6 neighbors
- Test IPv6 loopback
- Recognize compressed IPv6 addresses
- Expand IPv6 addresses
- Build an IPv6 LAN in Packet Tracer
- Configure IPv6 `/64` prefixes
- Configure IPv6 router interfaces
- Test local IPv6 communication
- Test routed IPv6 communication
- Observe Neighbor Discovery
- Observe ICMPv6
- Troubleshoot incorrect IPv6 prefixes
- Troubleshoot IPv6 gateway problems

---

# 🎓 Network+ Focus

This lab reinforces:

- IPv6 notation
- Link-local addressing
- Global unicast concepts
- `/64`
- Neighbor Discovery
- ICMPv6
- SLAAC concepts
- IPv6 routing
- Dual stack
- IPv6 troubleshooting

---

# ⏱️ Estimated Time

**60–75 minutes**

---

# ⚠️ Safety

During the Windows portion:

> **Do not change IPv6 settings on your work or production computer.**

We'll only inspect the existing configuration.

All configuration changes will occur inside:

> **Cisco Packet Tracer**

---

# 🖥️ PART 1 — WINDOWS IPV6

# Step 1 — View Your IPv6 Configuration

Open Command Prompt.

Run:

```cmd
ipconfig
```

Find your active:

```text
Ethernet
```

or:

```text
Wi-Fi
```

adapter.

Look for entries such as:

```text
IPv6 Address
Temporary IPv6 Address
Link-local IPv6 Address
```

---

# 📝 Record What You Find

```text
Interface:

____________________________________

IPv6 Address:

____________________________________

Link-local IPv6 Address:

____________________________________
```

If you don't have a globally routable IPv6 address, that's okay.

You should still commonly see a link-local address.

---

# 🧠 Identify Link-Local

Does one address begin with:

```text
fe80
```

?

```text
YES / NO
```

If yes:

> **That's an IPv6 link-local address.**

---

# Step 2 — Detailed Configuration

Run:

```cmd
ipconfig /all
```

Look at your active adapter.

Record any IPv6-related information you see:

```text
____________________________________

____________________________________

____________________________________
```

---

# 🔷 Step 3 — PowerShell IPv6 Addresses

Open PowerShell.

Run:

```powershell
Get-NetIPAddress -AddressFamily IPv6
```

Look at:

```text
IPAddress
InterfaceAlias
PrefixLength
AddressState
```

---

# 📝 Record One Entry

```text
Interface:

____________________________________

IPv6 Address:

____________________________________

Prefix Length:

____________________________________

Address State:

____________________________________
```

---

# 🔁 Step 4 — Test IPv6 Loopback

Run:

```cmd
ping ::1
```

Record:

```text
PASS / FAIL
```

---

# 🧠 What Did You Test?

You tested:

> **The local IPv6 TCP/IP stack**

You did not test:

- Your router
- The Internet
- DNS
- Another device

Compare:

```text
IPv4 Loopback:
127.0.0.1

IPv6 Loopback:
::1
```

---

# 👥 Step 5 — Inspect IPv6 Neighbors

Run:

```powershell
Get-NetNeighbor -AddressFamily IPv6
```

Look for entries containing IPv6 addresses and link-layer addresses.

Record one if available:

```text
IPv6 Address:

____________________________________

Link-Layer Address:

____________________________________

State:

____________________________________
```

---

# 🧠 What Created These Entries?

IPv6 uses:

> **Neighbor Discovery**

rather than:

> **ARP**

---

# 🧪 PART 2 — IPV6 ADDRESS PRACTICE

# Step 6 — Compress an IPv6 Address

Start with:

```text
2001:0db8:0000:0000:0000:0000:0000:0010
```

Remove leading zeros:

```text
____________________________________
```

Then compress consecutive zero groups:

```text
____________________________________
```

---

# ✅ Answer

```text
2001:db8::10
```

---

# Step 7 — Compress Another Address

Start with:

```text
2001:0db8:1234:0000:0000:0000:0000:0025
```

Your answer:

```text
____________________________________
```

---

# ✅ Answer

```text
2001:db8:1234::25
```

---

# Step 8 — Expand an Address

Expand:

```text
2001:db8::50
```

Your answer:

```text
____________________________________
```

---

# ✅ Answer

```text
2001:0db8:0000:0000:0000:0000:0000:0050
```

---

# Step 9 — Identify the Address Type

Identify each.

### `::1`

```text
____________________________________
```

### `fe80::25`

```text
____________________________________
```

### `fd12:3456:789a::25`

```text
____________________________________
```

### `ff02::1`

```text
____________________________________
```

### `2001:db8::25`

```text
____________________________________
```

---

# ✅ Answers

```text
::1
Loopback

fe80::25
Link-local

fd12:3456:789a::25
Unique Local

ff02::1
Multicast

2001:db8::25
Documentation / Example Address
```

---

# 🌐 PART 3 — BUILD AN IPV6 LAN

Open:

> **Cisco Packet Tracer**

Add:

```text
PC-A
PC-B
SW-A
```

Build:

```text
PC-A ──┐
       │
      SW-A
       │
PC-B ──┘
```

---

# Step 10 — Configure IPv6 Addresses

We'll use the documentation prefix:

```text
2001:db8:10::/64
```

Configure PC-A:

```text
IPv6:
2001:db8:10::10

Prefix:
64
```

Configure PC-B:

```text
IPv6:
2001:db8:10::20

Prefix:
64
```

No router is needed yet because they're on the same subnet.

---

# Step 11 — Test Local IPv6

From PC-A:

```cmd
ping 2001:db8:10::20
```

Record:

```text
PASS / FAIL
```

---

# 🧠 Why Should This Work?

Both devices belong to:

```text
2001:db8:10::/64
```

Therefore they can communicate locally through the switch.

---

# 🔬 PART 4 — OBSERVE IPV6 TRAFFIC

Switch Packet Tracer to:

> **Simulation Mode**

Generate traffic from:

```text
PC-A
```

to:

```text
PC-B
```

Look for:

- ICMPv6
- Neighbor Discovery
- Neighbor Solicitation
- Neighbor Advertisement

Use:

> **Capture / Forward**

to watch the process.

---

# 🧠 Compare With IPv4

IPv4 may perform:

```text
ARP
    ↓
Find MAC
    ↓
Send ICMP
```

IPv6 performs:

```text
Neighbor Discovery
        ↓
Neighbor Information
        ↓
ICMPv6 Communication
```

---

# 📢 Step 12 — Look for Multicast

During Neighbor Discovery, you may observe multicast IPv6 traffic.

Remember:

```text
IPv6
=
No Broadcast
```

Instead:

```text
IPv6
=
Uses Multicast
```

---

# 🚦 PART 5 — ADD AN IPV6 ROUTER

Add:

```text
R-01
SW-B
PC-C
```

Build:

```text
PC-A ──┐
       │
      SW-A
       │
PC-B ──┘
       │
      R-01
       │
      SW-B
       │
      PC-C
```

---

# Step 13 — Create Network B

Network A:

```text
2001:db8:10::/64
```

Network B:

```text
2001:db8:20::/64
```

---

# Step 14 — Configure R-01

On the interface facing Network A:

```text
2001:db8:10::1/64
```

On the interface facing Network B:

```text
2001:db8:20::1/64
```

Make sure both interfaces are:

> **Enabled / On**

If configuring through the router CLI, IPv6 routing may need to be enabled with:

```text
ipv6 unicast-routing
```

---

# Step 15 — Configure Gateways

PC-A:

```text
IPv6:
2001:db8:10::10/64

Gateway:
2001:db8:10::1
```

PC-B:

```text
IPv6:
2001:db8:10::20/64

Gateway:
2001:db8:10::1
```

---

# Step 16 — Configure PC-C

PC-C:

```text
IPv6:
2001:db8:20::10/64

Gateway:
2001:db8:20::1
```

---

# 📋 IPv6 Addressing Table

| Device | IPv6 Address | Prefix | Gateway |
|---|---|---:|---|
| PC-A | `2001:db8:10::10` | /64 | `2001:db8:10::1` |
| PC-B | `2001:db8:10::20` | /64 | `2001:db8:10::1` |
| R-01 Network A | `2001:db8:10::1` | /64 | — |
| R-01 Network B | `2001:db8:20::1` | /64 | — |
| PC-C | `2001:db8:20::10` | /64 | `2001:db8:20::1` |

---

# Step 17 — Test the Local Router

From PC-A:

```cmd
ping 2001:db8:10::1
```

Record:

```text
PASS / FAIL
```

---

# Step 18 — Test Remote IPv6

From PC-A:

```cmd
ping 2001:db8:20::10
```

Record:

```text
PASS / FAIL
```

Traffic should travel:

```text
PC-A
 ↓
SW-A
 ↓
R-01
 ↓
SW-B
 ↓
PC-C
```

---

# 🧠 Why Is Routing Required?

PC-A belongs to:

```text
2001:db8:10::/64
```

PC-C belongs to:

```text
2001:db8:20::/64
```

These are:

> **Different IPv6 networks**

---

# 🔬 Step 19 — Observe Routed IPv6

Use:

> **Simulation Mode**

Send traffic:

```text
PC-A
 ↓
PC-C
```

Watch:

```text
PC-A
 ↓
SW-A
 ↓
R-01
 ↓
SW-B
 ↓
PC-C
```

Look for:

- ICMPv6
- Neighbor Discovery
- Router involvement
- IPv6 source address
- IPv6 destination address

---

# 💥 PART 6 — TROUBLESHOOTING

# Challenge 1 — Wrong Prefix

Change PC-B from:

```text
2001:db8:10::20/64
```

to:

```text
2001:db8:30::20/64
```

Now test from PC-A:

```cmd
ping 2001:db8:30::20
```

Record:

```text
PASS / FAIL
```

Why?

```text
____________________________________

____________________________________
```

Expected concept:

> PC-B is now configured for a different IPv6 network.

Restore:

```text
2001:db8:10::20/64
```

---

# Challenge 2 — Wrong Gateway

Change PC-C's gateway from:

```text
2001:db8:20::1
```

to:

```text
2001:db8:20::50
```

Test communication to another device on Network B if available.

Then test:

```text
PC-C
 ↓
PC-A
```

What happens?

```text
____________________________________

____________________________________
```

Local same-subnet communication can still work, while communication to another network requires a working router/default route.

Restore:

```text
2001:db8:20::1
```

---

# Challenge 3 — Link-Local Recognition

You see:

```text
fe80::2a0:ccff:fe12:3456
```

What type of address is this?

```text
____________________________________
```

> **IPv6 Link-Local**

---

# Challenge 4 — Loopback

You see:

```text
::1
```

What does it represent?

```text
____________________________________
```

> **IPv6 Loopback**

---

# Challenge 5 — Multicast

You see:

```text
ff02::1
```

What type of IPv6 address is it?

```text
____________________________________
```

> **Multicast**

Specifically, it represents all IPv6 nodes on the local link.

---

# 🧪 PART 7 — SLAAC OBSERVATION

Depending on the Packet Tracer devices and router configuration available, you can experiment with automatic IPv6 addressing.

IPv6 hosts may learn network information through:

> **Router Advertisements**

and configure themselves using:

> **SLAAC**

Conceptually:

```text
Router
   │
   │ Router Advertisement
   ▼
Host
   │
   ▼
Build IPv6 Address
```

If your Packet Tracer version supports automatic IPv6 configuration for the selected PC:

1. Configure the router's IPv6 `/64`.
2. Enable IPv6 routing.
3. Select automatic IPv6 configuration on the PC.
4. Observe the address it receives/configures.
5. Inspect its default gateway.

---

# 🧠 Important Observation

The default gateway may appear as a:

```text
fe80::
```

address.

That's normal in IPv6.

Routers commonly use their:

> **Link-local address**

as the next-hop/default-router address.

---

# 📝 PART 8 — ADDRESS PRACTICE

Identify each address.

---

## Address 1

```text
::1
```

Type:

```text
____________________________________
```

---

## Address 2

```text
fe80::abcd
```

Type:

```text
____________________________________
```

---

## Address 3

```text
fd12:3456:789a::1
```

Type:

```text
____________________________________
```

---

## Address 4

```text
ff02::1
```

Type:

```text
____________________________________
```

---

## Address 5

```text
2001:db8:1234::1
```

Type:

```text
____________________________________
```

---

# ✅ Answers

```text
::1
=
Loopback
```

```text
fe80::abcd
=
Link-Local
```

```text
fd12:3456:789a::1
=
Unique Local
```

```text
ff02::1
=
Multicast
```

```text
2001:db8:1234::1
=
Documentation / Example Address
```

---

# 🧠 Knowledge Check

### 1.

How many bits are in IPv6?

### 2.

What is the IPv6 loopback address?

### 3.

Which prefix identifies link-local IPv6 addresses?

### 4.

What type of IPv6 address begins with `ff`?

### 5.

Does IPv6 use ARP?

### 6.

What mechanism handles IPv6 neighbor discovery?

### 7.

What does SLAAC stand for?

### 8.

What prefix length is commonly used for an IPv6 LAN?

### 9.

What does dual stack mean?

### 10.

Does IPv6 use broadcast?

---

# ✅ Answers

1. **128 bits**
2. **`::1`**
3. **`fe80::/10`**
4. **Multicast**
5. **No**
6. **Neighbor Discovery using ICMPv6**
7. **Stateless Address Autoconfiguration**
8. **/64**
9. **Running IPv4 and IPv6 together**
10. **No**

---

# 🎓 Network+ Challenge 1

Which address is most likely IPv6 link-local?

### A. `::1`
### B. `fe80::25`
### C. `ff02::1`
### D. `2001:db8::25`

> **Answer: B**

---

# 🎓 Network+ Challenge 2

A technician wants to inspect IPv6 neighbors on Windows.

Which PowerShell command is useful?

### A. `Get-NetNeighbor -AddressFamily IPv6`
### B. `format c:`
### C. `nslookup -arp`
### D. `Get-Service IPv4`

> **Answer: A**

---

# 🎓 Network+ Challenge 3

PC-A:

```text
2001:db8:10::25/64
```

PC-B:

```text
2001:db8:20::25/64
```

What is required for normal communication between these networks?

### A. Hub
### B. Router / Layer 3 forwarding
### C. ARP
### D. IPv4 DHCP

> **Answer: B**

---

# 🎓 Network+ Challenge 4

Which IPv6 technology allows hosts to automatically build IPv6 addresses using router advertisements?

### A. NAT
### B. SLAAC
### C. ARP
### D. FTP

> **Answer: B**

---

# 📋 Lab Review

In this lab, you:

- Inspected IPv6 on Windows
- Found IPv6 link-local addresses
- Used `ipconfig`
- Used `Get-NetIPAddress`
- Tested `::1`
- Used `Get-NetNeighbor`
- Practiced IPv6 compression
- Practiced IPv6 expansion
- Identified IPv6 address types
- Built an IPv6 LAN
- Used `/64` prefixes
- Tested local IPv6 communication
- Observed Neighbor Discovery
- Observed ICMPv6
- Added an IPv6 router
- Built a second IPv6 network
- Routed between IPv6 networks
- Troubleshot an incorrect IPv6 prefix
- Troubleshot an incorrect gateway
- Examined SLAAC concepts
- Recognized IPv6 multicast

---

# 💾 Save Your Packet Tracer Lab

Save as:

```text
lab-09-ipv6-fundamentals.pkt
```

You do not need to upload the completed `.pkt` file unless you specifically want completed Packet Tracer examples in the repository.

---

# 🏆 Lab Complete

IPv6 should now look less like:

```text
2001:db8:85a3::8a2e:370:7334

😵
```

and more like:

```text
IPv6 Address
      ↓
What Type?
      ↓
What Prefix?
      ↓
Local or Remote?
      ↓
Gateway Needed?
      ↓
How Will Traffic Travel?
```

That's the same troubleshooting mindset you've already been developing with IPv4.

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

        ↓

🟡 NEXT:
Lesson 10 — TCP, UDP, Ports & Protocols
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 10 — TCP, UDP, Ports & Protocols**

This is where we'll connect addressing to the actual services running across the network.

You'll learn:

```text
TCP
UDP
Ports
Sockets
TCP Three-Way Handshake
DNS
DHCP
HTTP
HTTPS
SSH
RDP
SMTP
IMAP
POP3
SMB
SNMP
NTP
LDAP
LDAPS
FTP
SFTP
```

and start building the port numbers that are especially important for Network+.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**