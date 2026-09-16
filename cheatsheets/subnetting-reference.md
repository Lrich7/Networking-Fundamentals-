# 🧮 IPv4 Subnetting Reference

A practical subnetting reference for the **Networking Fundamentals** course and **CompTIA Network+ N10-009** study.

Use this guide when you need to quickly determine:

- Subnet masks
- CIDR prefixes
- Network addresses
- Broadcast addresses
- Usable host ranges
- Number of hosts
- Subnet boundaries
- Whether two devices are on the same subnet

> Subnetting becomes much easier when you learn the patterns instead of trying to calculate everything from scratch.

---

# 🌐 IPv4 Address Basics

An IPv4 address contains:

```text
32 bits
```

Example:

```text
192.168.10.25
```

In binary:

```text
11000000.10101000.00001010.00011001
```

Each section is called an:

> **Octet**

Each octet contains:

```text
8 bits
```

Therefore:

```text
8 + 8 + 8 + 8
=
32 bits
```

---

# 🧠 Network Bits vs. Host Bits

An IPv4 address contains two logical portions:

```text
NETWORK
+
HOST
```

The subnet mask determines where the division occurs.

Example:

```text
192.168.10.25/24
```

`/24` means:

```text
24 network bits
```

leaving:

```text
32 - 24
=
8 host bits
```

Conceptually:

```text
192 . 168 . 10 . 25
───────────────  ──
    NETWORK      HOST
```

---

# 🔢 What CIDR Means

CIDR notation tells you how many bits belong to the network prefix.

Example:

```text
192.168.10.0/24
```

means:

```text
/24
=
24 network bits
```

The equivalent subnet mask is:

```text
255.255.255.0
```

---

# ⭐ Core CIDR Table

These are the subnet sizes you should know first.

| CIDR | Subnet Mask | Total Addresses | Traditional Usable Hosts | Block Size |
|---:|---|---:|---:|---:|
| /24 | 255.255.255.0 | 256 | 254 | 256 |
| /25 | 255.255.255.128 | 128 | 126 | 128 |
| /26 | 255.255.255.192 | 64 | 62 | 64 |
| /27 | 255.255.255.224 | 32 | 30 | 32 |
| /28 | 255.255.255.240 | 16 | 14 | 16 |
| /29 | 255.255.255.248 | 8 | 6 | 8 |
| /30 | 255.255.255.252 | 4 | 2 | 4 |

> The "usable hosts" column uses the traditional rule of excluding the subnet's network and broadcast addresses.

---

# 🧠 The Pattern to Memorize

Start with:

```text
/24
=
256 addresses
```

Then every additional prefix bit cuts the address count in half:

```text
/24 → 256

/25 → 128

/26 → 64

/27 → 32

/28 → 16

/29 → 8

/30 → 4
```

Traditional usable hosts:

```text
/24 → 254

/25 → 126

/26 → 62

/27 → 30

/28 → 14

/29 → 6

/30 → 2
```

This pattern is worth memorizing.

---

# 🔢 Subnet Mask Pattern

Also memorize:

```text
/24 → 255.255.255.0

/25 → 255.255.255.128

/26 → 255.255.255.192

/27 → 255.255.255.224

/28 → 255.255.255.240

/29 → 255.255.255.248

/30 → 255.255.255.252
```

Notice the final octet:

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

# 🧮 Host Formula

Traditional IPv4 subnet host calculation:

```text
2^h - 2
```

where:

```text
h
=
number of host bits
```

Example:

```text
/27
```

IPv4 contains:

```text
32 bits
```

Therefore:

```text
32 - 27
=
5 host bits
```

Calculate:

```text
2^5
=
32 total addresses
```

Traditional usable hosts:

```text
32 - 2
=
30
```

Therefore:

```text
/27
=
30 usable hosts
```

---

# 🚫 Why Subtract 2?

In a traditional IPv4 subnet:

### First Address

Used as the:

> **Network address**

### Last Address

Used as the:

> **Broadcast address**

Example:

```text
192.168.10.0/24
```

Network:

```text
192.168.10.0
```

Broadcast:

```text
192.168.10.255
```

Traditional host range:

```text
192.168.10.1
through
192.168.10.254
```

---

# 🧱 Block Size Trick

One of the fastest subnetting methods is:

```text
256 - subnet mask octet
```

Example:

```text
/27
```

Mask:

```text
255.255.255.224
```

Calculate:

```text
256 - 224
=
32
```

Therefore subnet boundaries occur every:

```text
32 addresses
```

---

# 🧮 `/27` Boundaries

Starting at zero:

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

These are the network addresses in the final octet.

So:

```text
192.168.1.0/27
```

is followed by:

```text
192.168.1.32/27
```

which is followed by:

```text
192.168.1.64/27
```

and so on.

---

# ⭐ The Four Things You Usually Need

For most subnetting questions, determine:

```text
1. Network Address

2. First Usable Host

3. Last Usable Host

4. Broadcast Address
```

A useful pattern is:

```text
NETWORK
   ↓
+ 1
   ↓
FIRST HOST
   ↓
...
   ↓
LAST HOST
   ↓
+ 1
   ↓
BROADCAST
   ↓
+ 1
   ↓
NEXT NETWORK
```

---

# 🧮 Example 1 — `/24`

Given:

```text
192.168.10.25/24
```

Mask:

```text
255.255.255.0
```

Network:

```text
192.168.10.0
```

First host:

```text
192.168.10.1
```

Last host:

```text
192.168.10.254
```

Broadcast:

```text
192.168.10.255
```

Next network:

```text
192.168.11.0
```

---

# 🧮 Example 2 — `/25`

Given:

```text
192.168.10.75/25
```

Mask:

```text
255.255.255.128
```

Block size:

```text
128
```

Networks:

```text
192.168.10.0

192.168.10.128
```

`75` falls between:

```text
0
and
127
```

Therefore:

Network:

```text
192.168.10.0
```

First host:

```text
192.168.10.1
```

Last host:

```text
192.168.10.126
```

Broadcast:

```text
192.168.10.127
```

---

# 🧮 Example 3 — `/26`

Given:

```text
192.168.10.100/26
```

Mask:

```text
255.255.255.192
```

Block size:

```text
256 - 192
=
64
```

Subnet boundaries:

```text
0
64
128
192
```

`100` falls between:

```text
64
and
127
```

Therefore:

Network:

```text
192.168.10.64
```

First host:

```text
192.168.10.65
```

Last host:

```text
192.168.10.126
```

Broadcast:

```text
192.168.10.127
```

Next network:

```text
192.168.10.128
```

---

# 🧮 Example 4 — `/27`

Given:

```text
192.168.1.70/27
```

Mask:

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

`70` falls between:

```text
64
and
95
```

Therefore:

Network:

```text
192.168.1.64
```

First host:

```text
192.168.1.65
```

Last host:

```text
192.168.1.94
```

Broadcast:

```text
192.168.1.95
```

Next network:

```text
192.168.1.96
```

---

# 🧮 Example 5 — `/28`

Given:

```text
192.168.50.77/28
```

Mask:

```text
255.255.255.240
```

Block size:

```text
256 - 240
=
16
```

