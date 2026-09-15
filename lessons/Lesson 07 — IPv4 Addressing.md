# 📘 Lesson 07 — IPv4 Addressing

Welcome to **Lesson 07 of Networking Fundamentals**.

In Lesson 06, you learned how Ethernet and MAC addresses handle communication on the local network.

Now we're moving up to:

> 🌐 **IPv4 Addressing**

You've already seen addresses such as:

```text
192.168.10.25
```

But what does that address actually mean?

How does a computer know whether another device is:

- On the same network?
- On another network?
- Reachable directly?
- Reachable through a router?

That's what we'll begin answering in this lesson.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain what IPv4 is
- Recognize an IPv4 address
- Understand the four-octet structure
- Understand IPv4 address size
- Explain network and host portions
- Explain the purpose of a subnet mask
- Recognize CIDR notation
- Identify common private IPv4 ranges
- Explain public IPv4 addresses
- Recognize loopback addresses
- Recognize APIPA addresses
- Explain the default gateway
- Understand network addresses
- Understand broadcast addresses
- Understand usable host addresses
- Identify basic IPv4 configuration problems
- Use Windows tools to inspect IPv4 configuration
- Prepare for subnetting

---

# 🎓 Network+ Focus

IPv4 addressing is a major **CompTIA Network+ N10-009** topic.

Pay particular attention to:

- IPv4
- Private addressing
- Public addressing
- APIPA
- Loopback
- Subnet masks
- CIDR
- Default gateways
- Network addresses
- Broadcast addresses
- Host addresses
- DHCP-assigned addressing
- Static addressing
- Troubleshooting incorrect IP configuration

Don't focus only on memorizing addresses.

You need to understand:

> **What does this address tell me about the device and its network?**

---

# 🌐 What Is IPv4?

IPv4 stands for:

> **Internet Protocol Version 4**

IPv4 provides logical addressing that allows devices to communicate across IP networks.

Example:

```text
192.168.10.25
```

IPv4 operates primarily at:

> **OSI Layer 3 — Network**

and the:

> **TCP/IP Internet Layer**

---

# 🔢 IPv4 Address Size

An IPv4 address contains:

> **32 bits**

Those 32 bits are divided into:

> **Four 8-bit sections**

Each section is called an:

> **Octet**

Example:

```text
192 . 168 . 10 . 25
 ↑     ↑     ↑    ↑
Octet Octet Octet Octet
```

---

# 📦 Four Octets

Each octet can contain a decimal value from:

```text
0
```

through:

```text
255
```

Therefore this is valid:

```text
192.168.10.25
```

But this is not:

```text
192.168.300.25
```

Why?

Because:

```text
300 > 255
```

---

# 💻 IPv4 Is Really Binary

Computers don't actually interpret IPv4 addresses as decimal numbers.

They use binary.

For example:

```text
192
```

in binary is:

```text
11000000
```

An entire IPv4 address might look like:

```text
11000000.10101000.00001010.00011001
```

which represents:

```text
192.168.10.25
```

---

# 🧠 Don't Panic About Binary

You do **not** need to master binary in this lesson.

We're introducing it because:

> **Subnetting depends on understanding how bits divide networks and hosts.**

Lesson 08 will build this gradually.

---

# 🏠 Network Portion and Host Portion

An IPv4 address contains information representing:

```text
NETWORK
+
HOST
```

Conceptually:

```text
192.168.10.25

Network
192.168.10

Host
25
```

But there's an important catch:

> You cannot reliably determine the network and host portions from the IP address alone.

You also need the:

> **Subnet Mask / Prefix Length**

---

# 🎭 The Subnet Mask

Consider:

```text
IP Address:
192.168.10.25

Subnet Mask:
255.255.255.0
```

The subnet mask helps the device determine which part identifies the network and which part identifies the host.

In this simple example:

```text
192.168.10 | .25
-----------   ---
 Network      Host
```

---

# 📏 CIDR Notation

Instead of writing:

```text
255.255.255.0
```

you may see:

```text
/24
```

So:

```text
192.168.10.25/24
```

means the address is using a:

```text
24-bit network prefix
```

For now, remember:

```text
255.255.255.0
=
/24
```

We'll learn why in Lesson 08.

---

# 🏘️ A /24 Network

Consider:

```text
192.168.10.0/24
```

A typical /24 network has:

```text
Network Address:
192.168.10.0

Usable Hosts:
192.168.10.1
through
192.168.10.254

Broadcast Address:
192.168.10.255
```

---

# 🚫 Network Address

The:

```text
192.168.10.0
```

address identifies the network itself.

