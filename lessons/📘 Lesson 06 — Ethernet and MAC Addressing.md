# 📘 Lesson 06 — Ethernet and MAC Addressing

Welcome to **Lesson 06 of Networking Fundamentals**.

You have completed Phase 1 and your first major project. Now we begin:

> 🔵 **Phase 2 — Addressing & Communication**

In this lesson, you'll go deeper into what happens inside a local network.

You'll learn how:

```text
PC
 ↓
Ethernet
 ↓
Switch
 ↓
MAC Address
 ↓
Another Device
```

actually works.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain Ethernet
- Explain MAC addresses
- Recognize MAC address format
- Explain Ethernet frames
- Identify source and destination MAC addresses
- Explain how switches learn MAC addresses
- Understand MAC address tables
- Explain known and unknown unicast traffic
- Explain broadcast and multicast traffic
- Recognize the Ethernet broadcast address
- Explain ARP
- Understand how IPv4 and MAC addresses work together
- Explain local vs. routed Layer 2 communication
- Explain why MAC addresses change across routers
- Use Layer 2 concepts during troubleshooting

---

# 🎓 Network+ Focus

This lesson reinforces Network+ concepts including:

- Ethernet
- MAC addressing
- Ethernet frames
- Layer 2 switching
- MAC address tables
- Unicast
- Broadcast
- Multicast
- ARP
- Broadcast domains
- Layer 2 troubleshooting

A useful question to keep in mind throughout this lesson is:

> **How does a device actually deliver traffic to another device on the local network?**

---

# 🌐 What Is Ethernet?

Ethernet is one of the most common technologies used to connect devices on wired local area networks.

Example:

```text
PC-01 ─── SW-01 ─── PC-02
```

Ethernet operates primarily at:

> **OSI Layer 2 — Data Link**

and uses:

> **MAC addresses**

to help deliver frames across the local network.

---

# 🧠 Ethernet vs. IP

Ethernet and IP perform different jobs.

## Ethernet

Think:

> **Local delivery**

Ethernet uses:

```text
MAC Addresses
```

---

## IP

Think:

> **Logical addressing and communication across networks**

IP uses:

```text
IP Addresses
```

Together:

```text
IP determines where communication ultimately needs to go.

Ethernet helps deliver it across the current local network.
```

---

# 🪪 What Is a MAC Address?

MAC stands for:

> **Media Access Control**

A MAC address identifies a network interface at Layer 2.

Example:

```text
00:1A:2B:3C:4D:5E
```

Windows may display the same style of address as:

```text
00-1A-2B-3C-4D-5E
```

---

# 🔢 MAC Address Size

A traditional Ethernet MAC address is:

> **48 bits**

It is normally displayed as six groups of two hexadecimal digits.

Example:

```text
A4-B1-C1-12-34-56
```

---

# 🔤 Hexadecimal

MAC addresses use hexadecimal.

Hexadecimal contains:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

You don't need to perform hexadecimal calculations yet.

For now, simply recognize the format.

---

# 🖥️ Find Your MAC Address in Windows

Open Command Prompt and run:

```cmd
ipconfig /all
```

Look for:

```text
Physical Address
```

Example:

```text
Physical Address. . . . . . : A4-B1-C1-12-34-56
```

---

# 🔷 PowerShell

You can also run:

```powershell
Get-NetAdapter
```

Look for:

```text
MacAddress
```

---

# 🧠 One Computer Can Have Multiple MAC Addresses

A computer may contain:

- Ethernet adapter
- Wi-Fi adapter
- Bluetooth adapter
- VPN adapter
- Virtual network adapter

Different interfaces can have different MAC addresses.

So:

> **One computer does not necessarily mean one MAC address.**

---

# 🕵️ MAC Randomization

Modern operating systems may also use randomized MAC addresses, particularly with Wi-Fi.

This can help reduce tracking across wireless networks.

Because of this, you should not always assume that a device presents the exact same visible MAC address everywhere.

---

# 📦 Ethernet Frames

The Layer 2 PDU used by Ethernet is called a:

> **Frame**

A simplified Ethernet frame looks like:

```text
┌───────────────────────┐
│ Destination MAC       │
├───────────────────────┤
│ Source MAC            │
├───────────────────────┤
│ Type / Length         │
├───────────────────────┤
│ Payload               │
├───────────────────────┤
│ Frame Check Sequence  │
└───────────────────────┘
```

You don't need to memorize every field.

For now, focus heavily on:

```text
Source MAC
+
Destination MAC
```

---

# 📤 Source MAC

The source MAC tells us:

> **Which interface sent the Ethernet frame onto this local link?**

Example:

```text
Source MAC:
AA-AA-AA-AA-AA-AA
```

---

# 📥 Destination MAC

The destination MAC tells us:

> **Where should this Ethernet frame be delivered on this local link?**

Example:

```text
Destination MAC:
BB-BB-BB-BB-BB-BB
```

---

# 🏠 Local Communication Example

Suppose:

```text
PC-A
IP: 192.168.10.10
MAC: AA-AA-AA-AA-AA-AA
```

needs to communicate with:

```text
PC-B
IP: 192.168.10.20
MAC: BB-BB-BB-BB-BB-BB
```

Both are on the same local network.

The Ethernet frame can contain:

```text
Source MAC:
AA-AA-AA-AA-AA-AA

Destination MAC:
BB-BB-BB-BB-BB-BB
```

The switch uses Layer 2 information to forward the frame.

---

# 🔀 How Does a Switch Know Where Devices Are?

A switch learns.

Imagine:

```text
PC-A ── Fa0/1
PC-B ── Fa0/2
PC-C ── Fa0/3
          │
        SW-01
```

PC-A sends a frame.

The switch sees:

```text
Source MAC:
AA-AA-AA-AA-AA-AA
```

arriving on:

```text
Fa0/1
```

The switch learns:

```text
AA-AA-AA-AA-AA-AA → Fa0/1
```

---

# 📋 MAC Address Table

The switch stores learned information in its:

> **MAC Address Table**

Example:

| MAC Address | Port |
|---|---|
| AA-AA-AA-AA-AA-AA | Fa0/1 |
| BB-BB-BB-BB-BB-BB | Fa0/2 |
| CC-CC-CC-CC-CC-CC | Fa0/3 |

---

# 🧠 Important Rule

Switches primarily learn from:

> **Source MAC addresses**

Conceptually:

```text
Frame Arrives
      ↓
Read Source MAC
      ↓
Record Incoming Port
      ↓
Update MAC Table
```

---

# 🎯 Known Unicast

Suppose the switch already knows:

```text
BB-BB-BB-BB-BB-BB → Fa0/2
```

A frame arrives destined for that MAC.

The switch can forward it toward:

```text
Fa0/2
```

instead of unnecessarily forwarding it everywhere.

---

# ❓ Unknown Unicast

What if the destination MAC isn't in the table?

The switch may:

> **Flood the frame**

out the appropriate ports in that Layer 2 domain except the port where the frame arrived.

Conceptually:

```text
Unknown frame enters Port 1

        ↓

Port 2 → FRAME
Port 3 → FRAME
Port 4 → FRAME
```

If the destination replies, the switch can learn its location.

---

# 👤 Unicast

Unicast means:

> **One sender → One destination**

```text
PC-A
 │
 ▼
PC-B
```

---

# 📢 Broadcast

Broadcast means:

> **One sender → Everyone in the local broadcast domain**

Ethernet's broadcast MAC address is:

```text
FF:FF:FF:FF:FF:FF
```

This is an important address to recognize.

---

# 👥 Multicast

Multicast means:

> **One sender → Selected group**

Conceptually:

```text
             Device A ✓
            /
Sender ─── Network ─ Device B
            \
             Device C ✓
```

---

# 📋 Traffic Type Summary

| Type | Meaning |
|---|---|
| Unicast | One to one |
| Broadcast | One to all in broadcast domain |
| Multicast | One to selected group |

Easy memory aid:

```text
UNICAST
ONE

BROADCAST
EVERYONE

MULTICAST
GROUP
```

---

# 🧩 Broadcast Domains

A broadcast domain is the portion of a Layer 2 network where broadcasts can propagate.

Example:

```text
PC-A ──┐
       │
PC-B ─ SW-01
       │
PC-C ──┘
```

These devices may all belong to the same broadcast domain.

---

# 🚦 Routers Separate Broadcast Domains

Now consider:

```text
LAN A
  │
SW-01
  │
R-01
  │
SW-02
  │
LAN B
```

Normal Layer 2 broadcasts from LAN A do not simply pass through the router into LAN B.

Therefore:

```text
LAN A = Broadcast Domain 1

LAN B = Broadcast Domain 2
```

---

# 🔍 What Is ARP?

ARP stands for:

> **Address Resolution Protocol**

ARP answers a very important IPv4 networking question:

> **I know the IPv4 address. What MAC address should I use for local delivery?**

Conceptually:

```text
IPv4 Address
      ↓
     ARP
      ↓
MAC Address
```

---

# 📢 ARP Request

Suppose PC-A wants to communicate with:

```text
192.168.10.20
```

but doesn't know that device's MAC address.

PC-A can send an ARP request asking:

> **Who has 192.168.10.20?**

Because the MAC is unknown, the request is broadcast.

```text
PC-A
 │
 │ Who has 192.168.10.20?
 ▼
SW-01
 ├──── PC-B
 ├──── PC-C
 └──── PC-D
```

---

# 📬 ARP Reply