Boundaries:

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
144
160
176
192
208
224
240
```

`77` falls in:

```text
64–79
```

Therefore:

Network:

```text
192.168.50.64
```

First host:

```text
192.168.50.65
```

Last host:

```text
192.168.50.78
```

Broadcast:

```text
192.168.50.79
```

---

# 🧮 Example 6 — `/29`

Given:

```text
10.10.10.18/29
```

Mask:

```text
255.255.255.248
```

Block size:

```text
256 - 248
=
8
```

Boundaries include:

```text
0
8
16
24
32
40
...
```

`18` falls in:

```text
16–23
```

Therefore:

Network:

```text
10.10.10.16
```

First host:

```text
10.10.10.17
```

Last host:

```text
10.10.10.22
```

Broadcast:

```text
10.10.10.23
```

---

# 🧮 Example 7 — `/30`

Given:

```text
10.0.0.6/30
```

Mask:

```text
255.255.255.252
```

Block size:

```text
4
```

Boundaries:

```text
0
4
8
12
16
20
...
```

`6` falls in:

```text
4–7
```

Therefore:

Network:

```text
10.0.0.4
```

First host:

```text
10.0.0.5
```

Last host:

```text
10.0.0.6
```

Broadcast:

```text
10.0.0.7
```

Traditional usable hosts:

```text
2
```

---

# ⚡ Quick Boundary Tables

## `/25`

Block:

```text
128
```

Networks:

```text
0
128
```

---

## `/26`

Block:

```text
64
```

Networks:

```text
0
64
128
192
```

---

## `/27`

Block:

```text
32
```

Networks:

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

---

## `/28`

Block:

```text
16
```

Networks:

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
144
160
176
192
208
224
240
```

---

## `/29`

Block:

```text
8
```

Networks:

```text
0
8
16
24
32
40
48
56
64
72
80
88
96
104
112
120
128
136
144
152
160
168
176
184
192
200
208
216
224
232
240
248
```

---

## `/30`

Block:

```text
4
```

Networks:

```text
0
4
8
12
16
20
24
28
32
36
...
```

---

# 🧠 Fast Exam Method

If given:

```text
192.168.1.147/27
```

### Step 1 — Find Mask

```text
/27
=
255.255.255.224
```

### Step 2 — Find Block

```text
256 - 224
=
32
```

### Step 3 — Find Boundaries

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

### Step 4 — Locate 147

```text
128 < 147 < 160
```

Therefore:

Network:

```text
192.168.1.128
```

Next network:

```text
192.168.1.160
```

### Step 5 — Broadcast

One less than next network:

```text
192.168.1.159
```

### Step 6 — Hosts

First:

```text
192.168.1.129
```

Last:

```text
192.168.1.158
```

Done.

---

# 🔍 Same Subnet or Different Subnet?

Example:

```text
PC-A
192.168.10.20/24

PC-B
192.168.10.200/24
```

Both are in:

```text
192.168.10.0/24
```

Therefore:

> **Same subnet**

They can communicate locally at Layer 2, assuming VLAN/security/connectivity allows it.

---

# 🔍 Different Subnet Example

```text
PC-A
192.168.10.20/24

PC-B
192.168.20.20/24
```

Networks:

```text
PC-A
192.168.10.0/24

PC-B
192.168.20.0/24
```

Therefore:

> **Different subnets**

Layer 3 routing is required.

---

# ⚠️ The Mask Changes Everything

Consider:

```text
192.168.10.20

192.168.10.200
```

With:

```text
/24
```

they are on the same subnet.

But with:

```text
/25
```

they are not.

Why?

`/25` networks are:

```text
192.168.10.0–127

192.168.10.128–255
```

So:

```text
192.168.10.20
```

belongs to:

```text
192.168.10.0/25
```

while:

```text
192.168.10.200
```

belongs to:

```text
192.168.10.128/25
```

> Never determine whether two IPv4 addresses are local by looking only at the address. You need the subnet mask/prefix.

---

# 🏠 Private IPv4 Ranges

Know these:

```text
10.0.0.0/8
```

Range:

```text
10.0.0.0
through
10.255.255.255
```

---

```text
172.16.0.0/12
```

Range:

```text
172.16.0.0
through
172.31.255.255
```

---

```text
192.168.0.0/16
```

Range:

```text
192.168.0.0
through
192.168.255.255
```

These are private IPv4 address spaces.

---

# 🚨 APIPA

Windows may automatically assign an IPv4 address from:

```text
169.254.0.0/16
```

when normal DHCP configuration cannot be obtained.

If you unexpectedly see:

```text
169.254.x.x
```

