# 🧪 Lab 03 — Network Devices

Welcome to **Lab 03 of Networking Fundamentals**.

In Lesson 03, you learned about the devices that make networks work.

You learned the roles of:

- Network interface cards
- Switches
- Routers
- Wireless access points
- Firewalls
- Modems
- Gateways
- Layer 3 switches
- Proxies
- Load balancers
- IDS/IPS
- VPN concentrators

Now you'll return to **Cisco Packet Tracer** and build a larger network containing several of these device types.

Unlike Lab 02, this lab assumes you already know the basics of Packet Tracer.

This time, the focus is:

> **What does each device do, and where does it belong?**

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Identify common network devices in Packet Tracer
- Add PCs and servers
- Add switches
- Add a router
- Add a wireless access point
- Identify Ethernet network interfaces
- Connect devices using appropriate cabling
- Build a small-business network topology
- Configure basic IPv4 addresses
- Understand the role of a default gateway
- Test local connectivity
- Test communication through a router
- Identify the path traffic takes
- Recognize shared network dependencies
- Troubleshoot basic device and connection failures
- Document a basic network topology

---

# 🎓 Network+ Focus

This lab reinforces concepts associated with **CompTIA Network+ N10-009**, including:

- Network interface cards
- Layer 2 switches
- Routers
- Wireless access points
- Servers
- Ethernet
- IPv4
- Default gateways
- Physical topology
- Network diagrams
- Device roles
- Connectivity testing
- Troubleshooting

When working through the lab, don't focus only on making the network work.

Ask:

> **Why is this device here?**

and:

> **What would stop working if this device failed?**

---

# 🧰 Tools Used

You'll use:

- 🌐 Cisco Packet Tracer
- 🖥️ PCs
- 🗄️ Server
- 🔀 Ethernet switches
- 🚦 Router
- 📡 Wireless access point
- 💻 Wireless laptop
- 🔌 Ethernet connections
- 📡 ICMP / Ping
- 🔍 Simulation Mode

---

# ⏱️ Estimated Time

Approximately:

**45–60 minutes**

Take your time.

Understanding the network is more important than completing it quickly.

---

# 🗺️ What You're Going to Build

Your network will eventually resemble:

```text
                         R-01
                        ROUTER
                       /      \
                      /        \
                   SW-01      SW-02
                 OFFICE       SERVER
                /  |  \          |
               /   |   \         |
          PC-01  PC-02 AP-01   SRV-01
                        )))
                         |
                      LAPTOP-01
```

This is more complicated than Lab 02, but we'll build it one piece at a time.

---

# 🧠 What's Different From Lab 02?

In Lab 02, you built:

```text
PC ─── Switch ─── PC
```

All devices were on one local network.

This time we're introducing:

> **A router**

The router will connect **two different IPv4 networks**.

We'll use:

```text
Office LAN
192.168.10.0/24
```

and:

```text
Server LAN
192.168.20.0/24
```

Don't worry if `/24` isn't completely familiar yet.

You'll study IPv4 addressing and subnetting in depth later.

For now, focus on the device relationships.

---

# 🌐 Part 1 — Open Packet Tracer

Launch:

**Cisco Packet Tracer**

Create a new project.

You should begin with an empty Logical Workspace.

---

# 🖥️ Part 2 — Add Two Office PCs

From:

**End Devices**

add two standard PCs.

Rename them:

```text
PC-01
PC-02
```

Place them toward the left side of the workspace.

---

# 🔀 Part 3 — Add the Office Switch

From:

**Network Devices → Switches**

add a:

**2960 Switch**

Rename it:

```text
SW-01
```

Arrange:

```text
PC-01 ──┐
        │
       SW-01
        │
PC-02 ──┘
```

---

# 🔌 Part 4 — Connect the Office PCs

Use:

> **Copper Straight-Through**

Connect:

```text
PC-01 FastEthernet0
        ↓
SW-01 FastEthernet0/1
```

Then:

```text
PC-02 FastEthernet0
        ↓
SW-01 FastEthernet0/2
```

Wait for the links to become operational.

---

# 🚦 Part 5 — Add the Router

From:

**Network Devices → Routers**

choose a router with at least two usable Ethernet interfaces.

A model such as a **1941** may be used if available in your Packet Tracer version.

Rename it:

```text
R-01
```

Place it above or to the right of SW-01.

Your topology should now resemble:

```text
PC-01 ──┐
        │
       SW-01 ───── R-01
        │
PC-02 ──┘
```

---

# 🔌 Part 6 — Connect SW-01 to R-01

Use:

> **Copper Straight-Through**

Connect an available switch port such as:

```text
SW-01 GigabitEthernet0/1
```

to an Ethernet interface on R-01 such as:

```text
R-01 GigabitEthernet0/0
```

Your exact interface names may differ slightly depending on the router model.

That's okay.

The important relationship is:

```text
Office Devices
      ↓
    SW-01
      ↓
     R-01
```

---

# 🧠 Device Checkpoint 1

Answer:

### What is SW-01 primarily doing?

```text
____________________________________
```

### What is R-01 primarily going to do?

```text
____________________________________
```

### Which device primarily uses MAC addresses to forward Ethernet frames inside the LAN?

```text
____________________________________
```

### Which device will connect different IP networks?

```text
____________________________________
```

---

# 🗄️ Part 7 — Add the Server Network

Add another:

**2960 Switch**

Rename it:

```text
SW-02
```

Then add:

**Server**

from End Devices.

Rename the server:

```text
SRV-01
```

Arrange:

```text
R-01 ───── SW-02 ───── SRV-01
```

---

# 🔌 Part 8 — Connect the Server Network

Use Copper Straight-Through.

Connect an available second Ethernet interface on R-01 to SW-02.

For example:

```text
R-01 GigabitEthernet0/1
        ↓
SW-02 GigabitEthernet0/1
```

Then connect:

```text
SRV-01 FastEthernet0
        ↓
SW-02 FastEthernet0/1
```

Your network should now resemble:

```text
PC-01 ──┐
        │
       SW-01
        │
PC-02 ──┘
        │
        │
       R-01
        │
        │
       SW-02
        │
        │
      SRV-01
```

---

# 🧠 Stop and Think

You now have:

```text
Office LAN
    │
    ▼
  Router
    │
    ▼
Server LAN
```

Which device connects the two networks?

> **R-01**

This is one of the most important distinctions from Lesson 03:

```text
Switch
=
Connect devices inside a LAN
```

```text
Router
=
Connect different IP networks
```

---

# 📍 Part 9 — Configure the Router

Click:

**R-01**

Open the router's configuration options.

Depending on your Packet Tracer version, you may use the **Config** tab.

Configure the interface connected to SW-01.

Use:

```text
IP Address:
192.168.10.1

Subnet Mask:
255.255.255.0
```

Make sure the interface is:

> **On**

---

Configure the interface connected to SW-02.

Use:

```text
IP Address:
192.168.20.1

Subnet Mask:
255.255.255.0
```

Make sure this interface is also:

> **On**

---

# 🗺️ Router Configuration

R-01 now connects:

```text
192.168.10.0/24
       │
       ▼
192.168.10.1
     R-01
192.168.20.1
       │
       ▼
192.168.20.0/24
```

The router has an address in both networks.

That allows it to act as the path between them.

---

# 🖥️ Part 10 — Configure PC-01

Open:

**PC-01 → Desktop → IP Configuration**

Configure:

```text
IP Address:
192.168.10.10

Subnet Mask:
255.255.255.0

Default Gateway:
192.168.10.1
```

---

# 🖥️ Part 11 — Configure PC-02

Configure:

```text
IP Address:
192.168.10.20

Subnet Mask:
255.255.255.0

Default Gateway:
192.168.10.1
```

---

# 🗄️ Part 12 — Configure SRV-01

