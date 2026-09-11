# 🧪 Lab 02 — Network Types and Topologies

Welcome to **Lab 02 of Networking Fundamentals**.

In Lesson 02, you learned about different network types and common network topologies.

Now you're going to build your first simulated network using:

> 🌐 **Cisco Packet Tracer**

This lab is intentionally beginner-friendly.

If you've never opened Packet Tracer before, that's completely fine.

By the end of this lab, you'll have built a small LAN, connected multiple computers to a switch, assigned IP addresses, tested communication, and troubleshot your first simulated network problem.

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Open and navigate Cisco Packet Tracer
- Identify the main Packet Tracer workspace
- Add network devices
- Add end devices
- Connect devices using Ethernet
- Build a basic star topology
- Recognize a LAN
- Assign basic IPv4 addresses
- Test connectivity between computers
- Use the Packet Tracer Command Prompt
- Use Simulation Mode
- Observe packets moving through a network
- Identify a single point of failure
- Troubleshoot a basic connection problem
- Save a Packet Tracer project

---

# 🎓 Network+ Focus

This lab reinforces concepts associated with **CompTIA Network+ N10-009**, including:

- LANs
- Network topologies
- Star topology
- Ethernet
- Switches
- Network interfaces
- IPv4 addressing
- Physical connections
- Network diagrams
- Connectivity testing
- Troubleshooting methodology

The goal isn't to memorize Packet Tracer.

Packet Tracer is simply the tool we'll use to **see networking concepts happen**.

---

# 🧰 Tools Used

You'll use:

- 🌐 Cisco Packet Tracer
- 🖥️ Simulated PCs
- 🔀 Simulated Ethernet switch
- 🔌 Ethernet cabling
- 📡 ICMP / Ping

---

# ⏱️ Estimated Time

Approximately:

**30–45 minutes**

If this is your first time using Packet Tracer, take your time exploring the interface.

---

# ⚠️ Before You Begin

You will need **Cisco Packet Tracer** installed.

Packet Tracer is available through Cisco Networking Academy / Cisco Skills for All.

If you haven't installed it yet, use the setup information in:

➡️ **[Cisco Networking Companion](../resources/cisco-companion.md)**

> 💡 Packet Tracer is free with an eligible Cisco account.

Once Packet Tracer is installed, launch it and sign in if prompted.

---

# 🌐 Part 1 — Open Cisco Packet Tracer

Launch:

**Cisco Packet Tracer**

When it opens, you'll see a large blank area.

This is your:

> **Logical Workspace**

Think of this as the area where you'll build your network diagram.

A new project will look mostly empty.

That's about to change.

---

# 🧭 Part 2 — Learn the Interface

Before building anything, look around the Packet Tracer window.

You'll see several important areas.

---

## 🗺️ Logical Workspace

The large central area is where you'll place devices.

Eventually it might contain something like:

```text
PC-01 ─────┐
           │
PC-02 ─── Switch
           │
PC-03 ─────┘
```

---

## 🧰 Device Selection Area

Near the bottom of Packet Tracer you'll find device categories.

Depending on your Packet Tracer version, you'll see categories for things such as:

- Network Devices
- End Devices
- Components
- Connections

We'll only need a few of these today.

---

# 🖥️ Part 3 — Add Your First PC

Find:

**End Devices**

Select it.

Look for the standard:

**PC**

Select the PC and click somewhere in the Logical Workspace.

You should now have something similar to:

```text
PC0
```

Congratulations.

You just placed your first simulated network device.

---

# 🖥️ Part 4 — Add Three PCs

Add two more PCs.

Arrange them roughly like this:

```text
PC0

PC1

PC2
```

Don't worry about exact positioning.

Packet Tracer lets you drag devices around whenever you want.

---

# ✏️ Part 5 — Rename the PCs

Good network diagrams should be understandable.

Rename the computers:

```text
PC0 → PC-01

PC1 → PC-02

PC2 → PC-03
```

Depending on your Packet Tracer version, you can usually click the device and change its display name through the device configuration window.

