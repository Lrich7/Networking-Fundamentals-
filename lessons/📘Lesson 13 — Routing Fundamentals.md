# 📘 Lesson 13 — Routing Fundamentals

Welcome to **Lesson 13 of Networking Fundamentals**.

In Lesson 12, you built VLANs and discovered an important rule:

> **Different IP networks require Layer 3 routing to communicate.**

You used a router to move traffic between:

```text id="r13a01"
VLAN 10 — 192.168.10.0/24
              ↕
             R-01
              ↕
VLAN 20 — 192.168.20.0/24
```

But how did the router know where to send those packets?

That's what this lesson is about.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain what routing is
- Explain the purpose of a router
- Understand routing tables
- Identify directly connected networks
- Explain remote networks
- Understand next-hop addresses
- Explain exit interfaces
- Understand static routes
- Understand default routes
- Understand dynamic routing at a high level
- Read a Cisco routing table
- Use `show ip route`
- Understand route prefixes
- Explain longest-prefix match
- Understand administrative distance at a basic level
- Understand routing metrics at a basic level
- Explain the relationship between a host's default gateway and routing
- Use `route print` and `Get-NetRoute` in Windows
- Trace a routed path
- Recognize common routing problems
- Troubleshoot missing and incorrect routes

---

# 🎓 Network+ Focus

For **CompTIA Network+ N10-009**, pay particular attention to:

- Routers
- Routing tables
- Default gateways
- Static routes
- Default routes
- Dynamic routing concepts
- Next hops
- Route metrics
- Administrative distance concepts
- Longest-prefix match
- IPv4 prefixes
- Routing protocols
- Troubleshooting routing problems

A key idea for this lesson:

> **Routers forward packets based on the destination IP address and their routing table.**

---

# 🛣️ What Is Routing?

Routing is the process of determining:

> **Where an IP packet should go next to reach its destination network.**

Routing occurs primarily at:

> **OSI Layer 3 — Network**

The primary addressing information used is:

> **IP addresses**

---

# 🔀 Switching vs. Routing

You've now worked extensively with both.

## Switching

Traditional Layer 2 switching uses:

```text id="r13a02"
MAC Addresses
```

to forward:

```text id="r13a03"
Ethernet Frames
```

within Layer 2 networks.

## Routing

Routing uses:

```text id="r13a04"
IP Addresses
```

to forward:

```text id="r13a05"
IP Packets
```

between IP networks.

---

# 📋 Quick Comparison

| Switching | Routing |
|---|---|
| Primarily Layer 2 | Layer 3 |
| Uses MAC addresses | Uses IP addresses |
| Forwards frames | Forwards packets |
| MAC address table | Routing table |
| Local Layer 2 forwarding | Communication between IP networks |

---

# 🏠 Local vs. Remote Communication

Suppose PC-01 has:

```text id="r13a06"
IP:
192.168.10.10

Mask:
/24

Gateway:
192.168.10.1
```

PC-02 has:

```text id="r13a07"
192.168.10.20/24
```

PC-01 determines:

> PC-02 is on my local subnet.

So it can communicate directly at Layer 2.

---

# 🌎 Remote Destination

Now PC-01 wants to reach:

```text id="r13a08"
192.168.20.10
```

PC-01 compares the destination with its own network.

It determines:

> **192.168.20.10 is not local.**

Therefore:

```text id="r13a09"
PC-01
   ↓
Default Gateway
192.168.10.1
```

The router must take over.

---

# 🚪 The Default Gateway

A default gateway is the Layer 3 device a host uses to reach:

> **Networks outside its local subnet**

Example:

```text id="r13a10"
PC-01
192.168.10.10/24

Gateway:
192.168.10.1
```

If PC-01 wants to reach:

```text id="r13a11"
192.168.20.10
```

it sends the packet toward:

```text id="r13a12"
192.168.10.1
```

---

# ⭐ Important

The default gateway must normally be:

> **Reachable on the host's local subnet.**

For:

```text id="r13a13"
192.168.10.10/24
```

a gateway such as:

```text id="r13a14"
192.168.10.1
```

makes sense.

A gateway such as:

```text id="r13a15"
192.168.50.1
```

would not normally be directly reachable from that host without some special configuration.

---

# 📖 What Is a Routing Table?

A router needs information about:

> **Where networks are located.**

It stores this information in a:

> **Routing Table**

Think of it as a set of directions.

Example:

```text id="r13a16"
192.168.10.0/24
→ Directly Connected

192.168.20.0/24
→ Directly Connected

192.168.30.0/24
→ Send to 10.0.0.2
```

---

# 🗺️ Simple Router

Consider:

```text id="r13a17"
192.168.10.0/24
        │
        │
      R-01
        │
        │
192.168.20.0/24
```

R-01 has an interface in each network.

For example:

```text id="r13a18"
G0/0
192.168.10.1/24

G0/1
192.168.20.1/24
```

The router automatically knows about those networks because they are:

> **Directly Connected**

---

# 🔗 Directly Connected Routes

When a router interface is configured and operational, the router can install routes for the connected network.

Conceptually:

```text id="r13a19"
192.168.10.0/24
is directly connected
G0/0
```

and:

```text id="r13a20"
192.168.20.0/24
is directly connected
G0/1
```

No static route is needed for a network directly attached to the router.

---

# 🖥️ Cisco `show ip route`

One of the most important routing commands is:

```text id="r13a21"
show ip route
```

Example output may include:

```text id="r13a22"
C    192.168.10.0/24 is directly connected, GigabitEthernet0/0
C    192.168.20.0/24 is directly connected, GigabitEthernet0/1
```

The:

```text id="r13a23"
C
```

means:

> **Connected**

---

# 📍 Local Routes

Cisco routing tables may also display:

```text id="r13a24"
L
```

for a:

> **Local Route**

For example:

```text id="r13a25"
L    192.168.10.1/32
```

This represents the router interface's own IP address.

---

# 📋 Common Cisco Route Codes

| Code | Meaning |
|---|---|
| C | Connected |
| L | Local |
| S | Static |
| O | OSPF |
| R | RIP |
| D | EIGRP |

You do not need to master every dynamic protocol yet.

For now, recognize:

```text id="r13a26"
C = Connected
L = Local
S = Static
```

---

# 🌐 Remote Networks

Now add another router.

```text id="r13a27"
LAN A                  LAN B
192.168.10.0/24        192.168.20.0/24

     │                      │
     │                      │
    R-01 ─────── R-02
          10.0.0.0/30
```

R-01 knows its directly connected networks.

R-02 knows its directly connected networks.

But does R-01 automatically know where:

```text id="r13a28"
192.168.20.0/24
```

is?

Not necessarily.

We must provide that information.

---

# 🪧 Static Routes

A:

> **Static Route**

is manually configured by an administrator.

Conceptually:

```text id="r13a29"
To reach:
192.168.20.0/24

Send traffic to:
10.0.0.2
```

On Cisco IOS:

```text id="r13a30"
ip route 192.168.20.0 255.255.255.0 10.0.0.2
```

---

# 🧠 Breaking Down the Command

```text id="r13a31"
ip route
```

means:

> Create a static route.

```text id="r13a32"
192.168.20.0
```

is the destination network.

```text id="r13a33"
255.255.255.0
```

is the subnet mask.

```text id="r13a34"
10.0.0.2
```

is the next-hop router.

---

# ➡️ What Is a Next Hop?

The:

> **Next Hop**

is the next router that should receive the packet.

Example:

```text id="r13a35"
PC-01
   ↓
R-01
   ↓
R-02
   ↓
Server
```

From R-01's perspective:

```text id="r13a36"
R-02
=
Next Hop
```

for networks located behind R-02.

---

# 🚪 Exit Interface

A route may also identify an:

> **Exit Interface**

This is the router interface through which the packet leaves.

Conceptually:

```text id="r13a37"
Destination:
192.168.20.0/24

Exit:
G0/1
```

Depending on network type and configuration, static routes may reference:

- Next-hop address
- Exit interface
- Both

---

# 🔁 Routing Must Work Both Ways

This is extremely important.

Suppose:

```text id="r13a38"
PC-01
   ↓
R-01
   ↓
R-02
   ↓
SRV-01
```

R-01 knows how to reach SRV-01.

But R-02 doesn't know how to reach PC-01's network.

What happens?

The request may reach the server, but:

> **The reply doesn't know how to return.**

Routing needs a valid path:

```text id="r13a39"
THERE
+
BACK
```

---

# ⭐ Return Path

Always ask:

> **Does the destination know how to return traffic to the source network?**

This is one of the most useful troubleshooting questions in networking.

---

# 🧪 Example Two-Router Network

Consider:

```text id="r13a40"
PC-01
192.168.10.10
    │
    ▼
  R-01
10.0.0.1
    │
    │
10.0.0.0/30
    │
    ▼
  R-02
10.0.0.2
    │
    ▼
SRV-01
192.168.20.10
```

R-01 needs:

```text id="r13a41"
192.168.20.0/24
→ 10.0.0.2
```

R-02 needs:

```text id="r13a42"
192.168.10.0/24
→ 10.0.0.1
```

---

# 🖥️ Static Route on R-01

```text id="r13a43"
ip route 192.168.20.0 255.255.255.0 10.0.0.2
```

---

# 🖥️ Static Route on R-02

```text id="r13a44"
ip route 192.168.10.0 255.255.255.0 10.0.0.1
```

Now both routers know:

> **How to reach the remote network.**

---

# 📋 Static Route in the Routing Table

Run:

```text id="r13a45"
show ip route
```

You may see:

```text id="r13a46"
S    192.168.20.0/24 [1/0] via 10.0.0.2
```

The:

```text id="r13a47"
S
```

means:

> **Static**

---

# 🌎 Default Route

Imagine a router connected to many possible outside networks.

Instead of creating routes for every possible destination, we can use:

> **A Default Route**

IPv4 default route:

```text id="r13a48"
0.0.0.0/0
```

Think:

> **If I don't have a more specific route, send the packet this way.**

---

# 🖥️ Cisco Default Route

Example:

```text id="r13a49"
ip route 0.0.0.0 0.0.0.0 10.0.0.2
```

Meaning:

```text id="r13a50"
Unknown Destination
        ↓
No More Specific Route
        ↓
Send to 10.0.0.2
```

---

# 🚪 Default Gateway vs. Default Route

These sound similar but are not exactly the same thing.

## Default Gateway

Usually discussed from an endpoint's perspective.

Example:

```text id="r13a51"
PC Gateway:
192.168.10.1
```

## Default Route

Usually discussed as a routing-table entry.

```text id="r13a52"
0.0.0.0/0
```

The concepts are closely related:

> **Use this path when the destination isn't local or no more specific route exists.**

---

# 🛣️ Route Selection

What if multiple routes could match a destination?

Example:

```text id="r13a53"
192.168.0.0/16

192.168.10.0/24
```

Destination:

```text id="r13a54"
192.168.10.50
```

Both routes mathematically match.

Which one should be used?

> **The most specific route.**

---

# 🎯 Longest-Prefix Match

Routers prefer the route with the:

> **Longest matching prefix**

In this example:

```text id="r13a55"
/24
```

is more specific than:

```text id="r13a56"
/16
```

Therefore:

```text id="r13a57"
192.168.10.0/24
```

wins.

---

# 🧠 Another Example

Routing table:

```text id="r13a58"
0.0.0.0/0

10.0.0.0/8

10.10.0.0/16

10.10.50.0/24
```

Destination:

```text id="r13a59"
10.10.50.25
```

Best route:

```text id="r13a60"
10.10.50.0/24
```

because it is the most specific match.

---

# ⭐ Network+ Rule

Remember:

> **Longest-prefix match chooses the most specific matching route.**

---

# ⚖️ What If Routes Are Equally Specific?

If routes have the same destination prefix, the router may need additional information to choose between them.

Two important concepts are:

- Administrative distance
- Metric

---

# 📏 Administrative Distance

Administrative distance helps a router choose between routes learned from:

> **Different routing sources**

For example:

```text id="r13a61"
Static Route
vs.
OSPF Route
```

