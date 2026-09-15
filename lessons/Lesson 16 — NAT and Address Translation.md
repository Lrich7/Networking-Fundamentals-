# 📘 Lesson 16 — NAT and Address Translation

Welcome to **Lesson 16 of Networking Fundamentals**.

So far, most of the networks we've built have used addresses such as:

```text
192.168.10.0/24
192.168.20.0/24
10.0.0.0/30
```

These are **private IPv4 addresses**.

They work perfectly well inside private networks, but they are not normally routed across the public Internet.

That creates an important question:

> How can hundreds of private devices access the Internet without every device having its own public IPv4 address?

One major part of the answer is:

> **NAT — Network Address Translation**

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain NAT
- Distinguish private and public IPv4 addresses
- Identify RFC 1918 private IPv4 ranges
- Explain inside and outside networks
- Understand inside local and inside global addresses
- Explain static NAT
- Explain dynamic NAT
- Explain PAT
- Explain NAT overload
- Understand why PAT uses port numbers
- Read a basic NAT translation table
- Configure basic static NAT on Cisco IOS
- Configure PAT using an outside interface
- Configure PAT using an address pool
- Verify NAT operation
- Troubleshoot common NAT failures
- Explain what NAT does and does not provide
- Recognize NAT-related Network+ concepts

---

# 🎓 Network+ Focus

For **CompTIA Network+ N10-009**, pay particular attention to:

- NAT
- PAT
- Private IPv4
- Public IPv4
- Static NAT
- Dynamic NAT
- Port translation
- Inside vs. outside
- IPv4 address conservation
- NAT troubleshooting

---

# 🌐 Public vs. Private IPv4

IPv4 provides approximately:

```text
2^32
=
4.29 billion addresses
```

That sounded enormous when IPv4 was created.

Today, it isn't.

Computers, phones, servers, cameras, printers, tablets, IoT devices, cloud systems, and other equipment all require network addressing.

One way IPv4 networks conserve globally unique addresses is through:

> **Private IPv4 addressing + NAT**

---

# 🏠 Private IPv4 Addresses

Private IPv4 addresses are intended for use inside private networks.

The RFC 1918 ranges are:

| Range | CIDR |
|---|---|
| 10.0.0.0 – 10.255.255.255 | `10.0.0.0/8` |
| 172.16.0.0 – 172.31.255.255 | `172.16.0.0/12` |
| 192.168.0.0 – 192.168.255.255 | `192.168.0.0/16` |

Examples:

```text
10.20.30.40
172.20.5.10
192.168.10.25
```

are private IPv4 addresses.

---

# ⭐ Network+ Memory Tip

Memorize:

```text
10.0.0.0/8

172.16.0.0/12

192.168.0.0/16
```

Be careful with the middle range.

It is:

```text
172.16.0.0
through
172.31.255.255
```

Not every `172.x.x.x` address is private.

---

# 🌎 Public IPv4 Addresses

Public IPv4 addresses are globally unique addresses intended for routing on the public Internet.

Conceptually:

```text
PRIVATE NETWORK

192.168.10.10
192.168.10.20
192.168.10.30
        │
        ▼
     ROUTER
        │
        ▼
PUBLIC ADDRESS
        │
        ▼
    INTERNET
```

---

# 🚫 Private Addresses and the Internet

Suppose PC-01 has:

```text
192.168.10.25
```

It cannot simply send traffic across the Internet using that private address as though it were globally unique.

Why?

Because many organizations can use:

```text
192.168.10.25
```

at the same time.

Private addresses are reusable.

---

# 🏢 Example

Company A:

```text
192.168.10.25
```

Company B:

```text
192.168.10.25
```

Home Network:

```text
192.168.10.25
```

All can use the same private address internally.

Their edge devices can translate internal traffic to appropriate public addressing when communicating externally.

---

# 🔄 What Is NAT?

NAT stands for:

> **Network Address Translation**

NAT modifies IP addressing information as traffic moves between networks.

A common example is translating:

```text
Private IPv4
        ↓
Public IPv4
```

for Internet access.

---

# 🧠 Simple NAT Example

PC-01:

```text
192.168.10.25
```

sends traffic toward an Internet server.

At the NAT router:

```text
Inside Address:
192.168.10.25

        ↓ NAT ↓

Outside-facing Public Address:
203.0.113.5
```

The external server sees communication associated with:

```text
203.0.113.5
```

rather than the internal private address.

