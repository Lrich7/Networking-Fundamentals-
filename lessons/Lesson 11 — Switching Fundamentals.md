# 📘 Lesson 11 — Switching Fundamentals

Welcome to **Lesson 11 of Networking Fundamentals**.

You've completed Phase 2 and learned how devices use:

```text
MAC Addresses
      ↓
IPv4 / IPv6 Addresses
      ↓
TCP / UDP
      ↓
Ports & Protocols
```

Now we're beginning:

> 🟣 **Phase 3 — Switching, Routing & Services**

We'll start by taking a much deeper look at one of the most important devices on a LAN:

> **The Network Switch**

You've already used switches in several Packet Tracer labs.

Now you'll learn what the switch is actually doing.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain the purpose of a network switch
- Explain Layer 2 switching
- Understand Ethernet frame forwarding
- Explain MAC address learning
- Read a MAC address table
- Explain known unicast forwarding
- Explain unknown unicast flooding
- Explain broadcast forwarding
- Understand multicast at a basic level
- Explain collision domains
- Explain broadcast domains
- Understand full-duplex Ethernet
- Explain speed and duplex negotiation
- Understand managed vs. unmanaged switches
- Understand switch ports and interfaces
- Use basic Cisco IOS commands
- Explain why network loops are dangerous
- Understand the purpose of Spanning Tree Protocol
- Recognize common switching problems
- Perform basic switch troubleshooting

---

# 🎓 Network+ Focus

For **CompTIA Network+ N10-009**, pay particular attention to:

- Layer 2 switching
- MAC addresses
- MAC address tables
- Frame forwarding
- Broadcast domains
- Collision domains
- Speed and duplex
- Managed switches
- Switch ports
- PoE
- Network loops
- Spanning Tree Protocol
- Switch troubleshooting

These concepts also prepare you directly for:

> **Lesson 12 — VLANs and Network Segmentation**

---

# 🔀 What Does a Switch Do?

A switch connects devices on a local network.

Example:

```text
PC-01 ─────┐
           │
PC-02 ─────┤
           │
Printer ───┤── SW-01
           │
Server ────┤
           │
AP-01 ─────┘
```

But a switch doesn't simply send every Ethernet frame everywhere.

Modern switches make forwarding decisions using:

> **MAC Addresses**

---

# 🧱 What Layer Does a Switch Use?

Traditional Ethernet switches primarily operate at:

> **OSI Layer 2 — Data Link**

They examine Ethernet frames and use:

> **MAC addresses**

to make forwarding decisions.

---

# 📦 Ethernet Frame Review

Remember the simplified Ethernet frame:

```text
┌─────────────────────────┐
│ Destination MAC Address │
├─────────────────────────┤
│ Source MAC Address      │
├─────────────────────────┤
│ Type / Length           │
├─────────────────────────┤
│ Payload                 │
├─────────────────────────┤
│ FCS                     │
└─────────────────────────┘
```

For switching, two fields are especially important:

```text
Source MAC
Destination MAC
```

---

# 🧠 The Switch Learns From the Source MAC

This is extremely important:

> **A switch learns MAC addresses by examining the SOURCE MAC address of incoming frames.**

Suppose:

```text
PC-01
MAC: AA-AA-AA-AA-AA-AA
```

sends a frame into:

```text
SW-01 Port 1
```

The switch sees:

```text
Source MAC:
AA-AA-AA-AA-AA-AA

Incoming Port:
1
```

It learns:

```text
AA-AA-AA-AA-AA-AA
        ↓
      Port 1
```

---

# 📋 MAC Address Table

The switch stores this information in its:

> **MAC Address Table**

You may also hear:

- CAM table
- Forwarding table
- MAC table

Example:

| MAC Address | Port |
|---|---|
| AA-AA-AA-AA-AA-AA | Fa0/1 |
| BB-BB-BB-BB-BB-BB | Fa0/2 |
| CC-CC-CC-CC-CC-CC | Fa0/3 |

---

# 🔍 Example Network

Consider:

```text
PC-01 ─ Fa0/1
             \
              SW-01
             /
PC-02 ─ Fa0/2
```

PC-01:

```text
MAC:
AAAA.AAAA.AAAA
```

PC-02:

```text
MAC:
BBBB.BBBB.BBBB
```

After both devices send traffic, the switch might know:

```text
AAAA.AAAA.AAAA → Fa0/1

BBBB.BBBB.BBBB → Fa0/2
```

---

# ➡️ Known Unicast Forwarding

Suppose PC-01 sends a frame to PC-02.

Destination MAC:

```text
BBBB.BBBB.BBBB
```