Configure:

```text
IP Address:
192.168.20.10

Subnet Mask:
255.255.255.0

Default Gateway:
192.168.20.1
```

---

# 📋 Addressing Table

Your network should now use:

| Device | IPv4 Address | Subnet Mask | Default Gateway |
|---|---|---|---|
| PC-01 | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| PC-02 | 192.168.10.20 | 255.255.255.0 | 192.168.10.1 |
| R-01 Office | 192.168.10.1 | 255.255.255.0 | — |
| R-01 Server | 192.168.20.1 | 255.255.255.0 | — |
| SRV-01 | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 |

---

# 🧠 Why Do We Need Default Gateways Now?

In Lab 02, all PCs were on the same network.

They didn't need a router to communicate with each other.

Now PC-01 is:

```text
192.168.10.10
```

while SRV-01 is:

```text
192.168.20.10
```

These belong to different IPv4 networks in this lab.

PC-01 therefore sends traffic destined for the other network toward:

```text
192.168.10.1
```

which is:

> **R-01**

That's PC-01's:

> **Default Gateway**

---

# 📡 Part 13 — Test Local Communication

Open:

**PC-01 → Desktop → Command Prompt**

Run:

```cmd
ping 192.168.10.20
```

This tests:

```text
PC-01
   ↓
 SW-01
   ↓
PC-02
```

Record:

```text
PC-01 → PC-02

PASS / FAIL
```

---

# 🚦 Part 14 — Test the Default Gateway

From PC-01 run:

```cmd
ping 192.168.10.1
```

Record:

```text
PC-01 → R-01

PASS / FAIL
```

If successful, PC-01 can reach its router interface.

---

# 🌐 Part 15 — Test Communication Across Networks

Now run:

```cmd
ping 192.168.20.10
```

This tests communication from:

```text
PC-01
   │
   ▼
 SW-01
   │
   ▼
 R-01
   │
   ▼
 SW-02
   │
   ▼
SRV-01
```

Record:

```text
PC-01 → SRV-01

PASS / FAIL
```

> 💡 The first ping may time out while simulated devices learn necessary network information. Try it again if necessary.

---

# 🎉 What Just Happened?

If the ping succeeded, you just sent traffic between:

```text
192.168.10.0/24
```

and:

```text
192.168.20.0/24
```

using a router.

This is your first:

> **Routed network**

You haven't studied routing in depth yet.

That's okay.

The goal here is simply to understand:

```text
Same Network
     ↓
Switch

Different Network
     ↓
Router
```

---

# 📡 Part 16 — Add Wireless Networking

Now let's add wireless connectivity.

From Packet Tracer's wireless/network device options, add a basic:

> **Wireless Access Point**

Rename it:

```text
AP-01
```

Connect AP-01 to SW-01 using an Ethernet connection.

Your office LAN should begin to resemble:

```text
              R-01
                │
                │
              SW-01
          ┌─────┼─────┐
          │     │     │
        PC-01 PC-02 AP-01
                    )))
```

---

# 💻 Part 17 — Add a Wireless Laptop

Add a laptop from:

**End Devices**

Rename it:

```text
LAPTOP-01
```

Place it near AP-01.

Depending on the Packet Tracer laptop model, you may need to ensure it has a compatible wireless network module/interface.

If necessary:

1. Open the laptop.
2. Use the **Physical** tab.
3. Power the laptop off.
4. Install a compatible wireless interface if one isn't already present.
5. Power the laptop back on.

Packet Tracer versions and device models can vary, so don't worry if the exact interface looks slightly different.

---

# 📡 Part 18 — Configure the Wireless Network

Configure AP-01 with an SSID such as:

```text
TrainingWiFi
```

For this introductory lab, the primary goal is establishing wireless connectivity.

We'll study wireless security and proper Wi-Fi configuration later in:

> **Lesson 18 — Wireless Networking**

Connect LAPTOP-01 to:

```text
TrainingWiFi
```

---

# 📍 Part 19 — Configure LAPTOP-01

Configure the laptop with:

```text
IP Address:
192.168.10.30

Subnet Mask:
255.255.255.0

Default Gateway:
192.168.10.1
```

The laptop is part of the:

> **Office LAN**

even though it uses wireless connectivity.

---

# 🗺️ Your Expanded Network

Your topology should now resemble:

```text
                         R-01
                        /    \
                       /      \
                    SW-01     SW-02
                ┌─────┼────┐    │
                │     │    │    │
             PC-01 PC-02 AP-01 SRV-01
                           )))
                            │
                        LAPTOP-01
```

---

# 🧠 Device Checkpoint 2

### Which device provides wireless access?

```text
____________________________________
```

### Which device connects the wired office devices?

```text
____________________________________
```

### Which device connects the Office LAN and Server LAN?

```text
____________________________________
```

### Which device provides the server resource?

```text
____________________________________
```

---

# 📡 Part 20 — Test Wireless Communication

From LAPTOP-01, open the Command Prompt.

Run:

```cmd
ping 192.168.10.10
```

This tests connectivity to PC-01.

Then run:

```cmd
ping 192.168.20.10
```

This tests connectivity to SRV-01 across the router.

Record:

```text
LAPTOP-01 → PC-01

PASS / FAIL
```

```text
LAPTOP-01 → SRV-01

PASS / FAIL
```

---

# 🧭 Part 21 — Follow the Traffic Path

Think about the second ping.

Traffic from LAPTOP-01 to SRV-01 follows a path similar to:

```text
LAPTOP-01
    )))
   AP-01
     │
     ▼
   SW-01
     │
     ▼
    R-01
     │
     ▼
   SW-02
     │
     ▼
  SRV-01
```

Each device performs a different job.

### LAPTOP-01

Creates the traffic.

### AP-01

Provides wireless access to the wired LAN.

### SW-01

Connects devices within the Office LAN.

### R-01

Routes traffic between IP networks.

### SW-02

Connects devices within the Server LAN.

### SRV-01

Receives the traffic.

---

# 🔍 Part 22 — Use Simulation Mode

Switch Packet Tracer to:

> **Simulation Mode**

Create a Simple PDU from:

```text
PC-01
```

to:

```text
SRV-01
```

Advance the simulation one event at a time.

Watch the path.

You should see communication move through devices such as:

```text
PC-01
  ↓
SW-01
  ↓
R-01
  ↓
SW-02
  ↓
SRV-01
```

---

# 🧠 Observation

Which device did the traffic use to move from the Office LAN to the Server LAN?

```text
____________________________________
```

Why was that device required?

```text
____________________________________________________

____________________________________________________
```

---

# 🔬 Part 23 — Look at the Interfaces

Click:

**R-01**

Examine its interfaces.

Notice that the router has multiple network interfaces.

Conceptually:

```text
          R-01
        /      \
       /        \
192.168.10.1   192.168.20.1
     │              │
Office LAN       Server LAN
```

A router needs connectivity to the networks it routes between.

---

# 🧠 NIC Connection

Remember the NIC from Lesson 03?

Every endpoint needs a network interface.

For example:

```text
PC-01
  │
FastEthernet0
  │
  ▼
SW-01
```

and:

```text
LAPTOP-01
    │
Wireless NIC
    )))
  AP-01
```

Different technologies.

Same fundamental requirement:

> **The device needs a network interface.**

---

# 💥 Part 24 — Troubleshooting Challenge 1

Time to break something.

Disconnect the Ethernet cable between:

```text
PC-02
```

and:

```text
SW-01
```

Now test from PC-02:

```cmd
ping 192.168.10.10
```

Record:

```text
PC-02 → PC-01

PASS / FAIL
```

---

# 🧠 Analyze the Problem

PC-01 still works.

LAPTOP-01 still works.

SRV-01 still works.

Only PC-02 has failed.