> The `203.0.113.0/24` range is reserved for documentation and examples. We use it in labs so we do not pretend to own a real public address.

---

# 🏠 Inside and Outside

NAT commonly refers to two sides:

```text
INSIDE
Private Network

        │
        ▼
   NAT ROUTER
        │
        ▼

OUTSIDE
External Network
```

For a small business:

```text
Inside
=
LAN

Outside
=
ISP / Internet
```

---

# 📛 NAT Terminology

Cisco NAT terminology can initially look confusing.

Two important terms are:

## Inside Local

The address of the inside device as it appears on the inside network.

Example:

```text
192.168.10.25
```

## Inside Global

The address representing that inside device to the outside network.

Example:

```text
203.0.113.5
```

Conceptually:

```text
INSIDE LOCAL
192.168.10.25

      ↓ NAT ↓

INSIDE GLOBAL
203.0.113.5
```

---

# 📋 NAT Terminology Quick Reference

| Term | Meaning |
|---|---|
| Inside Local | Inside host address before translation |
| Inside Global | Address representing the inside host externally |
| Inside | Internal/private side |
| Outside | External/public side |

Cisco also defines **outside local** and **outside global** addresses, but inside local and inside global are the most important starting concepts for our labs.

---

# 🔢 Types of NAT

Three important NAT concepts are:

```text
Static NAT

Dynamic NAT

PAT
```

Let's examine each.

---

# 1️⃣ Static NAT

Static NAT creates a fixed:

> **One-to-one translation**

Example:

```text
192.168.20.10
        ↕
203.0.113.10
```

Every time:

```text
192.168.20.10
```

is translated, it uses:

```text
203.0.113.10
```

---

# 🏢 Static NAT Use Case

Imagine an internal server:

```text
WEB-01
192.168.20.10
```

that must be represented externally by:

```text
203.0.113.10
```

A static mapping can associate the two.

---

# ⚙️ Cisco Static NAT Example

Identify the inside interface:

```text
interface gigabitethernet 0/0
 ip nat inside
```

Identify the outside interface:

```text
interface gigabitethernet 0/1
 ip nat outside
```

Create the translation:

```text
ip nat inside source static 192.168.20.10 203.0.113.10
```

---

# 🔍 Verify Static NAT

Use:

```text
show ip nat translations
```

and:

```text
show ip nat statistics
```

---

# 2️⃣ Dynamic NAT

Dynamic NAT uses:

> **A pool of available addresses**

Instead of permanently assigning one translation to one host, inside hosts can receive temporary translations from the pool.

Example:

```text
INSIDE HOSTS

192.168.10.10
192.168.10.11
192.168.10.12

        ↓

PUBLIC POOL

203.0.113.10
203.0.113.11
203.0.113.12
```

---

# ⚠️ Dynamic NAT Limitation

Suppose:

```text
100 internal devices
```

need external access.

But your dynamic NAT pool contains:

```text
5 public addresses
```

Only a limited number of simultaneous translations can use those addresses.

That is one reason PAT became extremely important.

---

# 3️⃣ PAT

PAT stands for:

> **Port Address Translation**

PAT allows many internal devices to share a public IPv4 address by distinguishing connections using transport-layer port information.

PAT is often called:

> **NAT Overload**

---

# ⭐ NAT vs. PAT

Simplified:

```text
NAT
Changes Address Information

PAT
Changes Address Information
+
Uses Port Information
```

---

# 🏢 PAT Example

Internal devices:

```text
PC-01
192.168.10.10

PC-02
192.168.10.20

PC-03
192.168.10.30
```

All access the Internet through:

```text
203.0.113.5
```

Conceptually:

```text
192.168.10.10:50001
        ↓
203.0.113.5:30001


192.168.10.20:50001
        ↓
203.0.113.5:30002


192.168.10.30:50001
        ↓
203.0.113.5:30003
```

The router keeps track of the translations.

---

# 📋 Translation Table

Conceptually:

| Inside Local | Inside Global |
|---|---|
| 192.168.10.10:50001 | 203.0.113.5:30001 |
| 192.168.10.20:50001 | 203.0.113.5:30002 |
| 192.168.10.30:50001 | 203.0.113.5:30003 |

When response traffic returns:

```text
203.0.113.5:30002
```

the router knows it belongs to:

```text
192.168.10.20:50001
```

---

# 🧠 Why PAT Matters

PAT allows:

```text
Many Private Devices
        ↓
One or Few Public IPv4 Addresses
```

This is extremely common in:

- Homes
- Small businesses
- Enterprise networks
- Branch offices

---

# 🏠 Your Home Router

Your home network might contain:

```text
Laptop
Phone
Tablet
TV
Game Console
Printer
Camera
```

with private addresses such as:

```text
192.168.1.x
```

Yet your ISP may provide your router with one public IPv4 address.

PAT allows those internal devices to share that outside address for outbound connections.

---

# 🔀 PAT With an Interface Address

A common Cisco configuration uses the router's outside interface address.

Example:

```text
access-list 1 permit 192.168.10.0 0.0.0.255
```

Then:

```text
ip nat inside source list 1 interface gigabitethernet 0/1 overload
```

The key word:

```text
overload
```

enables PAT behavior.

---

# 🧠 Wildcard Mask

Notice:

```text
192.168.10.0 0.0.0.255
```

This uses a:

> **Wildcard mask**

For:

```text
255.255.255.0
```

the corresponding wildcard is:

```text
0.0.0.255
```

You will see wildcard masks frequently in Cisco ACL configuration.

We'll work with ACLs more deeply later in the security portion of the course.

---

# 🏗️ Full PAT Example

Inside network:

```text
192.168.10.0/24
```

Outside router address:

```text
203.0.113.2/30
```

Configuration:

```text
enable
configure terminal
```

Inside interface:

```text
interface gigabitethernet 0/0
 ip nat inside
 exit
```

Outside interface:

```text
interface gigabitethernet 0/1
 ip nat outside
 exit
```

Identify inside addresses:

```text
access-list 1 permit 192.168.10.0 0.0.0.255
```

Configure PAT:

```text
ip nat inside source list 1 interface gigabitethernet 0/1 overload
```

---

# 🔍 Verify PAT

Generate traffic from an inside client.

Then:

```text
show ip nat translations
```

You may see information representing:

```text
Inside Local
Inside Global
Outside Local
Outside Global
```

---

# 📊 NAT Statistics

Use:

```text
show ip nat statistics
```

This can show information such as:

- Inside interfaces
- Outside interfaces
- Translation counts
- NAT configuration information

---

# 🧹 Clearing NAT Translations

In a lab environment, dynamic translations can be cleared with:

```text
clear ip nat translation *
```

Use commands like this carefully on real production equipment.

---

# 🏊 PAT Using a Pool

PAT can also use a NAT pool.

Example:

```text
ip nat pool PUBLIC 203.0.113.10 203.0.113.12 netmask 255.255.255.0
```

Then:

```text
access-list 1 permit 192.168.10.0 0.0.0.255
```

and:

```text
ip nat inside source list 1 pool PUBLIC overload
```

Now multiple internal hosts can share addresses from the pool using PAT.

---

# 📋 Static NAT vs. Dynamic NAT vs. PAT

| Feature | Static NAT | Dynamic NAT | PAT |
|---|---|---|---|
| Mapping | Fixed | Temporary | Address + ports |
| Relationship | 1:1 | Pool-based | Many:1 or many:few |
| Conserves public IPv4 | Limited | Some | Very effectively |
| Common outbound Internet access | Less common | Less common | Very common |

---

# 🔙 Return Traffic

NAT must maintain enough translation information to return response traffic to the correct internal host.

Conceptually:

```text
PC-01
192.168.10.10
      │
      ▼
NAT ROUTER
      │
203.0.113.5
      │
      ▼
SERVER
```

Response:

```text
SERVER
      │
      ▼
203.0.113.5
      │
NAT TABLE
      │
      ▼
192.168.10.10
```

---

# 🚪 NAT and Inbound Connections

Outbound PAT works naturally because:

> The inside device starts the connection and creates a translation.

Unsolicited inbound communication is different.

The NAT device needs to know:

> **Which internal device should receive it?**

This can involve:

- Static NAT
- Static PAT
- Port forwarding
- Other firewall/NAT policies

---

# 🚪 Port Forwarding

A home or small-business router might have one public address:

```text
203.0.113.5
```

and an internal web server:

```text
192.168.20.10
```

A port-forwarding rule could conceptually say:

```text
203.0.113.5:443
        ↓
192.168.20.10:443
```

This is a form of static port translation.

---

# 🔐 NAT Is Not a Firewall

This distinction is important.

NAT changes addressing information.

A firewall enforces:

> **Traffic policy**

It is common for a device to perform both functions:

```text
Firewall
+
Router
+
NAT
```

but the concepts are not identical.