When finished, you should have:

```text
PC-01

PC-02

PC-03
```

---

# 🔀 Part 6 — Add a Switch

Now we need something to connect the computers.

Find:

**Network Devices**

Then:

**Switches**

Choose a standard Cisco switch such as:

**2960**

Place it near the center of your workspace.

Arrange your network approximately like this:

```text
          PC-01


PC-02     Switch     PC-03
```

Rename the switch:

```text
Switch0 → SW-01
```

---

# 🧠 What Did You Just Add?

The switch will become the central connection point for your computers.

Think back to Lesson 02.

When endpoint devices connect individually to a central device, the topology resembles a:

> ⭐ **Star topology**

We're about to build one.

---

# 🔌 Part 7 — Connect PC-01

Find:

**Connections**

You'll see several cable types.

For this lab, choose:

> **Copper Straight-Through**

Select the cable.

Click:

**PC-01**

Choose:

```text
FastEthernet0
```

Then click:

**SW-01**

Choose an available FastEthernet port such as:

```text
FastEthernet0/1
```

You should now see a cable between the devices.

```text
PC-01 ───── SW-01
```

---

# 🔌 Part 8 — Connect the Other PCs

Connect:

```text
PC-02 FastEthernet0
        ↓
SW-01 FastEthernet0/2
```

Then:

```text
PC-03 FastEthernet0
        ↓
SW-01 FastEthernet0/3
```

Your completed topology should resemble:

```text
             PC-01
               │
               │
PC-02 ─────── SW-01 ─────── PC-03
```

You have now built a:

> **Star topology**

And because these devices are connected within a small local network, you've also created a:

> **LAN — Local Area Network**

---

# 💡 Wait for the Links

You may initially see colored indicators near the switch ports.

Give Packet Tracer a few moments.

The connections should eventually indicate that the links are operational.

If they don't, check:

- Correct cable type
- Correct PC interface
- Correct switch port

---

# 📝 Checkpoint 1

Your network should contain:

```text
3 PCs

1 Switch

3 Ethernet Connections
```

Answer:

### What type of network have you created?

```text
____________________________
```

### What topology does it use?

```text
____________________________
```

### What device is at the center?

```text
____________________________
```

---

# 📍 Part 9 — Configure PC-01

The computers are physically connected, but they still need IP configuration.

Click:

**PC-01**

Open:

**Desktop**

Then select:

**IP Configuration**

Choose:

**Static**

Enter:

```text
IP Address:
192.168.10.10

Subnet Mask:
255.255.255.0
```

Leave the default gateway blank.

Why?

Because this network doesn't have a router yet.

All three PCs will be on the same local network.

---

# 📍 Part 10 — Configure PC-02

Open PC-02's IP Configuration.

Enter:

```text
IP Address:
192.168.10.20

Subnet Mask:
255.255.255.0
```

Leave the default gateway blank.

---

# 📍 Part 11 — Configure PC-03

Configure:

```text
IP Address:
192.168.10.30

Subnet Mask:
255.255.255.0
```

Leave the default gateway blank.

---

# 🗺️ Your Network Now Looks Like This

Conceptually:

```text
              PC-01
          192.168.10.10
                │
                │
                │
PC-02 ──────── SW-01 ──────── PC-03
192.168.10.20                  192.168.10.30
```

All three PCs are configured within the same IPv4 network for this lab.

---

# 🧠 Checkpoint 2

Complete the table:

| Device | IPv4 Address | Subnet Mask |
|---|---|---|
| PC-01 | 192.168.10.10 | 255.255.255.0 |
| PC-02 | 192.168.10.20 | 255.255.255.0 |
| PC-03 | 192.168.10.30 | 255.255.255.0 |

### Do these computers need a router to communicate with each other on this local network?

```text
Yes / No
```

Think about your answer before continuing.

---

# 📡 Part 12 — Your First Packet Tracer Ping

Click:

**PC-01**

Open:

**Desktop → Command Prompt**

