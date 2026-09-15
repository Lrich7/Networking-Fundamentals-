# 🧪 Lab 12 — VLANs and Network Segmentation

Welcome to **Lab 12 of Networking Fundamentals**.

This is one of the most important Packet Tracer labs in the course.

You'll build a network that progresses from:

```text
One Switch
One Network
```

to:

```text
Multiple VLANs
      ↓
Multiple Broadcast Domains
      ↓
802.1Q Trunk
      ↓
Inter-VLAN Routing
```

You'll also intentionally break several VLAN configurations and troubleshoot them.

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Create VLANs
- Name VLANs
- Assign access ports
- Verify VLAN membership
- Explain why VLANs separate devices
- Build VLANs across two switches
- Configure an 802.1Q trunk
- Verify trunk operation
- Configure router-on-a-stick
- Configure router subinterfaces
- Configure default gateways
- Test inter-VLAN routing
- View MAC addresses by VLAN
- Troubleshoot an incorrect access VLAN
- Troubleshoot a trunk problem
- Troubleshoot an incorrect default gateway
- Document a segmented network

---

# 🎓 Network+ Focus

This lab reinforces:

- VLANs
- Network segmentation
- Broadcast domains
- Access ports
- Trunk ports
- IEEE 802.1Q
- VLAN tagging
- Inter-VLAN routing
- Router-on-a-stick
- Default gateways
- Switch troubleshooting

---

# ⏱️ Estimated Time

**90–120 minutes**

This is intentionally a larger lab.

---

# 🧱 PART 1 — BUILD THE INITIAL NETWORK

Open:

> **Cisco Packet Tracer**

Add:

```text
SW-01
PC-01
PC-02
SRV-01
SRV-02
```

Use a Cisco 2960 or similar switch.

Build:

```text
PC-01 ─── Fa0/1
              \
PC-02 ─── Fa0/2 \
                SW-01
SRV-01 ── Fa0/3 /
              /
SRV-02 ── Fa0/4
```

Exact ports may vary.

---

# 📍 PART 2 — ADDRESS THE DEVICES

We'll eventually create:

```text
VLAN 10 — EMPLOYEES
192.168.10.0/24
```

and:

```text
VLAN 20 — SERVERS
192.168.20.0/24
```

Configure:

| Device | VLAN | IPv4 | Mask |
|---|---:|---|---|
| PC-01 | 10 | 192.168.10.10 | 255.255.255.0 |
| PC-02 | 10 | 192.168.10.20 | 255.255.255.0 |
| SRV-01 | 20 | 192.168.20.10 | 255.255.255.0 |
| SRV-02 | 20 | 192.168.20.20 | 255.255.255.0 |

Do not configure gateways yet.

---

# 🖥️ PART 3 — PREPARE THE SWITCH

Open SW-01 CLI.

Enter:

```text
enable
```

Then:

```text
configure terminal
```

Rename:

```text
hostname SW-01
```

Return:

```text
end
```

---

# 🧩 PART 4 — CREATE VLAN 10

Enter:

```text
configure terminal
```

Then:

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

---

# 🧩 PART 5 — CREATE VLAN 20

Enter:

```text
vlan 20
```

Then:

```text
name SERVERS
```

Then:

```text
exit
```

Finish:

```text
end
```

---

# 🔍 PART 6 — VERIFY THE VLANS

Run:

```text
show vlan brief
```

Find:

```text
10   EMPLOYEES

20   SERVERS
```

Record:

```text
VLAN 10 Status:

____________________________


VLAN 20 Status:

____________________________
```

---

# 🔌 PART 7 — ASSIGN EMPLOYEE PORTS

Assuming PC-01 and PC-02 use Fa0/1 and Fa0/2:

```text
configure terminal
```

```text
interface range fastethernet 0/1 - 2
```

```text
switchport mode access
```

```text
switchport access vlan 10
```

Then:

```text
exit
```

---

# 🖥️ PART 8 — ASSIGN SERVER PORTS

Assuming SRV-01 and SRV-02 use Fa0/3 and Fa0/4:

```text
interface range fastethernet 0/3 - 4
```

```text
switchport mode access
```

```text
switchport access vlan 20
```

Then:

```text
end
```

---

# 🔍 PART 9 — VERIFY ACCESS PORTS

Run:

```text
show vlan brief
```

You should see something conceptually like:

```text
10  EMPLOYEES   active   Fa0/1, Fa0/2

20  SERVERS     active   Fa0/3, Fa0/4
```

---

# 🧪 PART 10 — TEST SAME-VLAN COMMUNICATION

From PC-01:

```text
ping 192.168.10.20
```

Expected:

> **Success**

From SRV-01:

```text
ping 192.168.20.20
```

Expected:

> **Success**

---

# 🧪 PART 11 — TEST BETWEEN VLANS

From PC-01:

```text
ping 192.168.20.10
```

Expected:

> **Failure**

Why?

It isn't because VLAN 20 is broken.

It is because:

```text
VLAN 10
        ↓
NO ROUTING YET
        ↓
VLAN 20
```

---

# ⭐ Important Checkpoint

You should now have:

```text
PC-01 ↔ PC-02
✅

SRV-01 ↔ SRV-02
✅

PC-01 ↔ SRV-01
❌
```

This proves:

> **VLAN segmentation is working.**

---

# 📋 PART 12 — VIEW THE MAC TABLE

Generate traffic within both VLANs.

Then run:

```text
show mac address-table
```

Look at the VLAN column.

Record:

| Device | VLAN | MAC | Port |
|---|---:|---|---|
| PC-01 | 10 | | |
| PC-02 | 10 | | |
| SRV-01 | 20 | | |
| SRV-02 | 20 | | |

Notice:

> MAC learning occurs within VLAN context.

---

# 🏗️ PART 13 — ADD A SECOND SWITCH

Add:

```text
SW-02
```

Add:

```text
PC-03
SRV-03
```

Build:

```text
 PC-01                         PC-03
VLAN 10                       VLAN 10
   │                             │
   ▼                             ▼
 SW-01 ======================= SW-02
   ▲                             ▲
   │                             │
SRV-01                         SRV-03
VLAN 20                       VLAN 20
```

The link between switches will become a trunk.

---

# 📍 Configure New Devices

PC-03:

```text
192.168.10.30
255.255.255.0
```

SRV-03:

```text
192.168.20.30
255.255.255.0
```

---

# 🧩 PART 14 — CREATE VLANS ON SW-02

On SW-02:

```text
enable
```

```text
configure terminal
```

```text
hostname SW-02
```

Then:

```text
vlan 10
name EMPLOYEES
exit
```

Then:

```text
vlan 20
name SERVERS
exit
```

---

# 🔌 Assign SW-02 Access Ports

Assume:

```text
PC-03
=
Fa0/1
```

Configure:

```text
interface fastethernet 0/1
switchport mode access
switchport access vlan 10
exit
```

Assume:

```text
SRV-03
=
Fa0/2
```

Configure:

```text
interface fastethernet 0/2
switchport mode access
switchport access vlan 20
exit
```

Then:

```text
end
```

---

# 🚚 PART 15 — CONFIGURE THE TRUNK

Suppose the switches connect using:

```text
SW-01 Gi0/1
      ↕
SW-02 Gi0/1
```

On SW-01:

```text
configure terminal
```

```text
interface gigabitethernet 0/1
```

```text
switchport mode trunk
```

Then:

```text
end
```

On SW-02:

```text
configure terminal
```

```text
interface gigabitethernet 0/1
```

```text
switchport mode trunk
```

Then:

```text
end
```

Use the actual interfaces you connected if yours differ.

---

# 🔍 PART 16 — VERIFY THE TRUNK

On both switches:

```text
show interfaces trunk
```

Record:

```text
SW-01 Trunk Interface:

____________________________


SW-02 Trunk Interface:

____________________________


Native VLAN:

____________________________


Allowed VLANs:

____________________________
```

---

# 🧪 PART 17 — TEST VLAN 10 ACROSS SWITCHES

From PC-01:

```text
ping 192.168.10.30
```

Expected:

> **Success**

Traffic is crossing:

```text
PC-01
VLAN 10
   │
   ▼
SW-01
   │
   │ TRUNK
   ▼
SW-02
   │
   ▼
PC-03
VLAN 10
```

---

# 🧪 PART 18 — TEST VLAN 20 ACROSS SWITCHES

From SRV-01:

```text
ping 192.168.20.30
```

Expected:

> **Success**