think:

> **Investigate DHCP/connectivity.**

Possible causes:

```text
DHCP server unavailable

Wrong VLAN

DHCP relay failure

Switch port issue

Wi-Fi problem

Physical connectivity issue
```

---

# 🔁 Loopback

IPv4 loopback range:

```text
127.0.0.0/8
```

Most commonly:

```text
127.0.0.1
```

Think:

> **This computer**

Test:

```cmd
ping 127.0.0.1
```

---

# 📢 Network vs. Broadcast vs. Host

Example:

```text
192.168.5.64/27
```

Network:

```text
192.168.5.64
```

Hosts:

```text
192.168.5.65
through
192.168.5.94
```

Broadcast:

```text
192.168.5.95
```

Think:

```text
64
NETWORK

65
FIRST HOST

...

94
LAST HOST

95
BROADCAST

96
NEXT NETWORK
```

---

# 🧮 Choosing a Subnet Size

Suppose you need:

```text
25 hosts
```

Check the table:

```text
/28
=
14 usable
```

Too small.

```text
/27
=
30 usable
```

Large enough.

Therefore:

> **/27**

---

# 🧮 Another Host Requirement

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

Large enough.

Therefore:

> **/26**

---

# ⭐ Host Requirement Table

| Need Up To | Traditional Subnet Choice |
|---:|---:|
| 2 hosts | /30 |
| 6 hosts | /29 |
| 14 hosts | /28 |
| 30 hosts | /27 |
| 62 hosts | /26 |
| 126 hosts | /25 |
| 254 hosts | /24 |

---

# 🧩 VLSM

VLSM means:

> **Variable Length Subnet Masking**

It allows different subnet sizes to be used within an address space.

Suppose you have:

```text
192.168.10.0/24
```

and need networks for:

```text
Employees
100 hosts

Servers
25 hosts

Printers
10 hosts

WAN
2 hosts
```

You do not need to give every network a `/25`.

You can allocate different sizes.

For example:

```text
Employees
/25
126 usable
```

```text
Servers
/27
30 usable
```

```text
Printers
/28
14 usable
```

```text
WAN
/30
2 usable
```

This uses the address space more efficiently.

---

# 🧠 VLSM Rule

When designing VLSM:

> **Allocate the largest subnet first.**

Order:

```text
Largest
   ↓
Next Largest
   ↓
Next Largest
   ↓
Smallest
```

This makes address allocation easier and reduces fragmentation of the available space.

---

# 🏢 Practical VLAN Example

Suppose an office uses:

```text
192.168.0.0/16
```

You might design:

```text
VLAN 10
Employees
192.168.10.0/24
```

```text
VLAN 20
Servers
192.168.20.0/24
```

```text
VLAN 30
Printers
192.168.30.0/24
```

```text
VLAN 40
Voice
192.168.40.0/24
```

```text
VLAN 50
Guests
192.168.50.0/24
```

```text
VLAN 99
Management
192.168.99.0/24
```

This is easy for humans to recognize and troubleshoot.

---

# 🚪 Gateway Planning

A common convention is to use the first usable address as the gateway.

Example:

```text
Network:
192.168.10.0/24
```

Gateway:

```text
192.168.10.1
```

Clients:

```text
192.168.10.2
through
192.168.10.254
```

But:

> The gateway does not technically have to be `.1`.

Organizations can use another valid host address according to their design standards.

---

# 📦 DHCP Planning

Example:

```text
Network:
192.168.10.0/24

Gateway:
192.168.10.1

Infrastructure:
192.168.10.2–20

DHCP:
192.168.10.50–200

Reserved:
192.168.10.201–254
```

Planning address ranges makes troubleshooting much easier.

---

# 🧠 Binary Values

Each IPv4 octet uses these bit values:

```text
128 64 32 16 8 4 2 1
```

Example:

```text
192
```

Binary:

```text
128 + 64
=
192
```

Therefore:

```text
11000000
```

---

# 🔢 Important Binary Mask Values