It isn't normally assigned to an individual host.

Think:

```text
192.168.10.0
=
Name of the network
```

---

# 📢 Broadcast Address

For this /24 example:

```text
192.168.10.255
```

is the broadcast address.

It represents communication intended for all IPv4 hosts on that subnet.

It isn't normally assigned to an individual host.

---

# 🖥️ Usable Host Addresses

That leaves:

```text
192.168.10.1
through
192.168.10.254
```

for normal host assignments in this example.

Possible devices:

```text
Router       192.168.10.1
PC-01        192.168.10.10
PC-02        192.168.10.20
Printer      192.168.10.50
Server       192.168.10.100
```

---

# 🧮 Why 254 Usable Hosts?

A /24 leaves:

> **8 host bits**

Eight bits provide:

```text
256 total addresses
```

Traditionally:

```text
256
- 1 Network Address
- 1 Broadcast Address
---------------------
254 Usable Host Addresses
```

We'll calculate this properly during subnetting.

---

# 🏠 Private IPv4 Addresses

Some IPv4 ranges are reserved for private networks.

These are extremely important to memorize.

| Private Range | CIDR |
|---|---|
| 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 |
| 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 |
| 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 |

---

# ⭐ Memorize These

```text
10.x.x.x

172.16.x.x
through
172.31.x.x

192.168.x.x
```

These ranges appear constantly in:

- Home networks
- Business networks
- Labs
- Virtual environments
- Cloud environments
- Certification questions

---

# ⚠️ Common 172 Mistake

Not every address beginning with:

```text
172
```

is private.

The private range is specifically:

```text
172.16.0.0
through
172.31.255.255
```

For example:

```text
172.20.5.10
```

is private.

But:

```text
172.40.5.10
```

is not part of the RFC 1918 private range.

---

# 🌎 Public IPv4 Addresses

Addresses that are globally routable on the public Internet are generally referred to as:

> **Public IPv4 addresses**

Your internal computer might have:

```text
192.168.1.25
```

while your Internet connection uses a public IPv4 address externally.

A router/firewall commonly performs:

> **Network Address Translation — NAT**

between private and public addressing.

We'll explore NAT more deeply later.

---

# 🏠 Why Use Private Addresses?

There aren't enough IPv4 addresses for every modern device to have a unique public IPv4 address.

Private addressing allows many internal devices to use reusable address space.

For example:

```text
PC
192.168.1.20
       │
       ▼
Router / NAT
       │
       ▼
Public IPv4
       │
       ▼
Internet
```

---

# 🔁 Loopback

The IPv4 loopback range is:

```text
127.0.0.0/8
```

The address you'll encounter most often is:

```text
127.0.0.1
```

Common name:

> **localhost**

---

# 🧪 Testing Loopback

Run:

```cmd
ping 127.0.0.1
```

You're testing communication with:

> **Your own local TCP/IP stack**

You're not testing whether your router or Internet connection works.

---

# 🧠 Remember

```text
127.0.0.1
=
Me
```

That's an easy way to remember loopback.

---

# ⚠️ APIPA

APIPA stands for:

> **Automatic Private IP Addressing**

Windows may automatically assign an address from:

```text
169.254.0.0/16
```

when it cannot obtain an IPv4 address through DHCP.

Example:

```text
169.254.25.40
```

---

# 🚨 Why APIPA Matters

Suppose a user says:

> "The network isn't working."

You run:

```cmd
ipconfig
```

and see:

```text
IPv4 Address:
169.254.32.18
```

That is a major troubleshooting clue.

The device may have failed to obtain an expected DHCP lease.

---

# 🧠 Network+ Memory Aid

```text
169.254.x.x
=
Think DHCP problem
```

It's not absolute proof that the DHCP server itself is broken, but it tells you to investigate the DHCP/configuration path.

---

# 🚪 Default Gateway

A default gateway allows a device to send traffic toward:

> **Other IP networks**

Example:

```text
PC-01

IP:
192.168.10.25

Mask:
255.255.255.0

Gateway:
192.168.10.1
```

---

# 🏠 Local Traffic

PC-01 wants to reach:

```text
192.168.10.50
```

With a /24 mask, that's on the same local network.

Conceptually:

```text
PC-01
   │
   ▼
Switch
   │
   ▼
PC-02
```

No router is required to route between those two hosts.

---

# 🌎 Remote Traffic

PC-01 wants to reach:

```text
192.168.20.50
```

That's another network.

Conceptually:

```text
PC-01
   │
   ▼
Switch
   │
   ▼
Default Gateway
   │
   ▼
Other Network
```