Run:

```cmd
ping 192.168.10.20
```

This tests communication from:

```text
PC-01
   ↓
PC-02
```

You should eventually receive successful replies.

> 💡 The first ping may occasionally time out while the simulated devices learn information needed for communication. Try the command again if necessary.

---

# 📝 Record the Result

```text
PC-01 → PC-02

PASS / FAIL
```

---

# 📡 Part 13 — Test PC-03

From PC-01 run:

```cmd
ping 192.168.10.30
```

Record:

```text
PC-01 → PC-03

PASS / FAIL
```

---

# 🔄 Part 14 — Test in the Other Direction

Open the Command Prompt on PC-03.

Run:

```cmd
ping 192.168.10.10
```

Record:

```text
PC-03 → PC-01

PASS / FAIL
```

If everything is configured correctly, all three computers should be able to communicate.

---

# 🧠 What's Actually Happening?

When PC-01 communicates with PC-02:

```text
PC-01
   │
   ▼
 SW-01
   │
   ▼
PC-02
```

The traffic passes through the switch.

The computers aren't directly connected to each other.

The switch provides the central connectivity.

This is one reason the topology is called a:

> **Star**

---

# 🔍 Part 15 — Observe Traffic in Simulation Mode

Packet Tracer has two major operating modes:

```text
Realtime

Simulation
```

So far, you've been working primarily in:

> **Realtime Mode**

Now switch to:

> **Simulation Mode**

Look near the bottom-right portion of Packet Tracer for the Realtime/Simulation controls.

---

# ✉️ Part 16 — Send a Simple PDU

Packet Tracer can create a simple test packet using:

> **Add Simple PDU**

The icon often resembles an envelope.

Select:

**Add Simple PDU**

Then click:

```text
PC-01
```

followed by:

```text
PC-03
```

Packet Tracer creates a simulated ICMP communication.

---

# ▶️ Part 17 — Watch the Packet Move

Use the Simulation controls to advance the event.

Watch what happens.

You should see the packet travel:

```text
PC-01
   ↓
 SW-01
   ↓
PC-03
```

and communication return.

This is one of the most useful features of Packet Tracer.

Instead of networking being invisible, you can actually observe the simulated communication.

---

# 🧠 Question

Did PC-01 send traffic directly to PC-03 without involving the switch?

```text
Yes / No
```

Explain what you observed:

```text
____________________________________________________

____________________________________________________
```

---

# 🔬 Part 18 — Inspect the Packet

While still in Simulation Mode, click one of the packet/event entries.

Packet Tracer may display information about the simulated packet.

You may see references to things such as:

```text
Ethernet

IP

ICMP
```

You don't need to understand all of this yet.

You'll learn these concepts in later lessons.

For now, recognize:

> **Network communication is made up of multiple layers of information.**

This will become much clearer when we study the OSI and TCP/IP models.

---

# 🔁 Part 19 — Return to Realtime Mode

Switch back to:

> **Realtime**

Your network should continue operating normally.

---

# 💥 Part 20 — Break the Network

Networking becomes much easier to understand when you intentionally break something.

We're going to disconnect:

> **PC-03**

Delete or disconnect the cable between:

```text
PC-03
```

and:

```text
SW-01
```

Your topology should now resemble:

```text
             PC-01
               │
               │
PC-02 ─────── SW-01       PC-03
```

PC-03 is isolated.

---

# 🧪 Part 21 — Test the Failure

From PC-01 run:

```cmd
ping 192.168.10.30
```

What happens?

Record:

```text
PC-01 → PC-03

PASS / FAIL
```

It should fail because PC-03 no longer has a physical path to the network.

---

# 🧠 Troubleshooting Question

PC-01 can still ping PC-02.

But PC-01 cannot ping PC-03.

Which is the most likely area to investigate first?

### A.

The entire switch

### B.

PC-03's connection

### C.

Every IP address on the network

### D.

The Internet connection

Answer:

```text
____________________________
```

---

# 🔧 Part 22 — Repair the Network