Do not think:

> **NAT automatically equals security.**

---

# 🧱 NAT and Network Design

A small-business edge may look like:

```text
EMPLOYEE VLAN
192.168.10.0/24
        │
        │
SERVER VLAN
192.168.20.0/24
        │
        ▼
ROUTER / FIREWALL
        │
      NAT/PAT
        │
        ▼
       ISP
        │
        ▼
    INTERNET
```

This is getting much closer to a real business network.

---

# 🔄 NAT and Routing

NAT does not replace routing.

The router still needs to know:

> **Where traffic should go.**

Typical outbound traffic requires:

```text
Client IP Configuration
        ↓
Default Gateway
        ↓
Routing
        ↓
NAT
        ↓
ISP
```

---

# 🛣️ Default Route

An edge router commonly has a default route pointing toward the ISP.

Conceptually:

```text
0.0.0.0/0
        ↓
ISP
```

Cisco example:

```text
ip route 0.0.0.0 0.0.0.0 203.0.113.1
```

This says:

> If there is no more specific route, send the traffic toward the ISP router.

---

# 🔗 Full Dependency Chain

For an employee computer to reach an Internet server:

```text
Physical Connection
        ↓
Switching
        ↓
Correct VLAN
        ↓
IPv4 Address
        ↓
Subnet Mask
        ↓
Default Gateway
        ↓
Routing
        ↓
NAT/PAT
        ↓
ISP Path
        ↓
Destination
```

If a hostname is used:

```text
DNS
```

also becomes part of the process.

---

# 🛠️ Troubleshooting NAT

NAT failures often look like:

> "Internal networking works, but the Internet doesn't."

Do not immediately assume NAT.

Check the complete path.

---

# 🛠️ Scenario 1 — Missing `ip nat inside`

Inside interface:

```text
192.168.10.1
```

but:

```text
ip nat inside
```

was never configured.

Possible result:

```text
LAN Communication
✅

Routing Configuration
Maybe ✅

NAT Translation
❌
```

---

# 🛠️ Scenario 2 — Missing `ip nat outside`

The ISP-facing interface exists but isn't marked:

```text
ip nat outside
```

NAT may fail.

Check:

```text
show ip nat statistics
```

---

# 🛠️ Scenario 3 — ACL Does Not Match LAN

Actual LAN:

```text
192.168.10.0/24
```

NAT ACL:

```text
access-list 1 permit 192.168.20.0 0.0.0.255
```

The NAT rule doesn't match the employee traffic.

Result:

> **No translation for those clients**

---

# 🛠️ Scenario 4 — Missing `overload`

If the intention is to let many clients share one address but PAT overload isn't configured correctly, the expected many-to-one behavior may not occur.

Look for:

```text
overload
```

in the NAT configuration.

---

# 🛠️ Scenario 5 — No Default Route

NAT may be configured correctly, but the router doesn't know where to send Internet-bound traffic.

Check:

```text
show ip route
```

Look for:

```text
S*
0.0.0.0/0
```

or another appropriate route.

---

# 🛠️ Scenario 6 — Outside Interface Down

Check:

```text
show ip interface brief
```

If the outside interface is:

```text
administratively down
```

or:

```text
down/down
```

NAT isn't your first problem.

Fix connectivity first.

---

# 🛠️ Scenario 7 — Client Has Wrong Gateway

Client:

```text
IP:
192.168.10.25

Gateway:
192.168.10.254
```

Actual router:

```text
192.168.10.1
```

The packet may never reach the NAT router.

Again:

> **NAT isn't necessarily the root cause.**

---

# 🔍 NAT Troubleshooting Commands

Useful Cisco commands include:

```text
show ip nat translations
```

```text
show ip nat statistics
```

```text
show ip route
```

```text
show ip interface brief
```

```text
show access-lists
```

```text
show running-config
```

---

# 🧭 NAT Troubleshooting Workflow

```text
Does Client Have Valid IP?
        ↓
Correct Gateway?
        ↓
Can Client Reach Gateway?
        ↓
Is Router Outside Interface Up?
        ↓
Does Router Have Outside Route?
        ↓
Correct NAT Inside Interface?
        ↓
Correct NAT Outside Interface?
        ↓
Does ACL Match Inside Network?
        ↓
Correct NAT/PAT Rule?
        ↓
Generate Traffic
        ↓
Check Translation Table
```

---

# 📋 NAT Quick Reference