Which area should you investigate first?

### A.

R-01

### B.

SW-02

### C.

PC-02's network connection

### D.

SRV-01

Answer:

```text
____________________________
```

Reconnect PC-02 before continuing.

---

# 💥 Part 25 — Troubleshooting Challenge 2

Now disconnect:

```text
SW-02
```

from:

```text
R-01
```

Test from PC-01:

```cmd
ping 192.168.10.20
```

Then:

```cmd
ping 192.168.20.10
```

Record:

```text
PC-01 → PC-02

PASS / FAIL
```

```text
PC-01 → SRV-01

PASS / FAIL
```

---

# 🧠 What Does This Tell You?

If PC-01 can still reach PC-02:

> **The Office LAN is working.**

If PC-01 cannot reach SRV-01:

> **The path toward the Server LAN is broken.**

This is a very important troubleshooting technique.

Don't only ask:

> "Does the network work?"

Ask:

> **"How far can I communicate?"**

---

# 🛠️ Part 26 — Repair the Connection

Reconnect SW-02 to R-01.

Wait for the connection to become operational.

Then test:

```cmd
ping 192.168.20.10
```

Verify:

```text
PC-01 → SRV-01

PASS
```

---

# 💥 Part 27 — Troubleshooting Challenge 3

Now simulate a problem with the wireless portion of the network.

Disconnect AP-01 from SW-01 or temporarily disable its connection.

Think about the result.

Which devices should still work?

```text
PC-01

PC-02

SRV-01
```

Which device loses its path through AP-01?

```text
LAPTOP-01
```

---

# 🧠 Shared Dependencies

This introduces an important troubleshooting idea:

> **Look for what the affected devices have in common.**

For example:

```text
Only PC-02 fails
       ↓
Check PC-02-specific components
```

```text
Only wireless clients fail
       ↓
Check wireless infrastructure
```

```text
Entire Server LAN fails
       ↓
Check shared Server LAN components
```

```text
Everything loses remote connectivity
       ↓
Check shared routing/upstream infrastructure
```

---

# 🧪 Part 28 — Device Failure Challenge

Consider this topology:

```text
PC-01 ──┐
        │
PC-02 ─ SW-01 ─ R-01 ─ SW-02 ─ SRV-01
        │
       AP-01
        )))
     LAPTOP-01
```

Match each failure with the most likely impact.

---

### SW-01 Completely Fails

Likely affected:

```text
____________________________________
```

---

### SW-02 Completely Fails

Likely affected:

```text
____________________________________
```

---

### AP-01 Fails

Likely affected:

```text
____________________________________
```

---

### R-01 Fails

Likely affected:

```text
____________________________________
```

---

# ✅ Suggested Answers

### SW-01 Completely Fails

Office devices connected through SW-01 lose connectivity through that switch.

### SW-02 Completely Fails

SRV-01 loses connectivity through the Server LAN switch.

### AP-01 Fails

Wireless connectivity through AP-01 is lost.

### R-01 Fails

Communication between the two IP networks fails.

Devices within the same functioning local LAN may still be able to communicate with each other.

---

# 🗺️ Part 29 — Document the Network

Create a simple diagram in your notes.

Include:

```text
R-01

SW-01

SW-02

PC-01

PC-02

LAPTOP-01

AP-01

SRV-01
```

Add IPv4 addresses where appropriate.

Your logical diagram should resemble:

```text
                         R-01
              192.168.10.1 | 192.168.20.1
                     /             \
                    /               \
                 SW-01             SW-02
               OFFICE LAN        SERVER LAN
              192.168.10.x       192.168.20.x
              /    |    \              |
             /     |     \             |
         PC-01   PC-02   AP-01       SRV-01
        .10      .20       )))        .10
                           |
                       LAPTOP-01
                           .30
```

---

# 📝 Part 30 — Add Packet Tracer Labels

Use Packet Tracer's annotation tools to label the network.

Suggested labels:

```text
OFFICE LAN
192.168.10.0/24
```

and:

```text
SERVER LAN
192.168.20.0/24
```

You can also label:

```text
R-01
SW-01
SW-02
AP-01
```

Good documentation makes troubleshooting easier.

---

# 💾 Part 31 — Save Your Packet Tracer File

Save your project as:

```text
lab-03-network-devices.pkt
```

Your repository now has a logical location for Packet Tracer files:

```text
Networking-Fundamentals-/
│
├── labs/
│   └── lab-03-network-devices.md
│
└── packet-tracer/
    └── lab-03-network-devices.pkt
```

> 💡 The `.md` file contains the instructions. The `.pkt` file contains the actual Packet Tracer network.

---

# 🏆 Optional Challenge — Add Another Server

Add:

```text
SRV-02
```

Connect it to:

```text
SW-02
```

Configure:

```text
IP Address:
192.168.20.20

Subnet Mask:
255.255.255.0

Default Gateway:
192.168.20.1
```

Then test from PC-01:

```cmd
ping 192.168.20.20
```

Think about this question:

> Did adding another server require adding another router?

Why or why not?

---

# 🏆 Optional Challenge — Add Another Office PC

Add:

```text
PC-03
```

Configure:

```text
IP Address:
192.168.10.40

Subnet Mask:
255.255.255.0

Default Gateway:
192.168.10.1
```

Connect it to SW-01.

Test communication with:

```text
PC-01
PC-02
SRV-01
```

---

# 🏆 Optional Challenge — Identify Device Roles

Without looking back at Lesson 03, describe each device in one sentence.

### SW-01

```text
____________________________________________________
```

### R-01

```text
____________________________________________________
```

### AP-01

```text
____________________________________________________
```

### SRV-01

```text
____________________________________________________
```

### SW-02

```text
____________________________________________________
```

---

# 🧠 Knowledge Check

### 1.

Which device connects PC-01 and PC-02 inside the Office LAN?

### 2.

Which device connects the Office LAN to the Server LAN?

### 3.

Which device provides wireless connectivity?

### 4.

What is PC-01's default gateway?

### 5.

What is SRV-01's default gateway?

### 6.

Why doesn't PC-01 need the router when communicating with PC-02?

### 7.

Why does PC-01 need the router when communicating with SRV-01?

### 8.

What network interface does the wired PC use?

### 9.

What happens to LAPTOP-01 if AP-01 fails?

### 10.

What troubleshooting information can you gain by successfully pinging PC-02 but failing to ping SRV-01?

---

# ✅ Knowledge Check Answers

### 1.

**SW-01**

### 2.

**R-01**

### 3.

**AP-01**

### 4.

```text
192.168.10.1
```

### 5.

```text
192.168.20.1
```

### 6.

PC-01 and PC-02 are on the same local IPv4 network, so they can communicate through the switch without routing through R-01.

### 7.

SRV-01 is on a different IPv4 network, so PC-01 sends the traffic toward its default gateway for routing.

### 8.

An Ethernet network interface such as FastEthernet0.

### 9.

The laptop loses wireless connectivity through that access point.

### 10.

It suggests that the local Office LAN is functioning and that the problem may exist farther along the path toward the Server LAN.

---

# 🎓 Network+ Challenge 1

A company has:

```text
PCs ─── Switch ─── Router ─── Remote Network
```

The PCs can communicate with each other but cannot communicate with the remote network.

Which device or path should become a stronger suspect?

### A. Every PC NIC

### B. Router/upstream path

### C. Every Ethernet cable

### D. Replace all PCs

Answer:

> **B — Router/upstream path**

---

# 🎓 Network+ Challenge 2

A company needs to provide wireless devices access to its existing wired LAN.

Which device should be added?

### A. Load balancer

### B. Access point

### C. IDS

### D. Modem

Answer:

> **B — Access point**

---

# 🎓 Network+ Challenge 3

A device has:

```text
192.168.10.10
```