---

# ⭐ Default Gateway Rule

A default gateway should normally be reachable on the host's local subnet.

Example:

```text
PC:
192.168.10.25/24

Gateway:
192.168.10.1
```

makes sense.

But:

```text
PC:
192.168.10.25/24

Gateway:
192.168.50.1
```

would normally be an invalid basic configuration because that gateway isn't on the PC's local /24 network.

---

# 📝 Static IPv4 Addressing

A device can be manually configured with:

- IP address
- Subnet mask/prefix
- Default gateway
- DNS servers

This is:

> **Static Addressing**

Static addresses are commonly useful for infrastructure such as:

- Routers
- Switch management
- Servers
- Printers
- Firewalls
- Network appliances

The exact approach depends on the environment.

---

# 🤖 Dynamic IPv4 Addressing

Devices can also obtain configuration automatically through:

> **DHCP**

DHCP can provide information such as:

```text
IPv4 Address
Subnet Mask
Default Gateway
DNS Server
```

This is commonly used for:

- Laptops
- Desktops
- Phones
- Tablets
- Client devices

---

# 🔄 DHCP vs. Static

| DHCP | Static |
|---|---|
| Automatically assigned | Manually configured |
| Convenient for clients | Predictable address |
| Centralized management | Useful for infrastructure |
| Lease-based | Remains until changed |

---

# ⚠️ Duplicate IP Addresses

Two devices should not normally use the same IPv4 address on the same network simultaneously.

Example:

```text
PC-01
192.168.10.25

PC-02
192.168.10.25
```

This creates an:

> **IP Address Conflict**

Possible symptoms include:

- Intermittent connectivity
- One device losing access
- Address conflict warnings
- ARP confusion
- Unpredictable communication

---

# 🛠️ Windows IPv4 Tools

You've already used several useful commands.

## Basic Configuration

```cmd
ipconfig
```

---

## Detailed Configuration

```cmd
ipconfig /all
```

---

## PowerShell Configuration

```powershell
Get-NetIPConfiguration
```

---

## IP Addresses

```powershell
Get-NetIPAddress
```

---

## Test Local TCP/IP

```cmd
ping 127.0.0.1
```

---

## Test Gateway

```cmd
ping YOUR_GATEWAY
```

---

## Test Remote IP

```cmd
ping 8.8.8.8
```

---

# 🧭 Basic Troubleshooting Sequence

Suppose a workstation can't reach the Internet.

A simple investigation might include:

```text
1. Is the interface connected?
        ↓
2. Does it have an expected IPv4 address?
        ↓
3. Is the subnet mask correct?
        ↓
4. Is the gateway correct?
        ↓
5. Can it reach the gateway?
        ↓
6. Can it reach a remote IP?
        ↓
7. Can it resolve DNS names?
```

This isn't the only troubleshooting method, but it's a useful starting framework.

---

# 🧠 Scenario 1 — APIPA

You find:

```text
IP:
169.254.44.20

Gateway:
None
```

What should you investigate?

> **DHCP / IPv4 configuration**

---

# 🧠 Scenario 2 — Local Works, Remote Fails

A computer can reach:

```text
192.168.10.20
```

but cannot reach:

```text
192.168.20.20
```

Possible areas include:

- Default gateway
- Routing
- Router configuration
- Firewall
- Remote network

Don't immediately blame the switch.

---

# 🧠 Scenario 3 — Duplicate Address

Two printers are configured as:

```text
192.168.10.50
```

What is wrong?

> **Duplicate IPv4 address**

Each host on that network needs an appropriate unique host address.

---

# 🧠 Scenario 4 — Wrong Subnet Mask

Suppose:

```text
PC-01:
192.168.10.25/24

PC-02:
192.168.20.25/24
```

They're connected to the same Layer 2 switch.

Are they on the same IP subnet?

> **No**

A switch connection alone doesn't mean two hosts belong to the same IP network.

---

# 🗺️ Network vs. Physical Location

This distinction is important.

Two computers can sit:

> **Right next to each other**

and still belong to different IP networks.

Likewise, logical network design doesn't always match physical location.

---

# 📋 Special IPv4 Quick Reference

| Address/Range | Purpose |
|---|---|
| `10.0.0.0/8` | Private |
| `172.16.0.0/12` | Private |
| `192.168.0.0/16` | Private |
| `127.0.0.1` | Common loopback |
| `127.0.0.0/8` | Loopback range |
| `169.254.0.0/16` | IPv4 link-local/APIPA |
| `255.255.255.255` | Limited broadcast |

---

# 📋 /24 Example