Reconnect PC-03.

Use:

**Copper Straight-Through**

Connect:

```text
PC-03 FastEthernet0
```

to:

```text
SW-01 FastEthernet0/3
```

Wait for the connection to become operational.

Then test again:

```cmd
ping 192.168.10.30
```

Record:

```text
PC-01 → PC-03

PASS / FAIL
```

You just:

```text
Identified a symptom
        ↓
Investigated the topology
        ↓
Found the failed connection
        ↓
Repaired it
        ↓
Verified connectivity
```

That's basic network troubleshooting.

---

# 💥 Part 23 — Explore the Single Point of Failure

Now think about the topology:

```text
             PC-01
               │
               │
PC-02 ─────── SW-01 ─────── PC-03
```

What happens if:

> **SW-01 fails?**

Every computer depends on the central switch.

That makes SW-01 a potential:

> **Single Point of Failure**

---

# 🧠 Question

If the switch stops working completely, how many of the three computers could continue communicating through this topology?

```text
____________________________
```

Why?

```text
____________________________________________________

____________________________________________________
```

---

# 🕸️ Part 24 — Think About Redundancy

You learned about mesh topology in Lesson 02.

Mesh networks can provide:

> **Multiple possible paths**

Our current network doesn't have that.

```text
PC
 │
 ▼
Switch
```

There is only one path from each PC into the LAN.

Later in the course, you'll learn how network designers introduce redundancy without simply connecting everything to everything.

---

# 🗺️ Part 25 — Create a Network Diagram

Based on what you built, complete this diagram in your notes:

```text
                 __________
                     │
                     │
                     │
__________ ───── __________ ───── __________
```

Fill in:

```text
PC-01

PC-02

PC-03

SW-01
```

Then add each PC's IPv4 address.

Your finished diagram should resemble:

```text
               PC-01
          192.168.10.10
                 │
                 │
                 │
PC-02 ───────── SW-01 ───────── PC-03
192.168.10.20                 192.168.10.30
```

This is your first basic:

> **Network diagram**

---

# ✏️ Part 26 — Add a Note to Packet Tracer

Packet Tracer includes drawing and annotation tools.

If available in your version, add a text note near your topology:

```text
Lab 02
Star Topology
192.168.10.0/24
```

Don't worry about `/24` yet.

You'll learn exactly what that means during IPv4 addressing and subnetting.

For now, it's simply documenting the network you're building.

---

# 💾 Part 27 — Save Your Network

Save your Packet Tracer project.

Use:

**File → Save As**

Suggested filename:

```text
lab-02-star-topology.pkt
```

If you're maintaining a local course folder, you might organize it like:

```text
Networking-Fundamentals
│
└── packet-tracer
    │
    └── lab-02-star-topology.pkt
```

> 💡 `.pkt` is the standard Packet Tracer project file format.

---

# 🏆 Optional Challenge — Add a Fourth Computer

If you're comfortable with the lab so far, add:

```text
PC-04
```

Configure:

```text
IP Address:
192.168.10.40

Subnet Mask:
255.255.255.0
```

Connect it to:

```text
SW-01 FastEthernet0/4
```

Then test:

```cmd
ping 192.168.10.10

ping 192.168.10.20

ping 192.168.10.30
```

All four computers should be able to communicate.

---

# 🏆 Optional Challenge — Create a Second LAN

Want to experiment?

Add:

```text
SW-02

PC-05

PC-06
```

Connect:

```text
PC-05 ─── SW-02

PC-06 ─── SW-02
```

Do **not** connect SW-02 to SW-01 yet.

You now have two physically separate LAN segments.

Think about this question:

> How could we eventually allow devices on different networks to communicate?

You'll learn the answer soon.

One important device will be:

> **A router**

---

# 🧠 Knowledge Check

Try answering these without looking back.

### 1.

What type of network did you build?

### 2.

What topology did you build?

### 3.

Which device was at the center of the topology?

### 4.

What type of cable connected the PCs to the switch?