The switch checks its table:

```text
BBBB.BBBB.BBBB
        ↓
      Fa0/2
```

The switch forwards the frame:

> **Only out Fa0/2**

This is called:

> **Known Unicast Forwarding**

---

# ❓ Unknown Unicast

What happens if the switch doesn't know where the destination MAC lives?

Suppose:

```text
Destination MAC:
DDDD.DDDD.DDDD
```

isn't in the table.

The switch performs:

> **Unknown Unicast Flooding**

It sends the frame out other relevant ports in the same VLAN except the port where the frame arrived.

---

# 🌊 Flooding

Conceptually:

```text
             SW-01
          /    |    \
         /     |     \
      PC-01  PC-02  PC-03
        ↑
     Incoming

Unknown destination
        ↓

SW-01 sends copies toward
other ports in that VLAN.
```

If the destination responds, the switch can learn its source MAC.

Future frames can then be forwarded more efficiently.

---

# 📢 Broadcast Frames

An Ethernet broadcast uses:

```text
FF:FF:FF:FF:FF:FF
```

A switch forwards a broadcast out other relevant ports within the same:

> **Broadcast domain / VLAN**

Example:

```text
PC-01
  │
  │ Broadcast
  ▼
SW-01
 ├──── PC-02
 ├──── PC-03
 └──── PC-04
```

---

# 🧠 Important Difference

A switch:

> **Does not normally forward a frame back out the port where that frame arrived.**

---

# 👥 Multicast

Multicast represents:

> **One sender to a selected group of receivers**

Basic switches may flood some multicast traffic unless multicast-management features are being used.

Later networking concepts can improve multicast handling.

For now, understand the difference:

```text
Unicast
One → One

Broadcast
One → Everyone in broadcast domain

Multicast
One → Selected Group
```

---

# 🔄 How a Switch Handles a Frame

When a frame arrives:

```text
FRAME ARRIVES
      ↓
Read Source MAC
      ↓
Learn Source MAC + Port
      ↓
Read Destination MAC
      ↓
Check MAC Table
```

Then:

```text
Known Destination?
       │
       ├── YES → Forward to appropriate port
       │
       └── NO → Flood within the VLAN
```

Broadcast?

```text
Flood within the VLAN
```

This process happens extremely quickly.

---

# ⏳ MAC Address Aging

MAC table entries aren't necessarily permanent.

Dynamic entries eventually:

> **Age out**

if the switch stops seeing traffic from that MAC address.

This prevents the MAC table from filling indefinitely with outdated information.

---

# 🔌 Collision Domains

Older Ethernet networks using hubs shared a collision domain.

Example:

```text
PC ─┐
PC ─┼── HUB
PC ─┘
```

Devices shared the same Ethernet medium.

Modern switches change this.

---

# ⭐ Switch Ports and Collision Domains

Each switch port normally creates its own:

> **Collision domain**

Example:

```text
PC-01 ── SW-01 ── PC-02
```

Each switch link is a separate collision domain.

---

# 📢 Broadcast Domains

This is different from collision domains.

A basic switch does:

> **Not automatically separate broadcast domains**

Without VLAN segmentation or routing:

```text
PC-01
PC-02
PC-03
PC-04
```

may all share the same broadcast domain.

---

# 🧠 Memorize This

```text
SWITCH PORT
      ↓
Separates Collision Domains
```

But:

```text
ROUTER / VLAN BOUNDARY
      ↓
Can Separate Broadcast Domains
```

We'll explore VLAN broadcast domains in Lesson 12.

---

# ↔️ Half Duplex

Half-duplex communication means:

> **A device can transmit or receive, but not both simultaneously on that link.**

Think:

```text
Walkie-Talkie
```

One side talks at a time.

---

# ↔️ Full Duplex

Full duplex means:

> **Both sides can transmit and receive simultaneously.**

Modern switched Ethernet normally uses:

> **Full Duplex**

---

# 🚫 Collisions and Full Duplex

Properly operating full-duplex switched Ethernet doesn't use the old collision-detection behavior associated with shared half-duplex Ethernet.

This is one reason modern switched networks are far more efficient than old hub-based networks.

---

# ⚙️ Speed and Duplex

Ethernet interfaces can operate at different speeds.

Examples:

```text
100 Mbps

1 Gbps

2.5 Gbps

5 Gbps

10 Gbps
```

Interfaces can often automatically negotiate:

```text
Speed
+
Duplex
```

---

# 🤝 Auto-Negotiation

Modern Ethernet commonly uses:

> **Auto-Negotiation**

Devices determine compatible link settings.