Given:

```text
192.168.50.25/24
```

we can determine:

```text
Network:
192.168.50.0

Host:
192.168.50.25

Usable Range:
192.168.50.1 – 192.168.50.254

Broadcast:
192.168.50.255
```

This pattern will become extremely important in Lesson 08.

---

# 🧠 Knowledge Check

### 1.

How many bits are in an IPv4 address?

### 2.

How many octets are in an IPv4 address?

### 3.

What is the maximum decimal value of an octet?

### 4.

What subnet mask corresponds to /24?

### 5.

Is `192.168.25.10` private or public?

### 6.

Is `172.40.10.5` part of the RFC 1918 private range?

### 7.

What does `127.0.0.1` represent?

### 8.

What does a `169.254.x.x` address commonly suggest on Windows?

### 9.

What is the purpose of a default gateway?

### 10.

Can the network and host portions always be determined from the IPv4 address alone?

---

# ✅ Knowledge Check Answers

1. **32 bits**
2. **4 octets**
3. **255**
4. **255.255.255.0**
5. **Private**
6. **No**
7. **Loopback / localhost**
8. **Automatic link-local/APIPA addressing, often indicating the device did not obtain the expected DHCP configuration**
9. **To reach other IP networks**
10. **No — the subnet mask/prefix is also needed**

---

# 🎓 Network+ Challenge 1

Which address is private?

### A. `8.8.8.8`
### B. `172.20.10.5`
### C. `172.40.10.5`
### D. `1.1.1.1`

> **Answer: B**

---

# 🎓 Network+ Challenge 2

A Windows workstation unexpectedly has:

```text
169.254.10.20
```

Which service/path should be investigated early?

### A. DNS only
### B. DHCP
### C. HTTPS
### D. SSH

> **Answer: B — DHCP**

---

# 🎓 Network+ Challenge 3

Given:

```text
192.168.25.50/24
```

what is the network address?

### A. `192.168.0.0`
### B. `192.168.25.0`
### C. `192.168.25.1`
### D. `192.168.25.255`

> **Answer: B**

---

# 🎓 Network+ Challenge 4

What is the broadcast address for:

```text
192.168.25.0/24
```

### A. `192.168.25.0`
### B. `192.168.25.1`
### C. `192.168.25.254`
### D. `192.168.25.255`

> **Answer: D**

---

# 🎓 Network+ Challenge 5

A PC is configured as:

```text
IP:
192.168.10.25

Mask:
255.255.255.0

Gateway:
192.168.50.1
```

What configuration should immediately look suspicious?

> **The default gateway**

For this basic /24 configuration, the gateway isn't on the PC's local subnet.

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- IPv4 uses 32-bit addresses.
- IPv4 addresses contain four octets.
- Each octet ranges from 0–255.
- Subnet masks identify network and host portions.
- `/24` corresponds to `255.255.255.0`.
- Network addresses identify networks.
- Broadcast addresses identify subnet broadcasts.
- Host addresses identify interfaces.
- Private IPv4 ranges should be memorized.
- `127.0.0.1` is the common loopback address.
- `169.254.0.0/16` is IPv4 link-local/APIPA space.
- A default gateway provides a path toward other networks.
- DHCP can automatically provide IPv4 configuration.
- Static addressing is manually configured.
- Duplicate IPv4 addresses cause conflicts.
- Correct IPv4 configuration is fundamental to troubleshooting.

---

# 🧪 Next Step — Lab 07

Now you'll configure and troubleshoot IPv4 yourself.

You'll use:

```text
Windows
+
PowerShell
+
Cisco Packet Tracer
```

➡️ **[Lab 07 — IPv4 Addressing](../labs/lab-07-ipv4-addressing.md)**

---

# 📍 Course Progress

```text
🔵 PHASE 2 — ADDRESSING & COMMUNICATION

✅ Lesson 06 — Ethernet & MAC Addressing
✅ Lab 06

✅ Lesson 07 — IPv4 Addressing
        ↓
🟡 NEXT: Lab 07 — IPv4 Addressing
        ↓
⬜ Lesson 08 — Subnetting Fundamentals
⬜ Lab 08
        ↓
⬜ Lesson 09 — IPv6 Fundamentals
        ↓
⬜ Lesson 10 — TCP, UDP, Ports & Protocols
```

---

# ➡️ After the Lab

Next:

> **📘 Lesson 08 — Subnetting Fundamentals**

That's where you'll learn how to determine:

```text
Network Address
Host Range
Broadcast Address
Number of Hosts
Subnet Size
```

for networks beyond a simple `/24`.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**