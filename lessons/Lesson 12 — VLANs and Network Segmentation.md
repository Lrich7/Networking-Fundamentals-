# 📘 Lesson 12 — VLANs and Network Segmentation

Welcome to **Lesson 12 of Networking Fundamentals**.

In Lesson 11, you learned how a switch:

```text
Receives Ethernet Frames
        ↓
Learns Source MAC Addresses
        ↓
Builds a MAC Address Table
        ↓
Forwards Frames
```

But a basic switched network has an important limitation.

By default, devices may all belong to the same logical Layer 2 network.

Imagine a company with:

```text
Employees
Servers
VoIP Phones
Security Cameras
Guest Wi-Fi
IT Management
```

Should all of those devices share the same network?

Usually:

> **No.**

This is where VLANs become important.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain what a VLAN is
- Explain why VLANs are used
- Understand network segmentation
- Explain broadcast domains
- Understand VLAN IDs
- Explain the relationship between VLANs and IP subnets
- Explain access ports
- Explain trunk ports
- Understand IEEE 802.1Q
- Explain VLAN tagging
- Understand the native VLAN concept
- Create VLANs using Cisco IOS
- Assign switch ports to VLANs
- Verify VLAN configuration
- Configure a basic trunk
- Explain why devices in different VLANs cannot communicate directly at Layer 2
- Explain inter-VLAN routing
- Understand router-on-a-stick
- Understand Layer 3 switching
- Recognize common VLAN configuration problems
- Apply VLANs to a small-business network

---

# 🎓 Network+ Focus

For **CompTIA Network+ N10-009**, pay particular attention to:

- VLANs
- Network segmentation
- Broadcast domains
- Access ports
- Trunk ports
- IEEE 802.1Q
- VLAN tagging
- Native VLAN
- Inter-VLAN routing
- Layer 2 vs. Layer 3
- VLAN troubleshooting

A key concept is:

> **A VLAN creates a separate logical Layer 2 broadcast domain.**

---

# 🧩 What Is a VLAN?

VLAN stands for:

> **Virtual Local Area Network**

A VLAN allows us to divide switching infrastructure into separate logical Layer 2 networks.

Consider:

```text
PC-01 ─┐
PC-02 ─┤
PC-03 ─┤── SW-01
PC-04 ─┘
```

Without additional segmentation, all four PCs may belong to the same VLAN.

---

# 📢 One Broadcast Domain

If PC-01 sends a Layer 2 broadcast:

```text
FF:FF:FF:FF:FF:FF
```

the switch can flood it toward the other devices in that VLAN.

Conceptually:

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

# 🧱 Why Segment a Network?

Now imagine those devices belong to different business functions:

```text
PC-01 → Employee

PC-02 → Employee

PC-03 → Server

PC-04 → Guest
```

We may want to separate them for:

- Security
- Performance
- Organization
- Broadcast control
- Policy enforcement
- Troubleshooting
- Network design

---

# 🧩 VLAN Example

We could create:

```text
VLAN 10
EMPLOYEES

VLAN 20
SERVERS

VLAN 30
GUEST
```

Then assign switch ports accordingly.

Conceptually:

```text
             SW-01

PC-01 ───── VLAN 10
PC-02 ───── VLAN 10

SRV-01 ──── VLAN 20

GUEST-01 ── VLAN 30
```

One physical switch now supports:

> **Three logical Layer 2 networks**

---

# 📢 VLANs Create Separate Broadcast Domains

Suppose PC-01 sends a broadcast.

PC-01 belongs to:

```text
VLAN 10
```

The switch floods the broadcast only within:

> **VLAN 10**

It does not automatically forward the broadcast into:

```text
VLAN 20
VLAN 30
```

---

# 🧠 Important Concept

```text
VLAN 10
=
Broadcast Domain 1

VLAN 20
=
Broadcast Domain 2

VLAN 30
=
Broadcast Domain 3
```

This is one of the major reasons VLANs are useful.

---

# 🏢 Real-World VLAN Design

A small business might use:

| VLAN | Name | Purpose |
|---:|---|---|
| 10 | EMPLOYEES | Employee computers |
| 20 | SERVERS | Servers |
| 30 | VOICE | VoIP phones |
| 40 | GUEST | Guest Wi-Fi |
| 50 | CAMERAS | Security cameras |
| 99 | MANAGEMENT | Network management |

The exact VLAN numbers are:

> **Design choices**

There is nothing magical about VLAN 10 being employees.

---

# 🔢 VLAN IDs

IEEE 802.1Q VLAN IDs use a 12-bit VLAN identifier.

The usable normal VLAN ID range is generally:

```text
1 – 4094
```

However, some IDs have special or reserved purposes.

For beginner administration, you'll commonly see values such as:

```text
10
20
30
40
50
99
```

---

# ⚠️ VLAN 1

Cisco switches commonly use:

```text
VLAN 1
```

as the default VLAN.

Switch ports may initially belong to VLAN 1.

In production environments, administrators often avoid using VLAN 1 for normal user traffic where practical.

For our labs, we'll create dedicated VLANs.

---

# 🏷️ Naming VLANs

Instead of remembering:

```text
VLAN 10
```

we can name it:

```text
EMPLOYEES
```

Likewise:

```text
VLAN 20
SERVERS
```

Names make configurations easier to understand.

---

# 🖥️ Creating a VLAN

On a Cisco switch:

```text
enable
```

Then:

```text
configure terminal
```

Create VLAN 10:

```text
vlan 10
```

Name it:

```text
name EMPLOYEES
```

Then:

```text
exit
```

Create VLAN 20:

```text
vlan 20
name SERVERS
exit
```

---

# 📋 Verify VLANs

Use:

```text
show vlan brief
```

You might see:

```text
VLAN  Name        Status
----  ----------  ------
1     default     active
10    EMPLOYEES   active
20    SERVERS     active
```

This will become one of your most useful VLAN commands.

---

# 🔌 What Is an Access Port?

An:

> **Access Port**

normally carries traffic for a single VLAN toward an endpoint.

Examples:

```text
PC
Printer
Server
Camera
```

Suppose PC-01 should belong to VLAN 10.

We configure its switch port as:

```text
interface fastethernet 0/1
switchport mode access
switchport access vlan 10
```

Now Fa0/1 belongs to:

```text
VLAN 10
```

---

# 🧠 Access Port Concept

```text
PC-01
  │
  │
Fa0/1
  │
  │ Access VLAN 10
  ▼
SW-01
```

The PC normally doesn't need to understand that the switch port belongs to VLAN 10.

The switch handles that VLAN association.

---

# 🧪 Multiple Access Ports

Suppose:

```text
Fa0/1 → VLAN 10
Fa0/2 → VLAN 10
Fa0/3 → VLAN 20
Fa0/4 → VLAN 20
```

Then:

```text
PC-01 ─┐
       ├── VLAN 10
PC-02 ─┘


PC-03 ─┐
       ├── VLAN 20
PC-04 ─┘
```

---

# 📋 Configure Multiple Ports

Cisco IOS can often configure a range:

```text
interface range fastethernet 0/1 - 2
```

Then:

```text
switchport mode access
switchport access vlan 10
```

For another range:

```text
interface range fastethernet 0/3 - 4
switchport mode access
switchport access vlan 20
```

---

# 🧠 VLANs and MAC Tables

Switch MAC tables also associate learned MAC addresses with VLAN information.

You may see something like:

```text
Vlan    Mac Address       Type       Ports
----    -----------       -------    -----
10      aaaa.aaaa.aaaa    DYNAMIC    Fa0/1
10      bbbb.bbbb.bbbb    DYNAMIC    Fa0/2
20      cccc.cccc.cccc    DYNAMIC    Fa0/3
```

This helps the switch keep Layer 2 forwarding separate between VLANs.

---

# 🌐 VLANs and IP Subnets

A very common network design is:

> **One IP subnet per VLAN**

Example:

```text
VLAN 10
Employees

192.168.10.0/24
```

and:

```text
VLAN 20
Servers

192.168.20.0/24
```

and:

```text
VLAN 30
Guest

192.168.30.0/24
```

---

# ⭐ Recommended Mental Model

Think:

```text
VLAN
=
Layer 2 Boundary
```

and:

```text
IP Subnet
=
Layer 3 Boundary
```

In a clean network design, they commonly line up:

```text
VLAN 10
        ↓
192.168.10.0/24


VLAN 20
        ↓
192.168.20.0/24
```

---

# ❓ Can Different VLANs Communicate?

Suppose:

```text
PC-01
VLAN 10
192.168.10.10
```

wants to communicate with:

```text
SRV-01
VLAN 20
192.168.20.10
```

Can the Layer 2 switch simply forward the traffic from VLAN 10 into VLAN 20?

> **No.**

The VLANs are separate Layer 2 networks.

To communicate between them, we need:

> **Layer 3 Routing**

This is called:

> **Inter-VLAN Routing**

---

# 🔀 Two Switches

Now imagine:

```text
PC-01 ─ SW-01 ───── SW-02 ─ PC-02
```

Both PCs should belong to:

```text
VLAN 10
```

How do we carry VLAN 10 between the switches?

We could dedicate one physical cable to VLAN 10.

Then another cable to VLAN 20.

Then another to VLAN 30.

That would become inefficient.

Instead we use:

> **A Trunk**

---

# 🚚 What Is a Trunk Port?

A trunk port can carry traffic for:

> **Multiple VLANs**

across one physical link.

Example:

```text
                TRUNK
SW-01 ======================= SW-02

Carries:
VLAN 10
VLAN 20
VLAN 30
```

---

# 🏷️ VLAN Tagging

If multiple VLANs share one link, the receiving switch needs to know:

> **Which VLAN does each Ethernet frame belong to?**

IEEE:

> **802.1Q**

provides VLAN tagging.

---

# 📦 802.1Q Tag

Conceptually, the Ethernet frame receives VLAN information:

```text
Ethernet Frame

Destination MAC
Source MAC
802.1Q VLAN Tag
EtherType
Payload
FCS
```

The tag can identify:

```text
VLAN 10
```

or:

```text
VLAN 20
```

etc.

---

# 🧠 Access vs. Trunk

This distinction is critical.

## Access Port

```text
Endpoint
   │
   │ One VLAN
   ▼
Switch
```

Typically:

> Carries traffic for one VLAN.

## Trunk Port

```text
Switch
   │
   │ Multiple VLANs
   ▼
Switch
```

Typically:

> Carries traffic for multiple VLANs.

---

# 📋 Access vs. Trunk Table

| Feature | Access | Trunk |
|---|---|---|
| Typical connection | Endpoint | Switch/network device |
| VLANs carried | Usually one | Multiple |
| 802.1Q tagging | Usually not toward ordinary endpoint | Common |
| Example | PC → Switch | Switch → Switch |

---

# 🖥️ Configure a Trunk

Suppose:

```text
SW-01 Gi0/1
        ↓
SW-02 Gi0/1
```

On SW-01:

```text
interface gigabitethernet 0/1
switchport mode trunk
```

On SW-02:

```text
interface gigabitethernet 0/1
switchport mode trunk
```

Exact interface names depend on the switch model.

---

# 📋 Verify Trunks

Use:

```text
show interfaces trunk
```

This can show:

- Trunk interfaces
- Encapsulation
- Native VLAN
- Allowed VLANs
- Active VLANs

---

# 🚦 Allowed VLANs

A trunk doesn't necessarily need to carry every VLAN.

Administrators can restrict which VLANs are allowed.

Conceptually:

```text
Trunk

Allowed:
10
20
30

Not Allowed:
40
50
```

This can improve:

- Security
- Control
- Troubleshooting
- Network design

---

# 🏷️ Native VLAN

802.1Q trunks also have the concept of a:

> **Native VLAN**