The same trunk carries:

```text
VLAN 10
+
VLAN 20
```

---

# 🧠 What Did the Trunk Accomplish?

Without requiring:

```text
Cable for VLAN 10

+

Cable for VLAN 20
```

one physical trunk can carry both.

---

# 🔬 PART 19 — SIMULATION MODE

Switch to:

> **Simulation Mode**

Generate traffic:

```text
PC-01
      ↓
PC-03
```

Inspect the traffic as it crosses:

```text
SW-01
      ↓
TRUNK
      ↓
SW-02
```

Look for VLAN/802.1Q information where Packet Tracer exposes it.

---

# 🏷️ PART 20 — UNDERSTAND THE TAG

Conceptually, when VLAN 10 traffic crosses the trunk:

```text
Ethernet Frame
      +
802.1Q Tag
      ↓
VLAN 10
```

The receiving switch can determine:

> **This frame belongs to VLAN 10.**

---

# 🔀 PART 21 — ADD THE ROUTER

Now add:

```text
R-01
```

Connect it to SW-01.

Topology:

```text
                        R-01
                          │
                          │ 802.1Q Trunk
                          │
                          ▼
 PC-01 ──────────────── SW-01
 VLAN 10                  ║
                          ║ TRUNK
 SRV-01 ────────────────  ║
 VLAN 20                  ║
                          ║
                        SW-02
                        /    \
                       /      \
                  PC-03      SRV-03
                  VLAN 10    VLAN 20
```

---

# 🚚 PART 22 — CONFIGURE THE ROUTER TRUNK

Assume R-01 connects:

```text
G0/0
```

to SW-01:

```text
Gi0/2
```

Your interfaces may differ.

On SW-01:

```text
configure terminal
```

```text
interface gigabitethernet 0/2
```

```text
switchport mode trunk
```

Then:

```text
end
```

---

# 🖥️ PART 23 — CONFIGURE ROUTER-ON-A-STICK

On R-01:

```text
enable
```

Then:

```text
configure terminal
```

Enable the physical interface:

```text
interface gigabitethernet 0/0
```

```text
no shutdown
```

Then:

```text
exit
```

---

# VLAN 10 Subinterface

Enter:

```text
interface gigabitethernet 0/0.10
```

Then:

```text
encapsulation dot1Q 10
```

Then:

```text
ip address 192.168.10.1 255.255.255.0
```

Then:

```text
exit
```

---

# VLAN 20 Subinterface

Enter:

```text
interface gigabitethernet 0/0.20
```

Then:

```text
encapsulation dot1Q 20
```

Then:

```text
ip address 192.168.20.1 255.255.255.0
```

Then:

```text
end
```

---

# 📋 Router Configuration

You now have:

| Interface | VLAN | IP |
|---|---:|---|
| G0/0.10 | 10 | 192.168.10.1/24 |
| G0/0.20 | 20 | 192.168.20.1/24 |

These become the:

> **Default gateways**

for their respective VLANs.

---

# 🚪 PART 24 — CONFIGURE DEFAULT GATEWAYS

Set:

### VLAN 10 Devices

```text
Default Gateway:
192.168.10.1
```

This includes:

```text
PC-01
PC-02
PC-03
```

### VLAN 20 Devices

```text
Default Gateway:
192.168.20.1
```

This includes:

```text
SRV-01
SRV-02
SRV-03
```

---

# 🧪 PART 25 — TEST THE GATEWAYS

From PC-01:

```text
ping 192.168.10.1
```

Expected:

> **Success**

From SRV-01:

```text
ping 192.168.20.1
```

Expected:

> **Success**

---

# 🌐 PART 26 — TEST INTER-VLAN ROUTING

Now from PC-01:

```text
ping 192.168.20.10
```

Expected:

> **Success**

Before the router:

```text
VLAN 10 → VLAN 20
❌
```

After routing:

```text
VLAN 10
   ↓
R-01
   ↓
VLAN 20
✅
```

---

# ⭐ Major Checkpoint

You have now built:

> **Inter-VLAN Routing**

PC-01 and SRV-01 are:

```text
Different VLANs
+
Different IP Subnets
```

but communicate through:

> **R-01**

---

# 🛣️ PART 27 — TRACE THE PATH

From PC-01:

```text
tracert 192.168.20.10
```