A lower administrative distance is generally preferred.

For this course, understand the concept.

You do not need to memorize every vendor-specific administrative-distance value for Network+.

---

# 📊 Metric

A routing protocol can use a:

> **Metric**

to compare paths learned by that routing protocol.

Depending on the protocol, metrics may consider concepts such as:

- Cost
- Hop count
- Bandwidth
- Delay

Lower or better metric values are often preferred according to the protocol's rules.

---

# 🧠 Don't Mix These Up

```text id="r13a62"
Longest Prefix
=
Which route matches the destination most specifically?
```

```text id="r13a63"
Administrative Distance
=
Which routing source should I trust?
```

```text id="r13a64"
Metric
=
Which path from that routing protocol is preferred?
```

---

# 🔄 Dynamic Routing

Static routes work well for:

- Small networks
- Simple topologies
- Predictable paths
- Default routes

But imagine manually maintaining hundreds of networks.

That becomes difficult.

Dynamic routing protocols allow routers to:

> **Exchange routing information automatically.**

---

# 🌐 Common Dynamic Routing Protocols

Examples include:

```text id="r13a65"
OSPF

BGP

RIP

EIGRP
```

For Network+, you should recognize their roles and basic differences.

---

# 🟢 OSPF

OSPF stands for:

> **Open Shortest Path First**

It is a:

> **Link-state interior gateway protocol**

commonly used within organizations.

---

# 🌍 BGP

BGP stands for:

> **Border Gateway Protocol**

It is heavily associated with routing:

> **Between autonomous systems and across the Internet**

BGP is much larger and more complex than what we need right now.

---

# 🟡 RIP

RIP stands for:

> **Routing Information Protocol**

It uses:

> **Hop count**

as its metric.

It is historically important and useful for learning, but is uncommon in modern enterprise designs.

---

# 🔵 EIGRP

EIGRP stands for:

> **Enhanced Interior Gateway Routing Protocol**

It is strongly associated with Cisco environments, though parts of its specification have been published.

For this course, recognize the name and general purpose.

---

# 📋 High-Level Comparison

| Protocol | Type / Role | Key Idea |
|---|---|---|
| OSPF | Interior, link-state | Common enterprise IGP |
| BGP | Exterior/path-vector | Internet/inter-AS routing |
| RIP | Distance-vector | Hop-count metric |
| EIGRP | Advanced distance-vector style | Commonly associated with Cisco |

---

# 🖥️ Windows Has a Routing Table Too

Routers aren't the only devices with routing tables.

Your Windows computer has one.

Open Command Prompt:

```text id="r13a66"
route print
```

You may see entries for:

- Local subnet
- Loopback
- Default route
- Interface routes
- IPv4
- IPv6

---

# ⚡ PowerShell

Use:

```text id="r13a67"
Get-NetRoute
```

To focus on IPv4:

```text id="r13a68"
Get-NetRoute -AddressFamily IPv4
```

---

# 🔍 Find the Default Route

Look for:

```text id="r13a69"
0.0.0.0/0
```

This is typically the system's IPv4 default route.

It should point toward a:

> **Next hop / default gateway**

---

# 🧠 Endpoint Routing Decision

Your computer performs routing decisions too.

Suppose:

```text id="r13a70"
Destination:
192.168.10.20
```

and that's local.

Windows can use the directly connected route.

But for:

```text id="r13a71"
8.8.8.8
```

there probably isn't a more specific route.

So Windows uses:

```text id="r13a72"
0.0.0.0/0
```

toward the default gateway.

---

# 🧭 `tracert`

Windows:

```text id="r13a73"
tracert 8.8.8.8
```

shows Layer 3 hops toward a destination when devices along the path respond appropriately.

Example conceptually:

```text id="r13a74"
PC
 ↓
Gateway
 ↓
ISP Router
 ↓
Upstream Router
 ↓
Destination
```

---

# ⚡ PowerShell `Test-NetConnection`

You can also use:

```text id="r13a75"
Test-NetConnection 8.8.8.8
```

For route information:

```text id="r13a76"
Test-NetConnection 8.8.8.8 -TraceRoute
```