The device that owns the address responds.

Example:

```text
192.168.10.20 is at
BB-BB-BB-BB-BB-BB
```

PC-A now knows the Layer 2 address needed for local delivery.

---

# 🧾 ARP Cache

Windows stores learned IPv4-to-MAC mappings temporarily.

Run:

```cmd
arp -a
```

Example:

```text
Internet Address      Physical Address
192.168.1.1           11-22-33-44-55-66
192.168.1.20          aa-bb-cc-dd-ee-ff
```

---

# 🔷 PowerShell Neighbor Table

You can also run:

```powershell
Get-NetNeighbor
```

This can show neighbor information associated with both IPv4 and IPv6.

---

# 🌎 What About Remote Destinations?

Suppose your computer wants to communicate with:

```text
8.8.8.8
```

That address is not on your local LAN.

Your computer doesn't normally need the remote server's MAC address.

Instead, it needs the MAC address of its:

> **Default Gateway**

---

# ⭐ Critical Concept

For remote traffic:

```text
Destination IP
=
Remote Host
```

while:

```text
Destination MAC
=
Local Next Hop
```

Usually:

```text
Default Gateway
```

---

# 🚦 What Happens at the Router?

Consider:

```text
PC-A
 │
 ▼
R-01
 │
 ▼
Server
```

PC-A sends an Ethernet frame toward R-01.

R-01:

1. Receives the Ethernet frame
2. Removes the incoming Layer 2 framing
3. Examines the IP packet
4. Determines where the IP packet should go
5. Creates new Layer 2 framing for the next link

---

# 📦 MAC Addresses Change Across Routers

Suppose:

```text
PC-A
IP: 192.168.10.10
```

communicates with:

```text
SRV-01
IP: 192.168.20.10
```

First LAN:

```text
Source MAC:
PC-A

Destination MAC:
R-01
```

Second LAN:

```text
Source MAC:
R-01

Destination MAC:
SRV-01
```

The MAC addresses changed.

But the IP communication remains:

```text
192.168.10.10
       ↓
192.168.20.10
```

---

# 🧠 Layer 2 vs. Layer 3

This is one of the most important distinctions in networking:

```text
MAC ADDRESS
=
Local-link delivery
```

```text
IP ADDRESS
=
Logical communication across networks
```

---

# ⏳ MAC Address Table Aging

Dynamic MAC table entries don't necessarily stay forever.

They can:

> **Age out**

after periods of inactivity.

This allows switches to relearn where devices are located.

For example:

```text
Laptop
  ↓
Port 3
```

may later move to:

```text
Laptop
  ↓
Port 8
```

The switch needs to learn the new location.

---

# 🔐 MAC Addresses Are Not Strong Authentication

MAC addresses can sometimes be:

- Changed
- Spoofed
- Randomized

Therefore:

> **A MAC address alone should not be treated as proof of a user's identity.**

You'll explore this more during the security portion of the course.

---

# 🛠️ Layer 2 Troubleshooting

Common Layer 2 or Ethernet-related problems can include:

- Bad cable
- Disabled NIC
- Disabled switch port
- Incorrect switch port
- Incorrect VLAN
- Bad switch
- MAC learning issue
- Speed or duplex issue
- Excessive broadcast traffic

Useful questions include:

```text
Is the physical link up?

Can devices on the same LAN communicate?

Does the switch learn the MAC?

Is the device on the correct switch port?

Is it in the correct VLAN?
```

---

# 🧠 Troubleshooting Scenario

Suppose:

```text
PC-A ──┐
PC-B ─ SW-01 ─ Router
PC-C ──┘
```

PC-A fails.

PC-B and PC-C continue working.

Rather than assuming the entire network is down, investigate things specific to PC-A:

```text
NIC
Cable
Switch Port
Configuration
```

Ask:

> **What do the failed devices have in common?**

This question becomes increasingly important as networks become larger.

---

# 🦈 Ethernet in Wireshark

In Wireshark, select a packet and expand:

> **Ethernet II**

You can inspect:

```text
Source MAC
Destination MAC
EtherType
```

Then expand:

> **Internet Protocol Version 4**

and inspect:

```text
Source IP
Destination IP
```

This makes the difference between Layer 2 and Layer 3 visible.

---

# 🦈 ARP in Wireshark

Use the display filter:

```text
arp
```

You may see something like:

```text
Who has 192.168.1.1?
```

followed by:

```text
192.168.1.1 is at 11:22:33:44:55:66
```

ARP is one of the easiest protocols to observe and understand in a packet capture.

---

# 📋 Ethernet Quick Reference

