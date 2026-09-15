# 📘 Lesson 09 — IPv6 Fundamentals

Welcome to **Lesson 09 of Networking Fundamentals**.

You've now learned:

```text
Ethernet
    ↓
MAC Addressing
    ↓
IPv4
    ↓
Subnetting
```

Now it's time to look at the other major version of the Internet Protocol:

> 🌐 **IPv6 — Internet Protocol Version 6**

IPv6 may look intimidating at first:

```text
2001:db8:1234:5678:abcd:ef01:2345:6789
```

But don't let the size fool you.

For this course, we're going to break IPv6 into a few important concepts and make it practical.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain why IPv6 was developed
- Explain the size of an IPv6 address
- Recognize IPv6 notation
- Explain hexadecimal addressing
- Shorten IPv6 addresses correctly
- Expand compressed IPv6 addresses
- Recognize global unicast addresses
- Recognize link-local addresses
- Recognize unique local addresses
- Recognize the IPv6 loopback address
- Explain IPv6 multicast
- Understand why IPv6 doesn't use broadcast
- Understand `/64` prefixes
- Explain SLAAC
- Explain DHCPv6
- Explain Neighbor Discovery
- Understand ICMPv6
- Explain dual stack
- Understand the relationship between IPv4 and IPv6
- Perform basic IPv6 troubleshooting

---

# 🎓 Network+ Focus

For **CompTIA Network+ N10-009**, pay particular attention to:

- IPv6 notation
- IPv6 address types
- Global unicast
- Link-local
- Unique local
- Multicast
- Loopback
- Prefix notation
- SLAAC
- DHCPv6
- Neighbor Discovery
- ICMPv6
- Dual stack
- IPv4 vs. IPv6

The goal isn't to memorize every IPv6 standard.

You should be able to look at an IPv6 address and think:

> **What kind of address is this, and what is it probably being used for?**

---

# 🌐 Why IPv6?

IPv4 uses:

> **32-bit addresses**

This provides approximately:

```text
4.3 billion addresses
```

That sounded enormous when IPv4 was created.

Then came:

- Personal computers
- Smartphones
- Tablets
- Servers
- Cloud computing
- IoT devices
- Smart TVs
- Cameras
- Vehicles
- Industrial systems

The world needed far more addresses.

---

# 🌎 IPv6 Address Space

IPv6 uses:

> **128-bit addresses**

Compared with:

```text
IPv4
32 bits
```

IPv6 provides:

```text
128 bits
```

The theoretical IPv6 address space contains:

```text
2^128
```

addresses.

That's approximately:

```text
340 undecillion
```

or:

```text
340,282,366,920,938,463,463,374,607,431,768,211,456
```

You do **not** need to memorize that number.

Remember:

```text
IPv4 = 32 bits

IPv6 = 128 bits
```

---

# 🔢 IPv6 Address Format

An IPv6 address is normally written as:

> **Eight groups of four hexadecimal digits**

Example:

```text
2001:0db8:1234:5678:abcd:ef01:2345:6789
```

Each group contains:

> **16 bits**

Eight groups × 16 bits:

```text
8 × 16
=
128 bits
```

---

# 🔤 Hexadecimal Review

IPv6 uses hexadecimal.

Hexadecimal contains:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

Values:

```text
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

IPv6 addresses are case-insensitive.

These mean the same thing:

```text
2001:DB8::1
```

and:

```text
2001:db8::1
```

Lowercase is commonly used.

---

# 🧱 IPv6 Groups

Consider:

```text
2001:0db8:1234:5678:abcd:ef01:2345:6789
```

Break it apart:

```text
2001
0db8
1234
5678
abcd
ef01
2345
6789
```

That's:

> **Eight groups**

IPv6 groups are sometimes called:

> **Hextets**

---

# ✂️ IPv6 Address Compression

IPv6 addresses are long.

Fortunately, they can be shortened.

There are two important rules.

---

# Rule 1 — Remove Leading Zeros

Consider:

```text
2001:0db8:0000:0000:0001:0000:0000:0001
```

Leading zeros inside each group can be removed.

So:

```text
0db8
```

becomes:

```text
db8
```

and:

```text
0001
```

becomes:

```text
1
```

Result:

```text
2001:db8:0:0:1:0:0:1
```

---

# ⚠️ Don't Remove Trailing Zeros

You can remove:

> **Leading zeros**

Not arbitrary zeros.

For example:

```text
1200
```

cannot become:

```text
12
```

Those are different values.

---

# Rule 2 — Compress Consecutive Zero Groups

A consecutive sequence of all-zero groups can be replaced by:

```text
::
```

Example:

```text
2001:db8:0:0:0:0:0:1
```

becomes:

```text
2001:db8::1
```

Much easier.

---

# ⭐ Important Compression Rule

You may use:

```text
::
```

only:

> **Once in a single IPv6 address**

Why?

Because if it appeared multiple times, you wouldn't know how many zero groups each `::` represented.

---

# 🧠 Compression Example

Start with:

```text
2001:0db8:0000:0000:0000:0000:0000:0025
```

Remove leading zeros:

```text
2001:db8:0:0:0:0:0:25
```

Compress the consecutive zero groups:

```text
2001:db8::25
```

---

# 🔄 Expanding IPv6

Suppose you see:

```text
2001:db8::10
```

IPv6 requires eight groups.

We currently have:

```text
2001
db8
10
```

The `::` fills the missing groups.

Expanded:

```text
2001:0db8:0000:0000:0000:0000:0000:0010
```

---

# 🏠 IPv6 Prefixes

IPv6 also uses CIDR-style prefix notation.

Example:

```text
2001:db8:1234:5678::/64
```

The:

```text
/64
```

means:

> **The first 64 bits represent the network prefix**

A `/64` is extremely common on normal IPv6 LANs.

---

# ⭐ Remember /64

For Network+ fundamentals:

```text
IPv6 LAN
        ↓
Often /64
```

Unlike IPv4, IPv6 was designed with an enormous address space.

IPv6 subnet design generally isn't about squeezing every possible address out of a subnet.

---

# 🏷️ IPv6 Address Types

Important IPv6 address types include:

```text
Global Unicast
Link-Local
Unique Local
Multicast
Loopback
Unspecified
```

Let's look at each.

---

# 🌎 Global Unicast

Global unicast addresses are generally used for globally routable IPv6 communication.

The currently allocated global unicast space is primarily within:

```text
2000::/3
```

Examples commonly begin with:

```text
2
```

or:

```text
3
```

Example:

```text
2001:db8:1234:1::25
```

However:

```text
2001:db8::/32
```

is specifically reserved for:

> **Documentation and examples**

That's why you'll see it throughout this course.

---

# 🧠 Documentation Range

We'll frequently use addresses such as:

```text
2001:db8:10::1
```

in labs.

These aren't intended to be real public Internet addresses.

They're safe for documentation examples.

---

# 🔗 Link-Local Addresses

IPv6 devices normally create a:

> **Link-local address**

Link-local addresses use:

```text
fe80::/10
```

You'll commonly see addresses beginning with:

```text
fe80:
```

Example:

```text
fe80::a8c2:15ff:fe20:1234
```

---

# 🏠 What Is Link-Local For?

Link-local addresses are used for communication on the:

> **Local Layer 2 link**

They are not normally routed across routers.

IPv6 uses link-local addressing for important functions including:

- Neighbor Discovery
- Router communication
- Local network operations

---

# ⭐ Network+ Memory Aid

```text
FE80
=
Think Local
```

If you see:

```text
fe80::
```

think:

> **IPv6 link-local**

---

# 🏢 Unique Local Addresses

IPv6 also has:

> **Unique Local Addresses — ULA**

The reserved range is:

```text
fc00::/7
```

In normal local assignment practice, you'll commonly encounter:

```text
fd00::/8
```

Example:

```text
fd12:3456:789a:1::25
```

These are intended for local/private-style IPv6 communication and aren't globally routed on the public Internet.

---

# ⚠️ ULA Isn't Exactly IPv4 Private Addressing

It's tempting to say:

```text
IPv4 Private
=
IPv6 ULA
```

They're similar conceptually, but IPv6 networking isn't designed simply as IPv4 with longer addresses.

Avoid assuming that IPv6 requires NAT in the same way private IPv4 commonly does.

---

# 🔁 IPv6 Loopback

IPv6 loopback is:

```text
::1
```

Compare:

```text
IPv4:
127.0.0.1