Traffic belonging to the native VLAN is normally sent untagged on an 802.1Q trunk.

Cisco switches commonly default the native VLAN to:

```text
VLAN 1
```

unless changed.

---

# ⚠️ Native VLAN Mismatch

Suppose:

```text
SW-01 Native VLAN
=
99
```

but:

```text
SW-02 Native VLAN
=
1
```

This creates a:

> **Native VLAN mismatch**

and can lead to connectivity or security problems.

Both ends of the trunk should be configured consistently.

---

# 🔀 Inter-VLAN Routing

Now let's return to:

```text
VLAN 10
192.168.10.0/24
```

and:

```text
VLAN 20
192.168.20.0/24
```

If PC-01 wants to reach SRV-01:

```text
PC-01
192.168.10.10
VLAN 10

       ↓

ROUTING

       ↓

SRV-01
192.168.20.10
VLAN 20
```

We need a Layer 3 device.

Common options include:

- Router
- Layer 3 switch
- Firewall

---

# 🛣️ Router-on-a-Stick

One common learning design is:

> **Router-on-a-Stick**

A router uses one physical interface connected to a switch trunk.

The router creates:

> **Subinterfaces**

for multiple VLANs.

---

# 🗺️ Example

```text
PC-01
VLAN 10
192.168.10.10
   │
   │
   ▼
 SW-01
   │
   │ 802.1Q Trunk
   │
   ▼
 R-01
```

Router subinterfaces:

```text
G0/0.10
192.168.10.1

G0/0.20
192.168.20.1
```

---

# 🧠 Default Gateways

PC-01:

```text
IP:
192.168.10.10

Gateway:
192.168.10.1
```

Server:

```text
IP:
192.168.20.10

Gateway:
192.168.20.1
```

The router provides Layer 3 communication between the two networks.

---

# 🖥️ Router Subinterface Example

Exact interface names vary, but conceptually:

```text
interface gigabitethernet 0/0
no shutdown
```

Then:

```text
interface gigabitethernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
```

Then:

```text
interface gigabitethernet 0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
```

---

# 🧠 What Does `dot1Q 10` Mean?

This:

```text
encapsulation dot1Q 10
```

associates the router subinterface with:

> **VLAN 10**

Likewise:

```text
encapsulation dot1Q 20
```

associates another subinterface with:

> **VLAN 20**

---

# 🚚 Switch Port Toward Router

Because the router must receive traffic for multiple VLANs, the switch interface toward the router is configured as a:

> **Trunk**

Example:

```text
interface gigabitethernet 0/1
switchport mode trunk
```

---

# 🔀 Communication Flow

PC-01 in VLAN 10 wants to reach SRV-01 in VLAN 20.

```text
PC-01
192.168.10.10
   │
   ▼
SW-01
VLAN 10
   │
   ▼
TRUNK
   │
   ▼
R-01
G0/0.10
   │
ROUTING
   │
G0/0.20
   │
   ▼
TRUNK
   │
   ▼
SW-01
VLAN 20
   │
   ▼
SRV-01
192.168.20.10
```

The router performs:

> **Layer 3 routing between VLANs.**

---

# ⚡ Layer 3 Switches

Many business networks don't use router-on-a-stick for all internal VLAN routing.

Instead, a:

> **Layer 3 Switch**

can perform both:

```text
Layer 2 Switching
+
Layer 3 Routing
```

It can create:

> **Switch Virtual Interfaces — SVIs**

Example:

```text
interface vlan 10
ip address 192.168.10.1 255.255.255.0
```

and:

```text
interface vlan 20
ip address 192.168.20.1 255.255.255.0
```

The Layer 3 switch can then route between those networks when routing is enabled and properly configured.

We'll explore routing more deeply in:

> **Lesson 13 — Routing Fundamentals**

---

# 🏢 Practical Small-Business Design

Consider:

```text
VLAN 10 — Employees
192.168.10.0/24

VLAN 20 — Servers
192.168.20.0/24

VLAN 30 — Voice
192.168.30.0/24

VLAN 40 — Guest
192.168.40.0/24

VLAN 50 — Cameras
192.168.50.0/24

VLAN 99 — Management
192.168.99.0/24
```