| Binary | Decimal |
|---|---:|
| 00000000 | 0 |
| 10000000 | 128 |
| 11000000 | 192 |
| 11100000 | 224 |
| 11110000 | 240 |
| 11111000 | 248 |
| 11111100 | 252 |
| 11111110 | 254 |
| 11111111 | 255 |

This explains the familiar mask sequence:

```text
0
128
192
224
240
248
252
254
255
```

---

# 🧠 CIDR Beyond `/24`

The same principles work outside the fourth octet.

Example:

```text
172.16.35.10/20
```

`/20` mask:

```text
255.255.240.0
```

The interesting octet is the third octet:

```text
240
```

Block size:

```text
256 - 240
=
16
```

Third-octet boundaries:

```text
0
16
32
48
64
80
...
```

`35` falls between:

```text
32
and
47
```

Therefore the network is:

```text
172.16.32.0/20
```

Next network:

```text
172.16.48.0
```

Broadcast:

```text
172.16.47.255
```

Traditional host range:

```text
172.16.32.1
through
172.16.47.254
```

---

# 📋 Expanded CIDR Reference

| CIDR | Mask | Total Addresses | Traditional Usable Hosts |
|---:|---|---:|---:|
| /16 | 255.255.0.0 | 65,536 | 65,534 |
| /17 | 255.255.128.0 | 32,768 | 32,766 |
| /18 | 255.255.192.0 | 16,384 | 16,382 |
| /19 | 255.255.224.0 | 8,192 | 8,190 |
| /20 | 255.255.240.0 | 4,096 | 4,094 |
| /21 | 255.255.248.0 | 2,048 | 2,046 |
| /22 | 255.255.252.0 | 1,024 | 1,022 |
| /23 | 255.255.254.0 | 512 | 510 |
| /24 | 255.255.255.0 | 256 | 254 |
| /25 | 255.255.255.128 | 128 | 126 |
| /26 | 255.255.255.192 | 64 | 62 |
| /27 | 255.255.255.224 | 32 | 30 |
| /28 | 255.255.255.240 | 16 | 14 |
| /29 | 255.255.255.248 | 8 | 6 |
| /30 | 255.255.255.252 | 4 | 2 |

---

# ⚠️ `/31` and `/32`

You may encounter these even though they don't follow the traditional host-count table.

## `/31`

Mask:

```text
255.255.255.254
```

A `/31` contains:

```text
2 addresses
```

It can be used on point-to-point links under modern networking standards where both addresses are treated as endpoints.

---

## `/32`

Mask:

```text
255.255.255.255
```

Represents:

```text
One IPv4 address
```

Common uses include:

```text
Host routes

Loopback interfaces

Routing entries
```

---

# 🧠 Subnetting Question Checklist

When given an address such as:

```text
192.168.1.173/27
```

ask:

### 1. What is the subnet mask?

```text
255.255.255.224
```

### 2. What is the block size?

```text
32
```

### 3. What are the boundaries?

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

### 4. Where does 173 fall?

```text
160–191
```

### 5. Network?

```text
192.168.1.160
```

### 6. Broadcast?

```text
192.168.1.191
```

### 7. First host?

```text
192.168.1.161
```

### 8. Last host?

```text
192.168.1.190
```

---

# 🎯 Fast Mental Subnetting

Try to recognize these immediately:

```text
/25
128-address blocks
```

```text
/26
64-address blocks
```

```text
/27
32-address blocks
```

```text
/28
16-address blocks
```

```text
/29
8-address blocks
```

```text
/30
4-address blocks
```

If you know the block size, many subnetting questions become:

> **Find which block contains the IP address.**

---

# 🧪 Practice 1

Given:

```text
192.168.1.140/26
```

What are the:

```text
Network?

First Host?

Last Host?

Broadcast?
```

### Answer

`/26` block size:

```text
64
```

Boundaries:

```text
0
64
128
192
```

140 belongs to:

```text
128–191
```