and needs to communicate with:

```text
192.168.20.10
```

Which type of device is needed to route traffic between these two networks?

### A. Hub

### B. Layer 2 switch

### C. Router

### D. Wireless access point

Answer:

> **C — Router**

---

# 🎓 Network+ Challenge 4

A user's wired computer stops communicating.

Every other computer connected to the same switch works normally.

What should you investigate first?

### A. Replace the router

### B. Replace the entire switch

### C. Components unique to the affected computer

### D. Replace every cable in the building

Answer:

> **C — Components unique to the affected computer**

Examples include:

- NIC
- Cable
- Switch port
- IP configuration

---

# 🧠 Troubleshooting Mindset

This lab introduced one of the most important ideas in networking:

```text
What Works?
    ↓
What Doesn't?
    ↓
What Do the Failed Devices Have in Common?
    ↓
Where Does the Working Path Stop?
    ↓
Which Device or Connection Is Next?
```

Don't randomly replace equipment.

Use the topology to narrow the problem.

---

# 📝 Lab Review

In this lab, you:

- Built a larger Packet Tracer network
- Added two switches
- Added a router
- Added PCs
- Added a server
- Added a wireless access point
- Added a wireless laptop
- Connected network interfaces
- Created two IPv4 networks
- Configured default gateways
- Tested local communication
- Routed traffic between networks
- Tested wireless communication
- Used Simulation Mode
- Followed traffic through multiple devices
- Identified device roles
- Broke network connections
- Diagnosed failures
- Repaired the network
- Documented the topology
- Saved the Packet Tracer network

---

# 🧠 What You Just Built

You've progressed from Lab 02:

```text
PC
 │
Switch
 │
PC
```

to:

```text
                   Router
                  /      \
                 /        \
              Switch     Switch
              / | \         |
             /  |  \        |
           PCs  AP         Server
                )))
              Laptop
```

That's a significant step.

You now have a network containing:

```text
Endpoints
    ↓
Network Interfaces
    ↓
Switching
    ↓
Wireless Access
    ↓
Routing
    ↓
Multiple IP Networks
    ↓
Servers
```

But there's an important question we haven't answered yet:

> **What actually happens to data while it travels through all of these devices?**

That's exactly what comes next.

---

# 📍 Course Progress

```text
✅ Lesson 01 — Networking Basics
        ↓
✅ Lab 01 — Networking Basics
        ↓
✅ Lesson 02 — Network Types & Topologies
        ↓
✅ Lab 02 — First Packet Tracer Network
        ↓
✅ Lesson 03 — Network Devices
        ↓
✅ Lab 03 — Network Devices
        ↓
🟡 NEXT: Lesson 04 — The OSI Model
        ↓
⬜ Lab 04 — OSI Model & Packet Simulation
        ↓
⬜ Lesson 05 — TCP/IP & Network Communication
```

---

# ➡️ Next Lesson

You have now seen:

```text
NICs
Switches
Routers
Access Points
Servers
Ethernet
MAC Addresses
IP Addresses
Frames
Packets
```

But how do all of these pieces fit together?

Continue to:

➡️ **[Lesson 04 — The OSI Model](../lessons/📘%20Lesson%2004%20—%20The%20OSI%20Model.md)**

In Lesson 04, you'll learn the seven OSI layers:

```text
7 — Application
6 — Presentation
5 — Session
4 — Transport
3 — Network
2 — Data Link
1 — Physical
```

You'll learn why:

```text
Switches
   ↓
Layer 2
```

and:

```text
Routers
   ↓
Layer 3
```

You'll also begin understanding:

> **Encapsulation and decapsulation**

Then, in **Lab 04**, we'll use Packet Tracer's Simulation Mode to watch data move through the network you now understand how to build.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Packet Tracer Files](../packet-tracer/README.md)**

➡️ **[Cisco Networking Companion](../resources/cisco-companion.md)**

➡️ **[Return to Main README](../README.md)**
