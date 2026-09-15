# 📘 Lesson 08 — Subnetting Fundamentals

Welcome to **Lesson 08 of Networking Fundamentals**.

In Lesson 07, you learned how IPv4 addressing works.

You saw networks such as:

```text
192.168.10.0/24
```

and learned that a `/24` contains:

```text
Network Address:
192.168.10.0

Usable Hosts:
192.168.10.1 – 192.168.10.254

Broadcast:
192.168.10.255
```

But networks aren't always `/24`.

You may encounter:

```text
/25
/26
/27
/28
/29
/30
```

So how do you determine where one network ends and another begins?

That's:

> 🧮 **Subnetting**

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain why subnetting is used
- Understand network bits and host bits
- Understand CIDR prefix lengths
- Convert common CIDR prefixes to subnet masks
- Recognize common subnet masks
- Calculate addresses per subnet
- Calculate traditional usable host counts
- Determine subnet block size
- Determine network addresses
- Determine broadcast addresses
- Determine usable host ranges
- Determine whether two hosts are in the same subnet
- Understand `/30` point-to-point networks
- Recognize `/31` and `/32`
- Solve basic Network+ subnetting questions
- Troubleshoot incorrect subnet configurations

---

# 🎓 Network+ Focus

Subnetting is an important **CompTIA Network+ N10-009** skill.

You should be comfortable with:

- IPv4
- CIDR notation
- Subnet masks
- Network addresses
- Broadcast addresses
- Host ranges
- Private addressing
- Network segmentation
- Routing between subnets
- Troubleshooting subnet mismatches

For Network+, the goal isn't to become a human subnet calculator.

You should be able to look at a network and understand:

> **Which addresses belong together?**

and:

> **Where does routing become necessary?**

---

# 🧠 What Is Subnetting?

Subnetting means:

> **Dividing an IP network into smaller logical networks.**

Suppose you have:

```text
192.168.10.0/24
```

Instead of using one large network, you could divide it into smaller networks.

For example:

```text
192.168.10.0/26

192.168.10.64/26

192.168.10.128/26

192.168.10.192/26
```

You now have:

> **Four smaller subnets**

instead of one `/24`.

---

# 🏢 Why Subnet?

Imagine a company with:

```text
Employees
Servers
Printers
VoIP Phones
Guest Wi-Fi
Security Cameras
```

Putting everything into one giant network isn't always desirable.

Instead:

```text
Employees
192.168.10.0/24

Servers
192.168.20.0/24

Voice
192.168.30.0/24

Guest
192.168.40.0/24
```

or smaller subnets could be used depending on requirements.

Subnetting helps with:

- Organization
- Address conservation
- Routing
- Security design
- Broadcast control
- VLAN design
- Troubleshooting
- Network scalability

---

# 🧩 Network Bits and Host Bits

IPv4 contains:

> **32 bits**

Those bits are divided between:

```text
NETWORK BITS
+
HOST BITS
```

A `/24` means:

```text
24 Network Bits
8 Host Bits
```

Conceptually:

```text
NNNNNNNN.NNNNNNNN.NNNNNNNN.HHHHHHHH
```

---

# 📏 What Does /26 Mean?

A:

```text
/26
```

means:

```text
26 Network Bits
6 Host Bits
```

Conceptually:

```text
NNNNNNNN.NNNNNNNN.NNNNNNNN.NNHHHHHH
```

The larger the prefix:

> **The more network bits and fewer host bits.**

---

# ⭐ Important Rule

As the prefix gets larger:

```text
/24 → /25 → /26 → /27
```

the subnet gets:

> **Smaller**

and supports:

> **Fewer host addresses**

---

# 🔢 Binary Review

Each IPv4 octet contains:

> **8 bits**

The binary place values are:

| Bit | Value |
|---|---:|
| 1 | 128 |
| 2 | 64 |
| 3 | 32 |
| 4 | 16 |
| 5 | 8 |
| 6 | 4 |
| 7 | 2 |
| 8 | 1 |

Memorize:

```text
128 64 32 16 8 4 2 1
```

You'll use this constantly.

---

# 🧮 Example — 255

Binary:

```text
11111111
```

Decimal:

```text
128 + 64 + 32 + 16 + 8 + 4 + 2 + 1
=
255
```

---

# 🧮 Example — 192

Binary:

```text
11000000
```