### 5.

What command did you use to test connectivity?

### 6.

Did the PCs require a router to communicate while they were on the same local IPv4 network?

### 7.

What happened when PC-03's cable was disconnected?

### 8.

Why is SW-01 a potential single point of failure?

### 9.

What Packet Tracer mode allows you to watch simulated packets move?

### 10.

What file extension does Packet Tracer normally use?

---

# ✅ Knowledge Check Answers

### 1.

**LAN — Local Area Network**

### 2.

**Star topology**

### 3.

**SW-01 — the switch**

### 4.

**Copper Straight-Through**

### 5.

```cmd
ping
```

### 6.

**No.**

The PCs were configured on the same local IPv4 network and could communicate through the switch.

### 7.

PC-03 lost its physical network connection and could no longer communicate with the other PCs.

### 8.

All three PCs depend on SW-01 for connectivity. If the switch fails completely, communication through it stops.

### 9.

**Simulation Mode**

### 10.

```text
.pkt
```

---

# 🎓 Network+ Challenge

Consider this network:

```text
PC-A ───┐
        │
PC-B ─ Switch ─ PC-C
        │
PC-D ───┘
```

What topology is shown?

**A. Bus**

**B. Ring**

**C. Star**

**D. Full Mesh**

Answer:

> **C — Star**

---

Now suppose only PC-D loses connectivity while PC-A, PC-B, and PC-C continue working.

Which should you investigate first?

**A. PC-D's network connection**

**B. Replace the switch immediately**

**C. Replace every cable**

**D. Reconfigure the entire network**

Answer:

> **A — PC-D's network connection**

The working devices provide evidence that the shared network infrastructure is at least partially functioning.

---

# 📝 Lab Review

In this lab, you:

- Opened Cisco Packet Tracer
- Learned the basic interface
- Added end devices
- Added a switch
- Connected devices with Ethernet
- Built a star topology
- Created a LAN
- Assigned IPv4 addresses
- Tested connectivity with `ping`
- Used Simulation Mode
- Observed simulated network traffic
- Disconnected a device
- Diagnosed the failure
- Restored connectivity
- Identified a single point of failure
- Created a basic network diagram
- Saved your first Packet Tracer project

---

# 🧠 What You Just Built

Your first Packet Tracer network was simple:

```text
             PC-01
               │
               │
PC-02 ─────── SW-01 ─────── PC-03
```

But this basic design introduces several concepts we'll continue using throughout the course:

```text
Endpoints
    ↓
Network Interfaces
    ↓
Ethernet Connections
    ↓
Switch
    ↓
LAN
    ↓
IP Addressing
    ↓
Connectivity Testing
    ↓
Troubleshooting
```

Later, this small network will grow into networks containing:

```text
Switches
Routers
VLANs
Servers
DHCP
DNS
Wireless Access Points
Firewalls
WAN Connections
VPNs
Cloud Networks
```

You just built the foundation.

---

# 📍 Course Progress

You have now completed:

```text
✅ Lesson 01 — Networking Basics
        ↓
✅ Lab 01 — Networking Basics
        ↓
✅ Lesson 02 — Network Types and Topologies
        ↓
✅ Lab 02 — First Packet Tracer Network
        ↓
🟡 NEXT: Lesson 03 — Network Devices
```

---

# ➡️ Next Lesson

Now that you've used a switch, it's time to understand what networking devices actually do.

Continue to:

➡️ **[Lesson 03 — Network Devices](../lessons/📘%20Lesson%2003%20—%20Network%20Devices.md)**

In Lesson 03, you'll learn about:

- Network interface cards
- Hubs
- Bridges
- Switches
- Layer 3 switches
- Routers
- Wireless access points
- Firewalls
- Modems
- Gateways
- Proxies
- Load balancers
- IDS/IPS

You'll then return to Packet Tracer in **Lab 03** and begin working with more network infrastructure.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Cisco Networking Companion](../resources/cisco-companion.md)**

➡️ **[Return to Main README](../README.md)**