| Concept | Meaning |
|---|---|
| NAT | Network Address Translation |
| PAT | Port Address Translation |
| NAT Overload | Many hosts sharing address(es) using ports |
| Inside Local | Internal host address |
| Inside Global | Address representing inside host externally |
| Static NAT | Fixed 1:1 mapping |
| Dynamic NAT | Temporary mapping from pool |
| Private IPv4 | Non-public RFC 1918 address |
| Public IPv4 | Globally routable IPv4 address |
| `ip nat inside` | Marks NAT inside interface |
| `ip nat outside` | Marks NAT outside interface |
| `overload` | Enables PAT behavior |

---

# 🧠 Knowledge Check

### 1.
What does NAT stand for?

### 2.
What does PAT stand for?

### 3.
What are the three RFC 1918 private IPv4 ranges?

### 4.
What is static NAT?

### 5.
What is dynamic NAT?

### 6.
What is PAT also commonly called?

### 7.
What does inside local mean?

### 8.
What does inside global mean?

### 9.
What Cisco keyword allows many clients to share an address using PAT?

### 10.
Does NAT replace routing?

---

# ✅ Answers

1. **Network Address Translation**
2. **Port Address Translation**
3. **10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16**
4. **A fixed one-to-one translation**
5. **Temporary translation using an address pool**
6. **NAT overload**
7. **The inside host's address as used internally**
8. **The address representing the inside host externally**
9. **`overload`**
10. **No**

---

# 🎓 Network+ Challenge 1

Which address is private?

### A. 8.8.8.8
### B. 172.20.10.5
### C. 172.40.10.5
### D. 203.0.113.10

> **Answer: B**

---

# 🎓 Network+ Challenge 2

A company has 100 private devices but only one public IPv4 address for normal outbound access.

Which technology is most appropriate?

> **PAT / NAT overload**

---

# 🎓 Network+ Challenge 3

Which NAT type provides a fixed one-to-one mapping?

> **Static NAT**

---

# 🎓 Network+ Challenge 4

What does:

```text
ip nat inside
```

identify?

> **An interface on the inside side of NAT.**

---

# 🎓 Network+ Challenge 5

What command displays current NAT translations?

> **`show ip nat translations`**

---

# 🎓 Network+ Challenge 6

The LAN works, the router can reach the ISP, but no translations appear when clients generate traffic.

What should you investigate?

> **NAT configuration, inside/outside interface assignments, and the ACL used to identify translatable traffic.**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- Private IPv4 addresses are reusable inside private networks.
- RFC 1918 defines the major private IPv4 ranges.
- NAT translates address information between networks.
- Static NAT provides fixed one-to-one translations.
- Dynamic NAT uses a pool.
- PAT allows many internal devices to share public IPv4 addresses.
- PAT uses transport-layer port information to distinguish connections.
- PAT is commonly called NAT overload.
- Inside local is the internal address.
- Inside global represents the internal host externally.
- Cisco NAT interfaces must be correctly identified as inside or outside.
- NAT rules must match the correct internal addresses.
- `overload` enables PAT behavior.
- NAT does not replace routing.
- NAT is not the same thing as a firewall.
- NAT problems should be diagnosed as part of the complete network path.

---

# 🧪 Next Step — Lab 16

In Lab 16 you'll build:

```text
PRIVATE LAN
     │
     ▼
 NAT ROUTER
     │
     ▼
 ISP ROUTER
     │
     ▼
INTERNET SERVER
```

You'll:

- Configure private IPv4
- Configure a simulated public network
- Configure routing
- Configure PAT
- Generate translations
- Examine the NAT table
- Configure static NAT
- Break NAT
- Repair NAT
- Diagnose wrong ACLs
- Diagnose inside/outside mistakes
- Diagnose routing failures

➡️ **[Lab 16 — NAT and Address Translation](../labs/lab-16-nat-address-translation.md)**

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ COMPLETE
✅ Project 02

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES

✅ Lesson 11 — Switching Fundamentals
✅ Lab 11
✅ Lesson 12 — VLANs & Network Segmentation
✅ Lab 12
✅ Lesson 13 — Routing Fundamentals
✅ Lab 13
✅ Lesson 14 — DHCP
✅ Lab 14
✅ Lesson 15 — DNS
✅ Lab 15
✅ Lesson 16 — NAT & Address Translation

        ↓

🟡 NEXT:
Lab 16 — NAT & Address Translation

        ↓

🏗️ Project 03
Build a Routed Small-Business Network
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**