IPv6:
::1
```

Easy memory:

```text
::1
=
Me
```

---

# 🕳️ Unspecified Address

The IPv6 unspecified address is:

```text
::
```

It means:

> **No address / unspecified**

Compare:

```text
IPv4:
0.0.0.0

IPv6:
::
```

depending on context.

---

# 📢 What Happened to Broadcast?

IPv4 uses broadcasts.

Example:

```text
255.255.255.255
```

IPv6 does:

> **Not use broadcast addressing**

Instead, IPv6 makes extensive use of:

> **Multicast**

---

# 👥 IPv6 Multicast

IPv6 multicast addresses begin with:

```text
ff
```

The multicast range is:

```text
ff00::/8
```

So:

```text
FF
=
Think Multicast
```

---

# ⭐ Important Multicast Addresses

You may encounter:

```text
ff02::1
```

which represents:

> **All nodes on the local link**

and:

```text
ff02::2
```

which represents:

> **All routers on the local link**

---

# 📋 IPv6 Quick Reference

| Address | Meaning |
|---|---|
| `::1` | Loopback |
| `::` | Unspecified |
| `fe80::/10` | Link-local |
| `fc00::/7` | Unique local range |
| `fd00::/8` | Common locally assigned ULA space |
| `ff00::/8` | Multicast |
| `2000::/3` | Global unicast allocation |
| `2001:db8::/32` | Documentation/examples |

---

# 🔍 IPv6 Neighbor Discovery

Remember ARP from IPv4?

ARP answers:

> **Which MAC address belongs to this local IPv4 address?**

IPv6 doesn't use ARP.

Instead, IPv6 uses:

> **Neighbor Discovery Protocol — NDP**

NDP operates using:

> **ICMPv6**

---

# 🔄 IPv4 vs. IPv6

Conceptually:

```text
IPv4
ARP
 ↓
IPv4 → MAC
```

IPv6:

```text
IPv6
Neighbor Discovery
 ↓
IPv6 Neighbor Information
```

NDP does more than simply replace ARP, but this comparison is useful for beginners.

---

# 📨 Neighbor Solicitation

A device can send a:

> **Neighbor Solicitation — NS**

to discover information about another IPv6 neighbor.

Conceptually:

```text
Who has this IPv6 address?
```

---

# 📬 Neighbor Advertisement

The neighbor can respond with a:

> **Neighbor Advertisement — NA**

Conceptually:

```text
That's me.
Here's my information.
```

---

# 🚦 Router Discovery

IPv6 devices can also discover routers using:

> **Router Solicitation — RS**

and:

> **Router Advertisement — RA**

Conceptually:

```text
Host:
Are there any IPv6 routers here?

Router:
Yes. Here's information about this network.
```

---

# 🧠 ICMPv6 Is Important

ICMPv6 isn't simply used for:

```text
ping
```

It's fundamental to many IPv6 operations.

Blocking ICMPv6 indiscriminately can break important IPv6 functionality.

---

# 🤖 SLAAC

SLAAC stands for:

> **Stateless Address Autoconfiguration**

SLAAC allows an IPv6 host to configure an address using information advertised by a router.

Conceptually:

```text
Router Advertisement
        ↓
Network Prefix
        ↓