This can help with troubleshooting and path visibility.

---

# 🛠️ Troubleshooting Scenario 1 — Local Works, Remote Fails

PC-01 can ping:

```text id="r13a77"
192.168.10.20
```

but not:

```text id="r13a78"
192.168.20.10
```

Possible causes:

- Wrong default gateway
- Missing route
- Router interface down
- Remote network down
- Return route missing
- Firewall/security policy

Don't immediately blame DNS.

You're testing IP addresses.

---

# 🛠️ Scenario 2 — Router Knows Local but Not Remote

R-01:

```text id="r13a79"
C 192.168.10.0/24
C 10.0.0.0/30
```

But there is no:

```text id="r13a80"
192.168.20.0/24
```

route.

R-01 doesn't know how to reach the remote LAN.

Possible fix:

> **Add an appropriate route.**

---

# 🛠️ Scenario 3 — One-Way Routing

R-01 knows:

```text id="r13a81"
192.168.20.0/24
→ R-02
```

But R-02 doesn't know:

```text id="r13a82"
192.168.10.0/24
→ R-01
```

Potential result:

> **Return traffic fails.**

Always verify both directions.

---

# 🛠️ Scenario 4 — Wrong Next Hop

Static route:

```text id="r13a83"
192.168.20.0/24
→ 10.0.0.99
```

But the actual neighboring router is:

```text id="r13a84"
10.0.0.2
```

The route points to the wrong next hop.

---

# 🛠️ Scenario 5 — Interface Down

A route may disappear or become unusable if a required router interface is down.

Check:

```text id="r13a85"
show ip interface brief
```

This is another extremely useful Cisco command.

---

# 📋 `show ip interface brief`

Example:

```text id="r13a86"
Interface              IP-Address      Status      Protocol
GigabitEthernet0/0     192.168.10.1    up          up
GigabitEthernet0/1     10.0.0.1        up          up
```

Ideally:

```text id="r13a87"
Status:
up

Protocol:
up
```

---

# 🛠️ Scenario 6 — Incorrect Host Gateway

PC:

```text id="r13a88"
192.168.10.10/24
```

Gateway configured:

```text id="r13a89"
192.168.10.254
```

Actual router:

```text id="r13a90"
192.168.10.1
```

Likely symptom:

```text id="r13a91"
Local LAN
✅

Remote Networks
❌
```

---

# 🛠️ Routing Troubleshooting Workflow

Use a structured approach:

```text id="r13a92"
Can Host Reach Itself?
        ↓
Can Host Reach Local Devices?
        ↓
Can Host Reach Default Gateway?
        ↓
Is Router Interface Up?
        ↓
Does Router Have Destination Route?
        ↓
Is Next Hop Reachable?
        ↓
Does Next Router Have Route?
        ↓
Does Destination Have Return Path?
        ↓
Any ACL / Firewall Blocking Traffic?
```

---

# 📋 Useful Cisco Commands

| Command | Purpose |
|---|---|
| `show ip route` | View IPv4 routing table |
| `show ip interface brief` | Quick interface/IP status |
| `show running-config` | View configuration |
| `ping` | Test reachability |
| `traceroute` | Trace Layer 3 path |
| `ip route ...` | Create static route |
| `no ip route ...` | Remove static route |

---

# 📋 Useful Windows Commands

| Command | Purpose |
|---|---|
| `ipconfig` | View IP configuration |
| `ipconfig /all` | Detailed configuration |
| `route print` | View routing table |
| `tracert` | Trace Layer 3 path |
| `ping` | Test reachability |
| `Get-NetRoute` | PowerShell routing table |
| `Get-NetIPConfiguration` | PowerShell network configuration |
| `Test-NetConnection` | Connectivity testing |

---

# 📋 Routing Quick Reference

| Concept | Meaning |
|---|---|
| Routing | Forwarding packets between IP networks |
| Routing Table | List of known routes |
| Connected Route | Network directly attached to router |
| Remote Network | Network reached through another router |
| Static Route | Manually configured route |
| Default Route | Used when no more specific route matches |
| Next Hop | Next router toward destination |
| Exit Interface | Interface packet leaves through |
| Longest-Prefix Match | Most specific matching route wins |
| Administrative Distance | Preference between route sources |
| Metric | Path preference within routing protocol |
| Dynamic Routing | Routers exchange route information |

