# 🧪 Lab 08 — Subnetting Fundamentals

Welcome to **Lab 08 of Networking Fundamentals**.

You've learned the subnetting process.

Now you're going to use it.

You'll begin with:

```text
192.168.10.0/24
```

and divide it into:

> **Four /26 subnets**

Then you'll build part of the network in:

> 🌐 **Cisco Packet Tracer**

This lab combines:

```text
Subnet Calculation
+
Network Design
+
IPv4 Configuration
+
Routing
+
Troubleshooting
```

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Convert common CIDR prefixes to subnet masks
- Calculate host bits
- Calculate total addresses
- Calculate usable host addresses
- Determine block sizes
- Find network addresses
- Find broadcast addresses
- Find usable host ranges
- Divide a /24 into smaller subnets
- Assign addresses to devices
- Configure multiple subnets in Packet Tracer
- Route between subnets
- Determine whether hosts belong to the same subnet
- Troubleshoot incorrect subnet masks
- Troubleshoot incorrect gateways

---

# 🎓 Network+ Focus

This lab reinforces:

- CIDR
- IPv4 subnetting
- Subnet masks
- Network addresses
- Broadcast addresses
- Host ranges
- Routing
- Network segmentation
- Troubleshooting

---

# ⏱️ Estimated Time

**75–90 minutes**

Subnetting takes practice.

Don't rush.

---

# 📝 PART 1 — BUILD YOUR SUBNET CHEAT SHEET

Without looking back at Lesson 08, complete:

| CIDR | Mask | Block Size | Total Addresses | Traditional Usable |
|---|---|---:|---:|---:|
| /24 | | | | |
| /25 | | | | |
| /26 | | | | |
| /27 | | | | |
| /28 | | | | |
| /29 | | | | |
| /30 | | | | |

---

# ✅ Check Your Work

| CIDR | Mask | Block | Total | Traditional Usable |
|---|---|---:|---:|---:|
| /24 | 255.255.255.0 | 256 | 256 | 254 |
| /25 | 255.255.255.128 | 128 | 128 | 126 |
| /26 | 255.255.255.192 | 64 | 64 | 62 |
| /27 | 255.255.255.224 | 32 | 32 | 30 |
| /28 | 255.255.255.240 | 16 | 16 | 14 |
| /29 | 255.255.255.248 | 8 | 8 | 6 |
| /30 | 255.255.255.252 | 4 | 4 | 2 |

---

# 🧮 PART 2 — DIVIDE A /24

You have been assigned:

```text
192.168.10.0/24
```

You need:

> **Four equally sized subnets**

---

# Step 1 — Determine the New Prefix

A `/24` contains:

```text
256 addresses
```

Dividing by four:

```text
256 ÷ 4
=
64
```

A subnet containing 64 addresses is:

```text
/26
```

Therefore:

> **The new prefix is /26**

---

# Step 2 — Determine the Mask

```text
/26
=
255.255.255.192
```

---

# Step 3 — Determine the Block Size

```text
256 - 192
=
64
```

Therefore subnet boundaries occur every:

```text
64
```

---

# Step 4 — Write the Network Addresses

Start with:

```text
0
```

Add 64:

```text
0
64
128
192
```

Therefore:

```text
Subnet 1:
192.168.10.0/26

Subnet 2:
192.168.10.64/26

Subnet 3:
192.168.10.128/26

Subnet 4:
192.168.10.192/26
```

---

# 📝 Step 5 — Complete the Table Yourself

| Subnet | Network | First Host | Last Host | Broadcast |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |
| 4 | | | | |

---

# ✅ Check Your Work

| Subnet | Network | First Host | Last Host | Broadcast |
|---|---|---|---|---|
| 1 | 192.168.10.0 | 192.168.10.1 | 192.168.10.62 | 192.168.10.63 |
| 2 | 192.168.10.64 | 192.168.10.65 | 192.168.10.126 | 192.168.10.127 |
| 3 | 192.168.10.128 | 192.168.10.129 | 192.168.10.190 | 192.168.10.191 |
| 4 | 192.168.10.192 | 192.168.10.193 | 192.168.10.254 | 192.168.10.255 |

---

# 🏢 PART 3 — ASSIGN DEPARTMENTS

Assign:

```text
Subnet 1
Employees

Subnet 2
Servers

Subnet 3
Voice

Subnet 4
Guest
```

Therefore:

| Department | Network |
|---|---|
| Employees | 192.168.10.0/26 |
| Servers | 192.168.10.64/26 |
| Voice | 192.168.10.128/26 |
| Guest | 192.168.10.192/26 |

---

# 🧠 Question

Can:

```text
192.168.10.25/26
```

communicate directly as a same-subnet host with:

```text
192.168.10.75/26
```

without routing?

```text
YES / NO
```

> **NO**

They belong to different /26 networks.

---

# 🌐 PART 4 — BUILD IT IN PACKET TRACER

We'll build two of the four subnets first.

Create:

```text
PC-EMP01
PC-EMP02

SW-EMP

R-01

SW-SRV

SRV-01
SRV-02
```

Topology:

```text
PC-EMP01 ─┐
          │
PC-EMP02 ─┴─ SW-EMP
                │
               R-01
                │
              SW-SRV
              ├──── SRV-01
              └──── SRV-02
```

---

# 📍 PART 5 — EMPLOYEE SUBNET

Use:

```text
192.168.10.0/26
```

Gateway:

```text
192.168.10.1
```

Configure:

### PC-EMP01

```text
IP:
192.168.10.10

Mask:
255.255.255.192

Gateway:
192.168.10.1
```

### PC-EMP02

```text
IP:
192.168.10.20

Mask:
255.255.255.192

Gateway:
192.168.10.1
```

---

# 🖥️ Configure R-01 Employee Interface

Use:

```text
192.168.10.1
255.255.255.192
```

Make sure the interface is:

> **On**

---

# 🗄️ PART 6 — SERVER SUBNET

Use:

```text
192.168.10.64/26
```

The usable range is:

```text
192.168.10.65
through
192.168.10.126
```

We'll use:

```text
192.168.10.65
```

as the gateway.

---

# Configure R-01 Server Interface

```text
IP:
192.168.10.65

Mask:
255.255.255.192
```

Make sure the interface is:

> **On**

---

# Configure SRV-01

```text
IP:
192.168.10.70

Mask:
255.255.255.192

Gateway:
192.168.10.65
```

---

# Configure SRV-02

```text
IP:
192.168.10.80

Mask:
255.255.255.192

Gateway:
192.168.10.65
```

---

# 📋 Addressing Table

| Device | Address | Mask | Gateway |
|---|---|---|---|
| PC-EMP01 | 192.168.10.10 | 255.255.255.192 | 192.168.10.1 |
| PC-EMP02 | 192.168.10.20 | 255.255.255.192 | 192.168.10.1 |
| R-01 Employees | 192.168.10.1 | 255.255.255.192 | — |
| R-01 Servers | 192.168.10.65 | 255.255.255.192 | — |
| SRV-01 | 192.168.10.70 | 255.255.255.192 | 192.168.10.65 |
| SRV-02 | 192.168.10.80 | 255.255.255.192 | 192.168.10.65 |

---

# 🧪 PART 7 — TEST LOCAL CONNECTIVITY

From PC-EMP01:

```text
ping 192.168.10.20
```

Record:

```text
PASS / FAIL
```

Why should this work?

```text
____________________________________________________
```

> Both devices are inside `192.168.10.0/26`.

---

# 🧪 PART 8 — TEST SERVER CONNECTIVITY

From SRV-01:

```text
ping 192.168.10.80
```

Record:

```text
PASS / FAIL
```

Why?

> Both servers are inside `192.168.10.64/26`.

---

# 🚦 PART 9 — TEST ROUTING

From PC-EMP01:

```text
ping 192.168.10.70
```

Record:

```text
PASS / FAIL
```

Traffic should travel:

```text
PC-EMP01
     ↓
SW-EMP
     ↓
R-01
     ↓
SW-SRV
     ↓
SRV-01
```

---

# 🧠 Why Is the Router Needed?

Even though both addresses begin with:

```text
192.168.10
```

they're in:

> **Different /26 subnets**

This is why you must consider the:

```text
IP Address
+
Subnet Mask
```

together.

---

# 🔬 PART 10 — SIMULATION MODE

Switch Packet Tracer to:

> **Simulation Mode**

Generate traffic:

```text
PC-EMP01
     ↓
SRV-01
```

Use:

> **Capture / Forward**

Observe the router handling communication between the two subnets.

---

# 💥 PART 11 — TROUBLESHOOTING CHALLENGE

Now we're going to intentionally break the network.

---

# Challenge 1 — Wrong Mask

Change PC-EMP02 from:

```text
255.255.255.192
```

to:

```text
255.255.255.0
```

Now PC-EMP02 believes it belongs to a larger network than it actually does.

Test several destinations.

Think about:

> **Which addresses does PC-EMP02 now incorrectly believe are local?**

Restore:

```text
255.255.255.192
```

---

# Challenge 2 — Wrong Gateway

Change SRV-01's gateway from:

```text
192.168.10.65
```

to:

```text
192.168.10.100
```

Test:

```text
SRV-01 → SRV-02
```

Then:

```text
SRV-01 → PC-EMP01
```

Record:

| Test | Result |
|---|---|
| SRV-01 → SRV-02 | PASS / FAIL |
| SRV-01 → PC-EMP01 | PASS / FAIL |

Why might local communication work while remote communication fails?

```text
____________________________________________________

____________________________________________________
```

Restore:

```text
192.168.10.65
```

---

# Challenge 3 — Network Address

Configure a test device as:

```text
192.168.10.64/26
```

Is this a valid normal host address?

```text
YES / NO
```

> **NO**

It is the network address for Subnet 2.

---

# Challenge 4 — Broadcast Address

Would:

```text
192.168.10.127/26
```

normally be assigned to a host in Subnet 2?

```text
YES / NO
```

> **NO**

It is the broadcast address.

---

# 🧮 PART 12 — SUBNETTING PRACTICE

Solve these without looking at the answers.