Therefore:

```text
Network:
192.168.1.128

First:
192.168.1.129

Last:
192.168.1.190

Broadcast:
192.168.1.191
```

---

# 🧪 Practice 2

Given:

```text
10.0.0.203/28
```

### Answer

`/28` block:

```text
16
```

Boundaries near 203:

```text
192
208
```

Therefore:

```text
Network:
10.0.0.192

First:
10.0.0.193

Last:
10.0.0.206

Broadcast:
10.0.0.207
```

---

# 🧪 Practice 3

Given:

```text
172.16.10.59/29
```

### Answer

`/29` block:

```text
8
```

Boundaries:

```text
56
64
```

Therefore:

```text
Network:
172.16.10.56

First:
172.16.10.57

Last:
172.16.10.62

Broadcast:
172.16.10.63
```

---

# 🧪 Practice 4

Are these devices on the same subnet?

```text
PC-A:
192.168.1.50/26

PC-B:
192.168.1.100/26
```

`/26` boundaries:

```text
0
64
128
192
```

PC-A belongs to:

```text
192.168.1.0/26
```

PC-B belongs to:

```text
192.168.1.64/26
```

Answer:

> **No — they are on different subnets.**

A Layer 3 device is required for communication between them.

---

# 🧪 Practice 5

Are these devices on the same subnet?

```text
PC-A:
192.168.1.70/27

PC-B:
192.168.1.90/27
```

`/27` block:

```text
32
```

Both addresses fall inside:

```text
64–95
```

Answer:

> **Yes — both are in 192.168.1.64/27.**

---

# 🎓 Network+ Exam Tips

## Memorize `/24` through `/30`

These are the most useful subnet sizes for quick calculations.

---

## Don't Forget the Mask

Never decide whether two IPv4 addresses are on the same subnet based only on the address.

Always consider:

```text
IP Address
+
Subnet Mask
```

---

## Find the Block

For many subnetting questions:

```text
MASK
 ↓
BLOCK SIZE
 ↓
BOUNDARIES
 ↓
FIND IP
 ↓
NETWORK
 ↓
BROADCAST
 ↓
HOST RANGE
```

---

## Don't Rush the Broadcast Address

Remember:

> **Broadcast = one address before the next subnet.**

Example:

```text
Current network:
192.168.1.64

Next network:
192.168.1.96
```

Therefore:

```text
Broadcast:
192.168.1.95
```

---

## Don't Confuse Broadcast and Last Host

If:

```text
Broadcast:
192.168.1.95
```

then:

```text
Last traditional usable host:
192.168.1.94
```

---

# 🏆 Subnetting Mental Model

When you see:

```text
192.168.10.77/27
```

don't panic.

Think:

```text
/27
 ↓
255.255.255.224
 ↓
256 - 224
 ↓
32
 ↓
Boundaries:
0 32 64 96...
 ↓
77 belongs to 64–95
 ↓
Network = 64
 ↓
Broadcast = 95
 ↓
Hosts = 65–94
```

That's subnetting.

The more often you practice the pattern, the less math you need to consciously perform.

---

# ⭐ Must-Memorize Mini Table

If you memorize only one table from this file, make it this one:

| CIDR | Mask Ending | Block | Traditional Hosts |
|---:|---:|---:|---:|
| /25 | 128 | 128 | 126 |
| /26 | 192 | 64 | 62 |
| /27 | 224 | 32 | 30 |
| /28 | 240 | 16 | 14 |
| /29 | 248 | 8 | 6 |
| /30 | 252 | 4 | 2 |

And remember:

```text
/24
=
255.255.255.0
=
254 traditional usable hosts
```

---

# 📚 Course Navigation

➡️ **[Cheat Sheet](cheat-sheet.md)**

➡️ **[Exam Tips](exam-tips.md)**

➡️ **[Command Reference](command-reference.md)**

➡️ **[Glossary](glossary.md)**

➡️ **[Return to Main README](../README.md)**

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**