---

# 🧠 Knowledge Check

### 1.

At what OSI layer does routing primarily occur?

### 2.

What address does a router primarily examine when forwarding a packet?

### 3.

What command displays a Cisco IPv4 routing table?

### 4.

What does `C` mean in a Cisco routing table?

### 5.

What does `S` mean?

### 6.

What is a next hop?

### 7.

What is the IPv4 default route?

### 8.

What happens when multiple routes match a destination?

### 9.

Why is a return route important?

### 10.

Which Windows command displays the routing table?

---

# ✅ Answers

1. **Layer 3 — Network**
2. **Destination IP address**
3. **`show ip route`**
4. **Connected**
5. **Static**
6. **The next router toward the destination**
7. **`0.0.0.0/0`**
8. **The most specific matching route is preferred using longest-prefix match**
9. **Replies need a path back to the source**
10. **`route print`**

---

# 🎓 Network+ Challenge 1

A router has:

```text id="r13a93"
10.0.0.0/8

10.10.0.0/16

10.10.20.0/24
```

Destination:

```text id="r13a94"
10.10.20.50
```

Which route is selected?

> **10.10.20.0/24**

because it is the longest and most specific matching prefix.

---

# 🎓 Network+ Challenge 2

A PC can reach devices on its local subnet but cannot reach any remote subnet.

What should you verify early?

> **The PC's default gateway.**

---

# 🎓 Network+ Challenge 3

R-01 has a correct route to a server network.

Traffic reaches the server, but replies never return.

What should you investigate?

> **The return route toward the source network.**

---

# 🎓 Network+ Challenge 4

What does:

```text id="r13a95"
0.0.0.0/0
```

represent?

> **The IPv4 default route.**

---

# 🎓 Network+ Challenge 5

Which protocol is commonly used as a link-state interior routing protocol?

### A. DNS
### B. OSPF
### C. DHCP
### D. ARP

> **Answer: B — OSPF**

---

# 🎓 Network+ Challenge 6

Which routing protocol is strongly associated with routing between autonomous systems on the Internet?

> **BGP**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- Routing occurs at Layer 3.
- Routers forward packets using destination IP addresses.
- Hosts use default gateways for remote networks.
- Routers use routing tables.
- Directly connected networks are learned from active router interfaces.
- Static routes are manually configured.
- Remote routes need a next hop or appropriate exit path.
- Routing must work in both directions.
- A default route is `0.0.0.0/0`.
- The most specific matching route wins.
- Administrative distance compares routing sources.
- Metrics help routing protocols compare paths.
- Dynamic routing protocols exchange routing information.
- OSPF, BGP, RIP, and EIGRP are important names to recognize.
- Windows computers also maintain routing tables.
- `show ip route`, `route print`, and `Get-NetRoute` are important troubleshooting tools.

---

# 🧪 Next Step — Lab 13

Now you'll build a network containing:

```text id="r13a96"
LAN A
  ↓
R-01
  ↓
Transit Network
  ↓
R-02
  ↓
LAN B
```

You'll:

- Inspect connected routes
- Add static routes
- Verify next hops
- Trace traffic
- Break the return route
- Break a next hop
- Use a default route
- Troubleshoot routing failures

➡️ **[Lab 13 — Routing Fundamentals](../labs/lab-13-routing-fundamentals.md)**

---

# 📍 Course Progress

```text id="r13a97"
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ COMPLETE

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES

✅ Lesson 11 — Switching Fundamentals
✅ Lab 11

✅ Lesson 12 — VLANs & Network Segmentation
✅ Lab 12

✅ Lesson 13 — Routing Fundamentals
        ↓
🟡 NEXT: Lab 13

⬜ Lesson 14 — DHCP
⬜ Lab 14

⬜ Lesson 15 — DNS
⬜ Lab 15

⬜ Lesson 16 — NAT & Address Translation
⬜ Lab 16
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**