Usually:

```text
AUTO
```

is the correct choice unless there is a specific reason to configure otherwise.

---

# ⚠️ Duplex Mismatch

If one side of a link operates differently from the other, poor performance may occur.

Possible symptoms:

- Slow network
- Intermittent performance
- Interface errors
- Retransmissions
- Poor throughput

This is less common with modern equipment but remains an important troubleshooting concept.

---

# 🧰 Managed vs. Unmanaged Switches

## Unmanaged Switch

An unmanaged switch generally provides basic switching with little or no administrative configuration.

Typical use:

```text
Plug in
      ↓
Connect devices
      ↓
Switch traffic
```

---

# 🛠️ Managed Switch

A managed switch provides administrative features such as:

- VLANs
- Trunking
- Port configuration
- Spanning Tree
- Port security
- Monitoring
- SNMP
- PoE management
- Link aggregation
- Logging
- Remote management

Business networks commonly use:

> **Managed switches**

---

# ⚡ Power over Ethernet — PoE

Some switches can provide electrical power over Ethernet cabling.

This is:

> **Power over Ethernet — PoE**

Common PoE devices include:

```text
VoIP Phones

Wireless Access Points

Security Cameras
```

This can eliminate the need for separate power adapters at the endpoint.

---

# 🧠 Real-World Clue

Remember:

> Pulling a device's wall power adapter may not turn it off if it receives power through Ethernet.

A PoE-powered device can receive both:

```text
DATA
+
POWER
```

over the Ethernet connection.

---

# 🔌 Switch Interface Names

Cisco switches may display ports such as:

```text
FastEthernet0/1

FastEthernet0/2
```

often shortened:

```text
Fa0/1

Fa0/2
```

Gigabit interfaces may appear as:

```text
GigabitEthernet0/1
```

or:

```text
Gi0/1
```

Exact naming depends on the device model.

---

# 🖥️ Cisco IOS Basics

Cisco switches commonly use:

> **Cisco IOS-style command-line interfaces**

Packet Tracer lets us practice this safely.

---

# 👤 User EXEC Mode

A Cisco CLI may initially show:

```text
Switch>
```

This is:

> **User EXEC Mode**

---

# 🔐 Privileged EXEC Mode

Enter:

```text
enable
```

Prompt becomes:

```text
Switch#
```

This is:

> **Privileged EXEC Mode**

---

# ⚙️ Global Configuration Mode

Enter:

```text
configure terminal
```

or:

```text
conf t
```

Prompt:

```text
Switch(config)#
```

---

# 🔌 Interface Configuration Mode

Example:

```text
interface fastethernet 0/1
```

Prompt:

```text
Switch(config-if)#
```

Now you're configuring that interface.

---

# 🏷️ Rename the Switch

From configuration mode:

```text
hostname SW-01
```

Prompt becomes:

```text
SW-01(config)#
```

Using meaningful hostnames makes administration easier.

---

# 📋 View Interfaces

From privileged EXEC mode:

```text
show interfaces status
```

Depending on the Packet Tracer switch/model, you can see information about interfaces and their state.

---

# 📋 View MAC Address Table

Use:

```text
show mac address-table
```

You may see:

```text
Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
1       aaaa.aaaa.aaaa    DYNAMIC     Fa0/1
1       bbbb.bbbb.bbbb    DYNAMIC     Fa0/2
```

This is one of the most important commands in this lesson.

---

# 🧠 What Does DYNAMIC Mean?

A:

```text
DYNAMIC
```

entry was learned automatically from network traffic.

---

# 🧹 Clear Dynamic MAC Entries

On supported Cisco IOS/Packet Tracer devices:

```text
clear mac address-table dynamic
```

Then:

```text
show mac address-table
```

The learned entries may disappear.

Generate traffic again.

Then check:

```text
show mac address-table
```

The switch relearns them.

---

# 🔍 Interface Details

You can inspect an interface using commands such as:

```text
show interfaces fastethernet 0/1
```

This can provide information including:

- Link state
- Protocol state
- Speed
- Duplex
- Errors
- Traffic counters

Available output varies by switch/model.

---

# 🔴 Administratively Down

An administrator can disable an interface.

Configuration:

```text
interface fastethernet 0/1
shutdown
```

To enable:

```text
no shutdown
```

---

# 🧠 Troubleshooting Clue

If an interface is:

```text
administratively down
```

the port has been disabled through configuration.

That is different from simply having an unplugged cable.

---

# 🔁 Network Loops

Now for a very important switching problem.

Imagine two switches:

```text
SW-01 ───── SW-02
  │           │
  └───────────┘
```