Host Builds IPv6 Address
```

This allows devices to configure themselves without requiring traditional stateful DHCP for the address.

---

# 📡 DHCPv6

IPv6 can also use:

> **DHCPv6**

DHCPv6 can provide IPv6 configuration depending on the network design.

IPv6 networks may use:

```text
SLAAC
```

or:

```text
DHCPv6
```

or combinations of IPv6 autoconfiguration mechanisms.

---

# 🧠 SLAAC vs. DHCPv6

At a high level:

| SLAAC | DHCPv6 |
|---|---|
| Uses router advertisements | Uses DHCPv6 service |
| Host can self-configure address | Can centrally provide configuration |
| Common in IPv6 | Also common depending on design |

Don't assume IPv6 configuration works exactly like IPv4 DHCP.

---

# 🔀 Dual Stack

Many networks support both:

```text
IPv4
+
IPv6
```

at the same time.

This is called:

> **Dual Stack**

Example:

```text
Laptop

IPv4:
192.168.10.25

IPv6:
2001:db8:10::25
```

The device can communicate using either protocol when supported.

---

# 🌉 IPv4 and IPv6 Are Separate Protocols

An IPv4-only device can't simply communicate directly with an IPv6-only device without some type of translation or intermediary mechanism.

That's why transition technologies exist.

For Network+ fundamentals, understand:

```text
Dual Stack
Translation
Tunneling
```

as broad IPv4/IPv6 coexistence approaches.

We'll revisit network translation and tunneling later.

---

# 🖥️ IPv6 on Windows

Your Windows computer likely already has IPv6 enabled.

Run:

```cmd
ipconfig
```

You may see:

```text
IPv6 Address
Temporary IPv6 Address
Link-local IPv6 Address
```

---

# 🔷 PowerShell

Run:

```powershell
Get-NetIPAddress -AddressFamily IPv6
```

This displays IPv6 addresses assigned to Windows interfaces.

---

# 🔎 Neighbor Information

Run:

```powershell
Get-NetNeighbor -AddressFamily IPv6
```

You can inspect IPv6 neighbor entries.

This is somewhat analogous to inspecting:

```cmd
arp -a
```

for IPv4, though IPv6 uses Neighbor Discovery rather than ARP.

---

# 🧪 IPv6 Ping

IPv6 addresses can be tested with:

```cmd
ping ::1
```

This tests IPv6 loopback.

You may also ping another IPv6 host:

```cmd
ping 2001:db8:10::20
```

if such a host exists in your lab.

---

# 🧭 Trace IPv6

Windows can use:

```cmd
tracert -6 ADDRESS
```

Example:

```cmd
tracert -6 2001:db8:20::10
```

when a reachable IPv6 route exists.

---

# 🛠️ Troubleshooting Scenario 1

A workstation has:

```text
fe80::1234:5678:abcd:ef01
```

but no expected global IPv6 address.

What does the `fe80::` address tell you?

> The interface has an IPv6 link-local address.

It does **not** prove that globally routed IPv6 connectivity is working.

---

# 🛠️ Troubleshooting Scenario 2

A technician sees:

```text
::1
```

What is it?

> **IPv6 loopback**

---

# 🛠️ Troubleshooting Scenario 3

A technician says:

> "IPv6 ARP isn't working."

What's wrong with that statement?

IPv6 doesn't use ARP.

It uses:

> **Neighbor Discovery**

---

# 🛠️ Troubleshooting Scenario 4

Two hosts are configured as:

```text
PC-A
2001:db8:10::10/64