---

# Problem 1

Given:

```text
192.168.50.100/27
```

Find:

```text
Mask:

Network:

First Host:

Last Host:

Broadcast:

Traditional Usable Hosts:
```

---

# Problem 2

Given:

```text
10.0.0.200/28
```

Find:

```text
Mask:

Network:

First Host:

Last Host:

Broadcast:

Traditional Usable Hosts:
```

---

# Problem 3

Given:

```text
172.16.1.50/29
```

Find:

```text
Mask:

Network:

First Host:

Last Host:

Broadcast:

Traditional Usable Hosts:
```

---

# Problem 4

Given:

```text
192.168.100.6/30
```

Find:

```text
Mask:

Network:

Usable Hosts:

Broadcast:
```

---

# 🛑 Stop Here Until You've Tried Them

Seriously.

Try the calculations before checking below.

---

# ✅ PRACTICE ANSWERS

## Problem 1

```text
192.168.50.100/27
```

Block:

```text
32
```

100 falls inside:

```text
96–127
```

Answer:

```text
Mask:
255.255.255.224

Network:
192.168.50.96

First:
192.168.50.97

Last:
192.168.50.126

Broadcast:
192.168.50.127

Usable:
30
```

---

# Problem 2

```text
10.0.0.200/28
```

Block:

```text
16
```

200 falls inside:

```text
192–207
```

Answer:

```text
Mask:
255.255.255.240

Network:
10.0.0.192

First:
10.0.0.193

Last:
10.0.0.206

Broadcast:
10.0.0.207

Usable:
14
```

---

# Problem 3

```text
172.16.1.50/29
```

Block:

```text
8
```

50 falls inside:

```text
48–55
```

Answer:

```text
Mask:
255.255.255.248

Network:
172.16.1.48

First:
172.16.1.49

Last:
172.16.1.54

Broadcast:
172.16.1.55

Usable:
6
```

---

# Problem 4

```text
192.168.100.6/30
```

Block:

```text
4
```

6 falls inside:

```text
4–7
```

Answer:

```text
Mask:
255.255.255.252

Network:
192.168.100.4

Hosts:
192.168.100.5
192.168.100.6

Broadcast:
192.168.100.7
```

---

# 🎓 NETWORK+ CHALLENGE

You need a subnet capable of supporting:

```text
28 devices
```

Which is the smallest traditional subnet?

### A. /28
### B. /27
### C. /26
### D. /25

`/28`:

```text
14 usable
```

`/27`:

```text
30 usable
```

> **Answer: B — /27**

---

# 🎓 Challenge 2

Which devices are on the same `/27` subnet?

```text
Device A:
192.168.1.65

Device B:
192.168.1.80

Device C:
192.168.1.100
```

The `/27` ranges include:

```text
64–95

96–127
```

Therefore:

> **A and B**

are on the same subnet.

---

# 🎓 Challenge 3

What is wrong with:

```text
IP:
192.168.10.127

Mask:
255.255.255.192
```

For the subnet:

```text
192.168.10.64/26
```

?

> `192.168.10.127` is the broadcast address.

---

# 📋 Lab Review

In this lab, you:

- Built a subnet cheat sheet
- Divided a /24 into four /26 networks
- Calculated network addresses
- Calculated broadcast addresses
- Calculated usable ranges
- Assigned subnets to departments
- Built multiple subnets in Packet Tracer
- Configured /26 subnet masks
- Configured gateways
- Routed between subnets
- Used Simulation Mode
- Created an incorrect subnet mask
- Created an incorrect gateway
- Identified network addresses
- Identified broadcast addresses
- Practiced /27
- Practiced /28
- Practiced /29
- Practiced /30
- Solved Network+ style subnetting questions

---

# 💾 Save Your Packet Tracer Lab

Save as:

```text
lab-08-subnetting-fundamentals.pkt
```

---

# 🏆 Lab Complete

You should now be able to take:

```text
192.168.10.70/26
```

and work out:

```text
Network
      ↓
First Host
      ↓
Last Host
      ↓
Broadcast
      ↓
Host Count
```

without relying entirely on a subnet calculator.

Subnet calculators are useful in real IT work.

But understanding the calculation helps you:

> **Recognize when a configuration is wrong.**

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

        ↓

🟡 NEXT:
Lesson 09 — IPv6 Fundamentals
        ↓
⬜ Lab 09 — IPv6 Fundamentals
        ↓
⬜ Lesson 10 — TCP, UDP, Ports & Protocols
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 09 — IPv6 Fundamentals**

You'll learn:

- Why IPv6 exists
- 128-bit addressing
- Hexadecimal IPv6 notation
- Address compression
- Global unicast
- Link-local addresses
- Unique local addresses
- Multicast
- Loopback
- IPv6 prefixes
- Neighbor Discovery
- SLAAC
- DHCPv6
- Dual stack
- Basic IPv6 troubleshooting

And don't worry:

> **We are not doing IPv6 subnetting the same way we just did IPv4 subnetting.**

The goal will be to understand how IPv6 addressing works and how you're likely to encounter it as an IT technician and on Network+.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**