Decimal:

```text
128 + 64
=
192
```

---

# 🧮 Example — 224

Binary:

```text
11100000
```

Decimal:

```text
128 + 64 + 32
=
224
```

---

# 📋 Common CIDR Masks

These are worth memorizing:

| CIDR | Subnet Mask |
|---|---|
| /24 | 255.255.255.0 |
| /25 | 255.255.255.128 |
| /26 | 255.255.255.192 |
| /27 | 255.255.255.224 |
| /28 | 255.255.255.240 |
| /29 | 255.255.255.248 |
| /30 | 255.255.255.252 |

---

# 🧠 Memory Pattern

Look at the final octet:

```text
/24 =   0
/25 = 128
/26 = 192
/27 = 224
/28 = 240
/29 = 248
/30 = 252
```

Notice the progression:

```text
0
128
192
224
240
248
252
```

---

# 🧮 How Many Addresses?

IPv4 has:

```text
32 total bits
```

If the network is:

```text
/26
```

then:

```text
32 - 26
=
6 host bits
```

The number of addresses is:

```text
2^6
=
64
```

So a `/26` contains:

> **64 total addresses**

---

# 🖥️ Traditional Usable Host Formula

For traditional IPv4 subnets with a network and broadcast address:

```text
2^host bits - 2
```

For `/26`:

```text
2^6 - 2

64 - 2

=
62 usable hosts
```

---

# 📋 Common Host Counts

| CIDR | Total Addresses | Traditional Usable Hosts |
|---|---:|---:|
| /24 | 256 | 254 |
| /25 | 128 | 126 |
| /26 | 64 | 62 |
| /27 | 32 | 30 |
| /28 | 16 | 14 |
| /29 | 8 | 6 |
| /30 | 4 | 2 |

This table is extremely useful for Network+.

---

# 🧱 Block Size

One of the easiest subnetting techniques is to determine the:

> **Block Size**

For common fourth-octet subnetting:

```text
Block Size
=
256 - Subnet Mask Value
```

Example `/26`:

```text
256 - 192
=
64
```

Therefore the networks occur every:

> **64 addresses**

---

# 📍 /26 Network Boundaries

Starting at 0:

```text
0
64
128
192
```

Those are the network addresses.

Therefore:

```text
192.168.10.0/26

192.168.10.64/26

192.168.10.128/26

192.168.10.192/26
```

---

# 📦 First /26

Network:

```text
192.168.10.0
```

Next network:

```text
192.168.10.64
```

Therefore the broadcast address is one address before the next network:

```text
192.168.10.63
```

Usable hosts:

```text
192.168.10.1
through
192.168.10.62
```

---

# 📦 Second /26

Network:

```text
192.168.10.64
```

Next network:

```text
192.168.10.128
```

Broadcast:

```text
192.168.10.127
```

Usable:

```text
192.168.10.65
through
192.168.10.126
```

---

# 📋 Complete /26 Breakdown

| Network | First Host | Last Host | Broadcast |
|---|---|---|---|
| 192.168.10.0 | .1 | .62 | .63 |
| 192.168.10.64 | .65 | .126 | .127 |
| 192.168.10.128 | .129 | .190 | .191 |
| 192.168.10.192 | .193 | .254 | .255 |

---

# ⭐ The Subnetting Process

When given something such as:

```text
192.168.10.70/26
```

follow this process.

### Step 1

Find the subnet mask:

```text
/26
=
255.255.255.192
```

### Step 2

Find block size:

```text
256 - 192
=
64
```

### Step 3

Write boundaries:

```text
0
64
128
192
```

### Step 4

Find where 70 fits:

```text
64 ≤ 70 < 128
```

Therefore:

```text
Network:
192.168.10.64
```

### Step 5

Next network:

```text
192.168.10.128
```

### Step 6

Broadcast:

```text
192.168.10.127
```

### Step 7

Host range:

```text
192.168.10.65
through
192.168.10.126
```

---

# 🧠 Answer

For:

```text
192.168.10.70/26
```

we have:

```text
Network:
192.168.10.64

First Host:
192.168.10.65

Last Host:
192.168.10.126

Broadcast:
192.168.10.127

Usable Hosts:
62
```

---

# 🧮 /27 Example

Given:

```text
192.168.50.75/27
```

Subnet mask:

```text
255.255.255.224
```

Block size:

```text
256 - 224
=
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

75 falls between:

```text
64
and
96
```

Therefore:

```text
Network:
192.168.50.64

Broadcast:
192.168.50.95

First Host:
192.168.50.65

Last Host:
192.168.50.94
```

---

# 🧮 /28 Example

Given:

```text
10.0.0.100/28
```

Mask:

```text
255.255.255.240
```

Block:

```text
256 - 240
=
16
```

Boundaries include:

```text
0
16
32
48
64
80
96
112
128
...
```

100 falls between:

```text
96
and
112
```

Therefore:

```text
Network:
10.0.0.96

Broadcast:
10.0.0.111

First:
10.0.0.97

Last:
10.0.0.110
```

---

# 🛣️ /30 Networks

A `/30` provides:

```text
4 total addresses
```

Traditionally:

```text
1 Network
2 Usable Hosts
1 Broadcast
```

Example:

```text
10.0.0.0/30
```

contains:

```text
Network:
10.0.0.0

Host:
10.0.0.1

Host:
10.0.0.2

Broadcast:
10.0.0.3
```

Historically, `/30` has commonly been used for point-to-point IPv4 links.

---

# 🔗 /31 Networks

You may also encounter:

```text
/31
```

on point-to-point links.

Unlike traditional subnetting, RFC 3021 allows both addresses in a `/31` to be used on supported point-to-point IPv4 links.

So don't blindly apply:

```text
2^hostbits - 2
```

to every possible IPv4 prefix.

For Network+ fundamentals, understand:

```text
/30
=
Traditional 2-host point-to-point subnet

/31
=
Efficient point-to-point addressing when supported
```

---

# 🎯 /32

A:

```text
/32
```

identifies one individual IPv4 address.

Example:

```text
192.168.10.25/32
```

You'll see `/32` used in areas such as:

- Routing
- Firewall rules
- Host routes
- Loopback interfaces

---

# 🏠 Are These Hosts on the Same Subnet?

Consider:

```text
PC-A:
192.168.10.10/26

PC-B:
192.168.10.50/26
```

The first `/26` is:

```text
192.168.10.0 – 192.168.10.63
```

Both addresses fall inside it.

Therefore:

> **Same subnet**

---

# 🌎 Different Subnets

Now:

```text
PC-A:
192.168.10.10/26

PC-B:
192.168.10.70/26
```

PC-A belongs to:

```text
192.168.10.0/26
```

PC-B belongs to:

```text
192.168.10.64/26
```

Therefore:

> **Different subnets**

A router or Layer 3 function is needed for normal communication between them.

---

# ⚠️ Same First Three Octets Does Not Mean Same Subnet

This is important.

You cannot simply say:

```text
192.168.10.x
=
Same network
```

if you're using smaller prefixes.

Example:

```text
192.168.10.10/26
```

and:

```text
192.168.10.200/26
```

are on different subnets.

The:

> **Prefix length matters.**

---

# 🏢 Practical Example

Suppose a company has:

```text
192.168.100.0/24
```

and wants four equally sized networks.

Borrowing two host bits gives:

```text
/26
```

The four networks become:

```text
192.168.100.0/26
192.168.100.64/26
192.168.100.128/26
192.168.100.192/26
```

You might assign:

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

---

# 🔀 Subnets and VLANs

Subnetting and VLANs are closely related in real networks.

A common design is:

```text
VLAN 10
Employees
192.168.10.0/24

VLAN 20
Servers
192.168.20.0/24