There are two Layer 2 paths between them.

Redundancy sounds good.

But Layer 2 Ethernet doesn't have a TTL field in the same way an IP packet does.

A switching loop can create serious problems.

---

# 🌪️ Broadcast Storm

Suppose a broadcast enters a switching loop.

Each switch can continue forwarding copies.

Conceptually:

```text
Broadcast
    ↓
SW-01
    ↓
SW-02
    ↓
SW-01
    ↓
SW-02
    ↓
...
```

This can create:

> **A Broadcast Storm**

---

# 💥 Effects of a Switching Loop

Possible symptoms include:

- Network becomes extremely slow
- Switch utilization spikes
- Broadcast traffic explodes
- MAC tables become unstable
- Users lose connectivity
- Large portions of the LAN become unusable

---

# 🛡️ Spanning Tree Protocol

To prevent Layer 2 loops, switches commonly use:

> **Spanning Tree Protocol — STP**

STP can detect redundant Layer 2 paths and logically block selected paths to create a loop-free topology.

Conceptually:

```text
       SW-01
       /   \
      /     \
   SW-02 ── SW-03
          X
       Blocked Path
```

The redundant physical path can remain available.

But STP prevents all redundant Layer 2 paths from forwarding simultaneously.

---

# 🧠 Why Keep a Blocked Link?

Because if the active path fails:

```text
ACTIVE PATH
     ↓
   FAILS
```

STP can potentially reconverge and allow a redundant path to forward.

This provides:

> **Redundancy without creating a Layer 2 loop**

---

# ⚠️ STP Is Deeper Than This

Spanning Tree includes concepts such as:

- Root bridge
- Bridge IDs
- Root ports
- Designated ports
- Port roles/states
- Path costs
- RSTP

We'll keep this introduction focused on:

> **Why STP exists**

You don't need to master every STP calculation yet.

---

# 🛠️ Switching Troubleshooting Workflow

Suppose a user reports:

> "My computer has no network."

Start with basics.

```text
1. Is the cable connected?
        ↓
2. Does the switch port show link?
        ↓
3. Is the NIC enabled?
        ↓
4. Is the switch interface enabled?
        ↓
5. Is the correct MAC learned?
        ↓
6. Is the port configured correctly?
        ↓
7. Are there interface errors?
        ↓
8. Is the problem local or shared?
```

---

# 🛠️ Scenario 1 — One User Fails

```text
PC-01 ❌

PC-02 ✅

PC-03 ✅
```

All connect to SW-01.

Start by investigating:

```text
PC-01
Cable
NIC
Switch Port
Port Configuration
```

A total switch failure is less likely because other users are working.

---

# 🛠️ Scenario 2 — Everyone Fails

```text
PC-01 ❌
PC-02 ❌
PC-03 ❌
PC-04 ❌
```

All connect to the same switch.

Now consider:

- Switch power
- Switch failure
- Uplink
- Shared configuration
- Broadcast storm
- Upstream network issue

Look for:

> **Shared dependencies**

---

# 🛠️ Scenario 3 — MAC Moves

Suppose a PC is moved:

```text
Fa0/1
 ↓
Fa0/8
```

After the device generates traffic, the switch should learn:

```text
PC MAC
 ↓
Fa0/8
```

The MAC address identifies the interface—not the physical switch port forever.

---

# 🛠️ Scenario 4 — Port Disabled

User has:

```text
No Link
```

You inspect the switch and discover:

```text
Fa0/10
administratively down
```

Likely cause:

> **The interface was shut down through configuration.**

---

# 🛠️ Scenario 5 — Network Suddenly Collapses

Someone connects an extra cable between two switches.

Immediately:

```text
Network becomes extremely slow
```

Potential cause:

> **Layer 2 loop / broadcast storm**

Investigate:

- Recent cabling changes
- STP
- Switch logs
- Interface activity

---

# 📋 Switching Quick Reference

| Concept | Meaning |
|---|---|
| Switch | Connects devices at Layer 2 |
| MAC Table | Maps MAC addresses to ports |
| Known Unicast | Forward toward known destination |
| Unknown Unicast | Flood within VLAN |
| Broadcast | Flood within broadcast domain/VLAN |
| Collision Domain | Normally one per switch port |
| Broadcast Domain | Shared until VLAN/routing boundary |
| Full Duplex | Send and receive simultaneously |
| PoE | Power + data over Ethernet |
| STP | Prevents Layer 2 loops |
| Managed Switch | Configurable enterprise/business switch |

---

# 📋 Useful Cisco Commands