Observe the Layer 3 path.

The important device is:

```text
192.168.10.1
```

which is PC-01's default gateway.

---

# 🔬 PART 28 — SIMULATE INTER-VLAN TRAFFIC

Use Packet Tracer Simulation Mode.

Send traffic:

```text
PC-01
192.168.10.10
VLAN 10
```

to:

```text
SRV-01
192.168.20.10
VLAN 20
```

Follow:

```text
PC-01
   ↓
SW-01
   ↓
R-01
   ↓
SW-01
   ↓
SRV-01
```

Identify where:

> **Layer 3 routing occurs**

Answer:

```text
R-01
```

---

# 💥 PART 29 — TROUBLESHOOTING CHALLENGE 1

Move PC-02's switch port from:

```text
VLAN 10
```

to:

```text
VLAN 20
```

without changing its IP address.

PC-02 still has:

```text
192.168.10.20/24
```

Now test:

```text
PC-02 → PC-01
```

What happens?

```text
____________________________________
```

---

# 🔍 Diagnose It

Use:

```text
show vlan brief
```

Find PC-02's port.

What is wrong?

> **The physical switch port belongs to the wrong VLAN.**

---

# 🔧 Repair

Return the port to:

```text
VLAN 10
```

Retest.

---

# 💥 PART 30 — TROUBLESHOOTING CHALLENGE 2

On SW-02, change the inter-switch port from:

```text
switchport mode trunk
```

to:

```text
switchport mode access
```

Now test:

```text
PC-01 → PC-03
```

and:

```text
SRV-01 → SRV-03
```

Investigate with:

```text
show interfaces trunk
```

---

# 🧠 Root Cause

The switch-to-switch connection is no longer operating as the intended:

> **802.1Q trunk**

Repair it:

```text
switchport mode trunk
```

Retest.

---

# 💥 PART 31 — TROUBLESHOOTING CHALLENGE 3

Change PC-01's gateway from:

```text
192.168.10.1
```

to:

```text
192.168.10.254
```

Test:

```text
PC-01 → PC-02
```

Then:

```text
PC-01 → SRV-01
```

---

# 🧠 Expected Pattern

Same VLAN:

```text
PC-01 → PC-02
✅
```

Different VLAN:

```text
PC-01 → SRV-01
❌
```

Why?

Local traffic doesn't require the gateway.

Remote-subnet traffic does.

---

# 🔧 Repair

Restore:

```text
192.168.10.1
```

---

# 💥 PART 32 — TROUBLESHOOTING CHALLENGE 4

Assume VLAN 20 traffic stops crossing between switches while VLAN 10 still works.

What should you investigate?

Think:

```text
Does VLAN 20 exist on both switches?
        ↓
Are server ports assigned correctly?
        ↓
Is the trunk active?
        ↓
Is VLAN 20 allowed on the trunk?
        ↓
Are MAC addresses being learned?
```

This is an example of:

> **Troubleshooting by scope**

If VLAN 10 crosses the trunk successfully, the entire trunk isn't necessarily dead.

---

# 📋 PART 33 — DOCUMENT THE NETWORK

Create a final VLAN table.

| VLAN | Name | Subnet | Gateway |
|---:|---|---|---|
| 10 | EMPLOYEES | 192.168.10.0/24 | 192.168.10.1 |
| 20 | SERVERS | 192.168.20.0/24 | 192.168.20.1 |

---

# 📋 Document Access Ports

### SW-01

| Port | Device | Mode | VLAN |
|---|---|---|---|
| | | | |
| | | | |
| | | | |
| | | | |

### SW-02

| Port | Device | Mode | VLAN |
|---|---|---|---|
| | | | |
| | | | |

---

# 📋 Document Trunks

| Device | Interface | Connected To | Mode |
|---|---|---|---|
| SW-01 | | SW-02 | Trunk |
| SW-02 | | SW-01 | Trunk |
| SW-01 | | R-01 | Trunk |

---

# 🧠 Knowledge Check

### 1.

What does a VLAN create?

### 2.

What type of port normally connects a PC?

### 3.

What type of port carries multiple VLANs?

### 4.

What standard provides VLAN tagging?

### 5.

What command shows VLAN membership?

### 6.

What command shows trunks?

### 7.

Can VLAN 10 communicate directly with VLAN 20 using only Layer 2 switching?