| Concept | Purpose |
|---|---|
| Ethernet | Common LAN technology |
| MAC Address | Layer 2 interface address |
| Frame | Ethernet Layer 2 PDU |
| Switch | Forwards Ethernet frames |
| MAC Table | Maps MAC addresses to switch ports |
| Unicast | One-to-one |
| Broadcast | One-to-all locally |
| Multicast | One-to-selected group |
| ARP | Resolves local IPv4 addresses to MAC addresses |
| Broadcast MAC | `FF:FF:FF:FF:FF:FF` |

---

# 🧠 Knowledge Check

### 1. Which OSI layer is Ethernet primarily associated with?

### 2. What does MAC stand for?

### 3. What is the Ethernet Layer 2 PDU?

### 4. What information does a switch store in its MAC address table?

### 5. Does a switch primarily learn from source or destination MAC addresses?

### 6. What may happen when the destination MAC is unknown?

### 7. What is the Ethernet broadcast MAC address?

### 8. What does ARP resolve?

### 9. For a remote destination, which local MAC address does a host usually need?

### 10. Do routers normally forward Ethernet broadcasts between IP networks?

---

# ✅ Knowledge Check Answers

1. **Layer 2 — Data Link**
2. **Media Access Control**
3. **Frame**
4. **MAC address → switch port mappings**
5. **Source MAC**
6. **The frame may be flooded within the Layer 2 domain**
7. **FF:FF:FF:FF:FF:FF**
8. **IPv4 address → local MAC address**
9. **The default gateway / next-hop MAC**
10. **No**

---

# 🎓 Network+ Challenge

A switch receives a frame with:

```text
Source MAC:
AA-AA-AA-AA-AA-AA
```

on:

```text
Fa0/5
```

What does it learn?

### A. The default gateway is Fa0/5
### B. AA-AA-AA-AA-AA-AA is reachable through Fa0/5
### C. Fa0/5 is a router
### D. Nothing

> **Answer: B**

---

# 🎓 Network+ Challenge 2

Which MAC address represents an Ethernet broadcast?

### A. `00:00:00:00:00:00`
### B. `FF:FF:FF:FF:FF:FF`
### C. `127.0.0.1`
### D. `255.255.255.0`

> **Answer: B**

---

# 🎓 Network+ Challenge 3

A workstation knows another local device's IPv4 address but needs its MAC address.

Which protocol is used?

### A. DNS
### B. DHCP
### C. ARP
### D. HTTPS

> **Answer: C — ARP**

---

# 🎓 Network+ Challenge 4

A workstation sends traffic to a remote server.

Which destination MAC normally appears in the Ethernet frame leaving the workstation?

### A. Remote server's MAC
### B. Default gateway's MAC
### C. DNS server's MAC
### D. Workstation's MAC

> **Answer: B — Default gateway's MAC**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- Ethernet operates primarily at Layer 2.
- Ethernet uses MAC addresses.
- Ethernet traffic is carried in frames.
- Switches learn source MAC addresses.
- Switches maintain MAC address tables.
- Known unicast traffic can be forwarded toward a specific port.
- Unknown unicast traffic may be flooded.
- Broadcast is one-to-all within the broadcast domain.
- `FF:FF:FF:FF:FF:FF` is the Ethernet broadcast address.
- ARP resolves local IPv4 addresses to MAC addresses.
- Routers separate broadcast domains.
- Remote traffic normally uses the gateway's MAC for the local Ethernet hop.
- MAC addresses change across routed links.
- IP addresses provide logical end-to-end addressing.

---

# 🌐 Cisco Companion

Cisco Packet Tracer is particularly useful for this topic because you can observe:

- MAC learning
- ARP
- Broadcasts
- Unicast forwarding
- Switch MAC tables

➡️ **[Cisco Networking Companion](../resources/cisco-companion.md)**

---

# 🧪 Next Step — Complete Lab 06

Lab 06 combines:

```text
Windows
+
Wireshark
+
Cisco Packet Tracer
```

You'll inspect Layer 2 communication from three different perspectives.

➡️ **[Lab 06 — Ethernet and MAC Addressing](../labs/lab-06-ethernet-mac-addressing.md)**

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS

✅ Lessons 01–05
✅ Labs 01–05
✅ Project 01

        ↓

🔵 PHASE 2 — ADDRESSING & COMMUNICATION

✅ Lesson 06 — Ethernet & MAC Addressing
        ↓
🟡 NEXT: Lab 06 — Ethernet & MAC Addressing
        ↓
⬜ Lesson 07 — IPv4 Addressing
        ↓
⬜ Lab 07 — IPv4 Addressing
        ↓
⬜ Lesson 08 — Subnetting Fundamentals
```

---

# ➡️ After the Lab

Continue to:

> **📘 Lesson 07 — IPv4 Addressing**

You'll go deeper into:

- IPv4 structure
- Private addresses
- Public addresses
- APIPA
- Loopback
- Subnet masks
- CIDR notation
- Network and host portions
- Default gateways

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**