| Command | Purpose |
|---|---|
| `enable` | Enter privileged EXEC |
| `configure terminal` | Enter configuration mode |
| `hostname SW-01` | Rename switch |
| `show mac address-table` | View learned MACs |
| `show interfaces status` | View interface status |
| `show interfaces` | Detailed interfaces |
| `show running-config` | View active configuration |
| `interface fa0/1` | Configure interface |
| `shutdown` | Disable interface |
| `no shutdown` | Enable interface |
| `clear mac address-table dynamic` | Clear learned dynamic MACs |

---

# 🧠 Knowledge Check

### 1.

At which OSI layer does a traditional Ethernet switch primarily operate?

### 2.

Which MAC address does a switch use to learn where a device is located?

### 3.

What happens when the destination MAC is known?

### 4.

What happens when the destination MAC is unknown?

### 5.

What Ethernet MAC represents broadcast?

### 6.

How many collision domains does a typical switch port create?

### 7.

Does a basic switch automatically separate broadcast domains?

### 8.

What does full duplex mean?

### 9.

What protocol helps prevent Layer 2 loops?

### 10.

Which Cisco command displays the MAC address table?

---

# ✅ Answers

1. **Layer 2 — Data Link**
2. **Source MAC**
3. **The frame is forwarded toward the appropriate port**
4. **It is flooded within the relevant VLAN**
5. **FF:FF:FF:FF:FF:FF**
6. **Each switch port normally represents a separate collision domain**
7. **No**
8. **Both sides can transmit and receive simultaneously**
9. **Spanning Tree Protocol — STP**
10. **`show mac address-table`**

---

# 🎓 Network+ Challenge 1

A switch receives a frame from:

```text
Source MAC:
AAAA.AAAA.AAAA

Port:
Fa0/5
```

What does the switch learn?

> **AAAA.AAAA.AAAA is reachable through Fa0/5**

---

# 🎓 Network+ Challenge 2

A switch receives a frame for an unknown destination MAC.

What does it normally do?

### A. Drop every unknown frame
### B. Send it only to the router
### C. Flood it within the VLAN
### D. Convert it to IPv6

> **Answer: C**

---

# 🎓 Network+ Challenge 3

Which device historically places multiple attached devices in one shared collision domain?

### A. Switch
### B. Hub
### C. Router
### D. Firewall

> **Answer: B — Hub**

---

# 🎓 Network+ Challenge 4

What is the main purpose of STP?

### A. Assign IP addresses
### B. Resolve DNS
### C. Prevent Layer 2 switching loops
### D. Encrypt Ethernet

> **Answer: C**

---

# 🎓 Network+ Challenge 5

A VoIP phone stays powered after its external power adapter is disconnected.

What is a likely explanation?

> **The phone is receiving Power over Ethernet from the switch.**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- Switches primarily operate at Layer 2.
- Switches make forwarding decisions using MAC addresses.
- Switches learn from the source MAC address.
- MAC tables map MAC addresses to switch ports.
- Known unicasts are forwarded toward the known destination.
- Unknown unicasts are flooded within the VLAN.
- Broadcasts are flooded within their broadcast domain/VLAN.
- Each switch port normally creates a separate collision domain.
- A basic switch doesn't automatically separate broadcast domains.
- Modern switched Ethernet normally uses full duplex.
- Speed and duplex can be negotiated.
- Managed switches provide advanced configuration and monitoring.
- PoE can provide power through Ethernet.
- Layer 2 loops can cause broadcast storms.
- STP helps prevent switching loops.
- Cisco CLI commands allow you to inspect and configure switches.

---

# 🧪 Next Step — Lab 11

Now you'll build a switched LAN and watch the switch learn MAC addresses.

You'll also use the Cisco CLI instead of relying only on the Packet Tracer GUI.

➡️ **[Lab 11 — Switching Fundamentals](../labs/lab-11-switching-fundamentals.md)**

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ COMPLETE

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES

✅ Lesson 11 — Switching Fundamentals
        ↓
🟡 NEXT: Lab 11 — Switching Fundamentals
        ↓
⬜ Lesson 12 — VLANs & Network Segmentation
⬜ Lab 12
        ↓
⬜ Lesson 13 — Routing Fundamentals
⬜ Lab 13
```

---

# ➡️ After the Lab

Continue to:

> **📘 Lesson 12 — VLANs and Network Segmentation**

You'll take one physical switch and divide it into multiple logical networks.

That's where concepts such as:

```text
VLAN 10 — Employees
VLAN 20 — Servers
VLAN 30 — Voice
VLAN 40 — Guest
```

start to make sense.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**