This makes the network easier to:

- Organize
- Secure
- Document
- Troubleshoot
- Apply policies to

---

# 🔒 Segmentation and Security

VLANs are useful for security design because they create logical separation.

But remember:

> **A VLAN by itself is not a complete security policy.**

If routing is configured between VLANs with no restrictions, devices may still communicate across them.

Security controls can include:

- Firewall rules
- ACLs
- Network access control
- Authentication
- Endpoint security
- Proper switch configuration

Think of VLANs as:

> **Segmentation**

not automatic total isolation.

---

# 🛠️ Troubleshooting Scenario 1

PC-01 and PC-02 should both belong to VLAN 10.

PC-01 works.

PC-02 cannot communicate.

You inspect:

```text
PC-01 → Fa0/1 → VLAN 10

PC-02 → Fa0/2 → VLAN 20
```

Likely problem:

> **PC-02's switch port is assigned to the wrong VLAN.**

---

# 🛠️ Troubleshooting Scenario 2

PCs in VLAN 10 can communicate on SW-01.

PCs in VLAN 10 can communicate on SW-02.

But VLAN 10 devices cannot communicate across the two switches.

Potential problem:

> **The inter-switch trunk isn't carrying VLAN 10.**

Check:

```text
show interfaces trunk
```

---

# 🛠️ Troubleshooting Scenario 3

VLAN 10 works.

VLAN 20 works.

Devices within each VLAN can communicate.

But VLAN 10 cannot reach VLAN 20.

Investigate:

> **Inter-VLAN routing**

including:

- Default gateways
- Router/L3 switch configuration
- Trunk configuration
- Subinterfaces/SVIs
- VLAN IDs
- Routing
- Security policies

---

# 🛠️ Troubleshooting Scenario 4

SW-01 uses native VLAN 99.

SW-02 uses native VLAN 1.

Potential issue:

> **Native VLAN mismatch**

---

# 🛠️ Troubleshooting Scenario 5

A switch has:

```text
VLAN 20
```

configured.

But a PC attached to Fa0/8 is still in VLAN 1.

Creating the VLAN alone isn't enough.

You must also:

> **Assign the appropriate access port to that VLAN.**

---

# 📋 Useful Cisco Commands

| Command | Purpose |
|---|---|
| `show vlan brief` | View VLANs and access-port assignments |
| `vlan 10` | Create/configure VLAN 10 |
| `name EMPLOYEES` | Name a VLAN |
| `switchport mode access` | Configure access mode |
| `switchport access vlan 10` | Assign access VLAN |
| `switchport mode trunk` | Configure trunk |
| `show interfaces trunk` | View trunk information |
| `show mac address-table` | View MACs and VLAN associations |
| `show running-config` | View current configuration |

---

# 🧠 Troubleshooting Workflow

When a VLAN problem occurs:

```text
Physical Link
      ↓
Interface Status
      ↓
Correct VLAN Exists?
      ↓
Correct Access VLAN?
      ↓
MAC Address Learned?
      ↓
Trunk Up?
      ↓
VLAN Allowed on Trunk?
      ↓
Correct IP Subnet?
      ↓
Correct Default Gateway?
      ↓
Inter-VLAN Routing?
      ↓
Security Policy?
```

---

# 📋 VLAN Quick Reference

| Concept | Meaning |
|---|---|
| VLAN | Logical Layer 2 network |
| Access Port | Usually carries one VLAN |
| Trunk Port | Carries multiple VLANs |
| 802.1Q | VLAN tagging standard |
| VLAN ID | Identifies VLAN |
| Native VLAN | Normally untagged VLAN on 802.1Q trunk |
| Inter-VLAN Routing | Routes between VLANs |
| Router-on-a-Stick | Router subinterfaces route multiple VLANs |
| SVI | Layer 3 interface representing a VLAN |
| Broadcast Domain | VLAN creates a separate Layer 2 broadcast domain |