### 8.

What provides communication between VLANs in this lab?

### 9.

What is the VLAN 10 gateway?

### 10.

What is the VLAN 20 gateway?

---

# ✅ Answers

1. **A separate logical Layer 2 broadcast domain**
2. **Access port**
3. **Trunk port**
4. **IEEE 802.1Q**
5. **`show vlan brief`**
6. **`show interfaces trunk`**
7. **No**
8. **R-01 using router-on-a-stick**
9. **192.168.10.1**
10. **192.168.20.1**

---

# 🎓 Network+ Challenge 1

PC-01 and PC-02 have correct addresses in:

```text
192.168.10.0/24
```

but cannot communicate.

PC-01's port is VLAN 10.

PC-02's port is VLAN 20.

What is the likely problem?

> **VLAN mismatch / incorrect access VLAN**

---

# 🎓 Network+ Challenge 2

Which technology allows VLANs 10, 20, and 30 to share one switch-to-switch connection?

> **802.1Q trunking**

---

# 🎓 Network+ Challenge 3

VLAN 10 hosts can communicate with each other.

VLAN 20 hosts can communicate with each other.

VLAN 10 cannot reach VLAN 20.

What functionality is missing?

> **Inter-VLAN routing**

---

# 🎓 Network+ Challenge 4

Which device performs the Layer 3 decision in the router-on-a-stick topology?

> **The router**

---

# 🎓 Network+ Challenge 5

PC-01 can reach PC-02 in VLAN 10 but cannot reach a server in VLAN 20 after its gateway is incorrectly configured.

Why?

> Local same-subnet traffic doesn't require the default gateway, but traffic to another subnet does.

---

# 📋 Lab Review

In this lab, you:

- Created VLAN 10
- Created VLAN 20
- Named VLANs
- Assigned access ports
- Verified VLAN membership
- Tested same-VLAN communication
- Proved different VLANs were separated
- Viewed MAC addresses by VLAN
- Added a second switch
- Extended VLANs across switches
- Configured an 802.1Q trunk
- Verified trunk operation
- Observed VLAN tagging
- Added a router
- Configured router-on-a-stick
- Created router subinterfaces
- Configured default gateways
- Tested inter-VLAN routing
- Used Simulation Mode
- Troubleshot a wrong access VLAN
- Troubleshot a broken trunk
- Troubleshot an incorrect gateway
- Documented VLANs and switch ports

---

# 💾 Save Your Packet Tracer Lab

Save as:

```text
lab-12-vlans-network-segmentation.pkt
```

You don't need to upload the completed `.pkt` file to the public repository.

Building and troubleshooting the topology is part of the exercise.

---

# 🏆 Lab Complete

You've now moved from:

```text
ONE SWITCH
ONE BROADCAST DOMAIN
```

to:

```text
PHYSICAL SWITCHING INFRASTRUCTURE

        ↓

VLAN 10 — EMPLOYEES
192.168.10.0/24

        +

VLAN 20 — SERVERS
192.168.20.0/24

        ↓

802.1Q TRUNKS

        ↓

INTER-VLAN ROUTING
```

This is much closer to how real business networks are designed.

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
✅ Lab 12

        ↓

🟡 NEXT:
Lesson 13 — Routing Fundamentals

⬜ Lab 13 — Routing Fundamentals

        ↓

⬜ Lesson 14 — DHCP
⬜ Lab 14

⬜ Lesson 15 — DNS
⬜ Lab 15

⬜ Lesson 16 — NAT & Address Translation
⬜ Lab 16

        ↓

🏗️ Project 03
Build a Routed Small-Business Network
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 13 — Routing Fundamentals**

You already used routing in this lab.

Next we'll slow down and understand exactly how a router decides:

```text
Where does this packet need to go?
        ↓
Is the network directly connected?
        ↓
Is there a matching route?
        ↓
Which route is most specific?
        ↓
What is the next hop?
        ↓
Which interface should I use?
```

We'll cover:

- Routing tables
- Directly connected routes
- Static routes
- Default routes
- Next-hop addresses
- Exit interfaces
- Longest-prefix match
- Route selection
- `show ip route`
- `route print`
- `Get-NetRoute`
- Multi-router Packet Tracer networks
- Routing troubleshooting

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**