VLAN 30
Voice
192.168.30.0/24
```

But remember:

> **A VLAN and an IP subnet are different concepts.**

VLANs operate primarily at Layer 2.

IP subnets operate at Layer 3.

We'll explore VLANs more deeply later.

---

# 🛠️ Troubleshooting Scenario 1

PC-A:

```text
192.168.10.10/26
```

PC-B:

```text
192.168.10.70/26
```

They're plugged into the same switch.

They can't communicate directly as same-subnet hosts.

Why?

> They're in different IPv4 subnets.

---

# 🛠️ Troubleshooting Scenario 2

PC-A:

```text
192.168.10.25/24
```

PC-B:

```text
192.168.10.50/26
```

The devices have:

> **Different subnet masks**

This can cause inconsistent ideas about which destinations are local.

Incorrect subnet masks can create confusing connectivity problems.

---

# 🧠 Subnetting Cheat Table

Memorize this:

| CIDR | Mask | Block | Total | Traditional Usable |
|---|---|---:|---:|---:|
| /24 | 255.255.255.0 | 256 | 256 | 254 |
| /25 | 255.255.255.128 | 128 | 128 | 126 |
| /26 | 255.255.255.192 | 64 | 64 | 62 |
| /27 | 255.255.255.224 | 32 | 32 | 30 |
| /28 | 255.255.255.240 | 16 | 16 | 14 |
| /29 | 255.255.255.248 | 8 | 8 | 6 |
| /30 | 255.255.255.252 | 4 | 4 | 2 |

Notice:

```text
128
64
32
16
8
4
```

The subnet size halves each time the prefix increases.

---

# 🧠 Knowledge Check

### 1.

How many bits are in IPv4?

### 2.

How many host bits does `/26` leave?

### 3.

What subnet mask corresponds to `/27`?

### 4.

How many total addresses are in a `/28`?

### 5.

How many traditionally usable host addresses are in a `/28`?

### 6.

What is the block size of `/26`?

### 7.

What is the network address of `192.168.10.70/26`?

### 8.

What is its broadcast address?

### 9.

Are `192.168.10.10/26` and `192.168.10.70/26` on the same subnet?

### 10.

What is a `/32` commonly used to represent?

---

# ✅ Answers

1. **32**
2. **6**
3. **255.255.255.224**
4. **16**
5. **14**
6. **64**
7. **192.168.10.64**
8. **192.168.10.127**
9. **No**
10. **One individual IPv4 address**

---

# 🎓 Network+ Challenge 1

Given:

```text
192.168.1.100/27
```

what is the network address?

Block size:

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
```

100 falls in:

```text
96–127
```

> **Answer: 192.168.1.96**

---

# 🎓 Network+ Challenge 2

What is the broadcast address for:

```text
192.168.1.100/27
```

> **Answer: 192.168.1.127**

---

# 🎓 Network+ Challenge 3

What is the usable range?

> **192.168.1.97 – 192.168.1.126**

---

# 🎓 Network+ Challenge 4

You need a traditional subnet supporting at least:

```text
25 hosts
```

Which is the smallest choice?

### A. /28
### B. /27
### C. /26
### D. /30

`/28` provides:

```text
14
```

`/27` provides:

```text
30
```

> **Answer: B — /27**

---

# 🎓 Network+ Challenge 5

You need a traditional subnet supporting:

```text
50 hosts
```

Which is the smallest suitable prefix?

### A. /28
### B. /27
### C. /26
### D. /25

`/27`:

```text
30
```

`/26`:

```text
62
```

> **Answer: C — /26**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- Subnetting divides networks into smaller networks.
- IPv4 contains 32 bits.
- CIDR identifies the number of network bits.
- Larger prefixes create smaller subnets.
- `/24` = 255.255.255.0.
- `/25` = 255.255.255.128.
- `/26` = 255.255.255.192.
- `/27` = 255.255.255.224.
- `/28` = 255.255.255.240.
- `/29` = 255.255.255.248.
- `/30` = 255.255.255.252.
- Block size helps identify subnet boundaries.
- The network address identifies the subnet.
- The broadcast address is traditionally the last address.
- Usable host addresses fall between network and broadcast.
- `/31` can be used for supported point-to-point links.
- `/32` represents one IPv4 address.
- Hosts can share the first three octets and still be in different subnets.
- Incorrect subnet masks can cause connectivity problems.

---

# 🧪 Next Step — Lab 08

Now you'll actually divide:

```text
192.168.10.0/24
```

into smaller networks and build them in Packet Tracer.

➡️ **[Lab 08 — Subnetting Fundamentals](../labs/lab-08-subnetting-fundamentals.md)**

---

# 📍 Course Progress

```text
🔵 PHASE 2 — ADDRESSING & COMMUNICATION

✅ Lesson 06 — Ethernet & MAC Addressing
✅ Lab 06

✅ Lesson 07 — IPv4 Addressing
✅ Lab 07

✅ Lesson 08 — Subnetting Fundamentals
        ↓
🟡 NEXT: Lab 08
        ↓
⬜ Lesson 09 — IPv6 Fundamentals
⬜ Lab 09
        ↓
⬜ Lesson 10 — TCP, UDP, Ports & Protocols
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**