---

# 🧠 Knowledge Check

### 1.

What does VLAN stand for?

### 2.

What does a VLAN create at Layer 2?

### 3.

What type of switch port normally connects to a PC?

### 4.

What type of port commonly connects two switches while carrying multiple VLANs?

### 5.

What standard is commonly used for VLAN tagging?

### 6.

Can a basic Layer 2 switch route between VLANs?

### 7.

What is inter-VLAN routing?

### 8.

What Cisco command shows configured VLANs?

### 9.

What Cisco command shows trunk information?

### 10.

What is router-on-a-stick?

---

# ✅ Answers

1. **Virtual Local Area Network**
2. **A separate logical Layer 2 broadcast domain**
3. **Access port**
4. **Trunk port**
5. **IEEE 802.1Q**
6. **No**
7. **Layer 3 routing between different VLANs**
8. **`show vlan brief`**
9. **`show interfaces trunk`**
10. **Using router subinterfaces over a trunk to route multiple VLANs**

---

# 🎓 Network+ Challenge 1

Which technology allows multiple VLANs to cross one switch-to-switch link?

### A. DNS
### B. DHCP
### C. 802.1Q trunking
### D. ARP

> **Answer: C**

---

# 🎓 Network+ Challenge 2

PC-01 is in VLAN 10.

PC-02 is in VLAN 20.

Both connect to the same Layer 2 switch.

What is required for them to communicate?

> **Layer 3 inter-VLAN routing**

---

# 🎓 Network+ Challenge 3

Which command would you use first to verify that Fa0/5 belongs to VLAN 20?

### A. `show vlan brief`
### B. `nslookup`
### C. `ipconfig`
### D. `show ip route`

> **Answer: A**

---

# 🎓 Network+ Challenge 4

Which port type normally carries multiple VLANs?

> **Trunk**

---

# 🎓 Network+ Challenge 5

Why are VLANs useful?

### A. They increase the number of physical cables.
### B. They create logical network segmentation.
### C. They replace IP addressing.
### D. They eliminate the need for routing.

> **Answer: B**

---

# 🎓 Network+ Challenge 6

A trunk carries VLANs 10 and 20, but VLAN 30 isn't allowed on the trunk.

What happens to VLAN 30 traffic that needs to cross that trunk?

> **It won't be carried across that trunk.**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- VLANs create logical Layer 2 networks.
- Each VLAN represents a separate broadcast domain.
- VLANs improve organization and segmentation.
- VLAN IDs identify VLANs.
- One IP subnet per VLAN is a common design.
- Access ports normally carry one VLAN.
- Trunk ports carry multiple VLANs.
- IEEE 802.1Q provides VLAN tagging.
- Native VLAN traffic is normally untagged on an 802.1Q trunk.
- Both sides of a trunk should use consistent configuration.
- Different VLANs require Layer 3 routing to communicate.
- Router-on-a-stick uses router subinterfaces.
- Layer 3 switches can route using SVIs.
- VLANs help with security but aren't a complete security solution.
- `show vlan brief` and `show interfaces trunk` are critical troubleshooting commands.

---

# 🧪 Next Step — Lab 12

Now you'll build the VLAN environment yourself.

You'll:

```text
Create VLANs
      ↓
Assign Access Ports
      ↓
Test Segmentation
      ↓
Build a Trunk
      ↓
Extend VLANs Across Switches
      ↓
Configure Router-on-a-Stick
      ↓
Route Between VLANs
      ↓
Break It
      ↓
Troubleshoot It
```

➡️ **[Lab 12 — VLANs and Network Segmentation](../labs/lab-12-vlans-network-segmentation.md)**

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ COMPLETE

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES

✅ Lesson 11 — Switching Fundamentals
✅ Lab 11

✅ Lesson 12 — VLANs & Network Segmentation
        ↓
🟡 NEXT: Lab 12

⬜ Lesson 13 — Routing Fundamentals
⬜ Lab 13

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