PC-B
2001:db8:20::20/64
```

Are they on the same IPv6 subnet?

> **No**

They have different `/64` prefixes.

Routing is required between those networks.

---

# 🛠️ Troubleshooting Scenario 5

A firewall administrator blocks all ICMPv6 because:

> "Ping isn't necessary."

Why can this be a problem?

Because ICMPv6 supports critical IPv6 functions including:

> **Neighbor Discovery**

and other network operations.

---

# 📋 IPv4 vs. IPv6

| Feature | IPv4 | IPv6 |
|---|---|---|
| Address Size | 32 bits | 128 bits |
| Example | `192.168.1.10` | `2001:db8::10` |
| Notation | Decimal | Hexadecimal |
| Loopback | `127.0.0.1` | `::1` |
| Local resolution | ARP | Neighbor Discovery |
| Broadcast | Yes | No |
| Multicast | Yes | Yes, heavily used |
| Automatic configuration | DHCP/APIPA | SLAAC/DHCPv6/link-local |
| Common LAN prefix | Varies | `/64` commonly |

---

# 🧠 IPv6 Memory Aids

```text
::1
=
Loopback
```

```text
FE80
=
Link-Local
```

```text
FD
=
Common Unique Local
```

```text
FF
=
Multicast
```

```text
2001:DB8
=
Documentation
```

```text
/64
=
Common IPv6 LAN Prefix
```

---

# 🧠 Knowledge Check

### 1.

How many bits are in an IPv6 address?

### 2.

How many hexadecimal groups are in a fully written IPv6 address?

### 3.

What does `::1` represent?

### 4.

What type of address commonly begins with `fe80`?

### 5.

What does `ff` indicate?

### 6.

Does IPv6 use broadcast?

### 7.

What protocol replaces the ARP function in IPv6?

### 8.

What does SLAAC stand for?

### 9.

What prefix length is extremely common on IPv6 LANs?

### 10.

What is dual stack?

---

# ✅ Knowledge Check Answers

1. **128 bits**
2. **8 groups**
3. **IPv6 loopback**
4. **Link-local**
5. **Multicast**
6. **No**
7. **Neighbor Discovery / NDP**
8. **Stateless Address Autoconfiguration**
9. **/64**
10. **Running IPv4 and IPv6 together**

---

# 🎓 Network+ Challenge 1

Which address is IPv6 loopback?

### A. `127.0.0.1`
### B. `::1`
### C. `fe80::1`
### D. `ff02::1`

> **Answer: B — `::1`**

---

# 🎓 Network+ Challenge 2

Which address is link-local?

### A. `2001:db8::10`
### B. `fd00::10`
### C. `fe80::10`
### D. `ff02::1`

> **Answer: C — `fe80::10`**

---

# 🎓 Network+ Challenge 3

Which technology allows an IPv6 host to configure an address using router advertisements?

### A. ARP
### B. SLAAC
### C. NAT
### D. DNS

> **Answer: B — SLAAC**

---

# 🎓 Network+ Challenge 4

Which protocol is heavily involved with IPv6 Neighbor Discovery?

### A. ICMPv6
### B. FTP
### C. ARP
### D. SMB

> **Answer: A — ICMPv6**

---

# 🎓 Network+ Challenge 5

Which IPv6 address is reserved for documentation?

### A. `2001:db8::10`
### B. `fe80::10`
### C. `ff02::10`
### D. `::1`

> **Answer: A**

---

# 🎓 Network+ Challenge 6

Which represents an IPv6 network commonly used as a normal LAN-sized prefix?

### A. `/8`
### B. `/24`
### C. `/64`
### D. `/128`

> **Answer: C — `/64`**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- IPv6 uses 128-bit addresses.
- IPv6 uses hexadecimal notation.
- IPv6 normally contains eight groups when fully expanded.
- Leading zeros can be removed.
- Consecutive zero groups can be compressed using `::`.
- `::` can only be used once in an address.
- `/64` is extremely common for IPv6 LANs.
- `fe80::/10` is link-local.
- `fc00::/7` is unique local space.
- `::1` is loopback.
- `::` is unspecified.
- `ff00::/8` is multicast.
- IPv6 doesn't use broadcast.
- IPv6 doesn't use ARP.
- Neighbor Discovery uses ICMPv6.
- SLAAC allows automatic IPv6 configuration using router advertisements.
- DHCPv6 can also provide IPv6 configuration.
- Dual-stack devices run IPv4 and IPv6.
- ICMPv6 is important to normal IPv6 operation.

---

# 🧪 Next Step — Lab 09

Now you'll inspect IPv6 on Windows and build an IPv6 network using Cisco Packet Tracer.

➡️ **[Lab 09 — IPv6 Fundamentals](../labs/lab-09-ipv6-fundamentals.md)**

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
        ↓
🟡 NEXT: Lab 09 — IPv6 Fundamentals
        ↓
⬜ Lesson 10 — TCP, UDP, Ports & Protocols
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**