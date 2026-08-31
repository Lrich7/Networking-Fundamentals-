# 📘 Lesson 02 — Network Types and Topologies

Welcome to **Lesson 02 of Networking Fundamentals**.

In Lesson 01, you learned what a network is and how your own computer connects to one.

Now we'll look at two bigger questions:

> **What kinds of networks exist?**

and:

> **How are devices arranged and connected inside those networks?**

These concepts are important because the size, purpose, and design of a network affect how it is built, managed, secured, and troubleshot.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain the difference between a LAN, WAN, WLAN, PAN, MAN, and SAN
- Understand client-server and peer-to-peer network models
- Explain what a network topology is
- Identify common physical and logical network topologies
- Explain star, bus, ring, mesh, and hybrid topologies
- Understand the difference between physical and logical topology
- Recognize common real-world network layouts
- Begin reading simple network diagrams
- Understand why topology matters during troubleshooting
- Prepare to build your first network in Cisco Packet Tracer

---

# 🎓 Network+ Focus

This lesson supports concepts found in **CompTIA Network+ N10-009**, especially network types, network architectures, and topologies.

Pay particular attention to:

- LAN
- WAN
- WLAN
- Network topology
- Star topology
- Mesh topology
- Hybrid topology
- Point-to-point connections
- Client-server networks
- Peer-to-peer networks

You do not need to memorize every possible network design immediately.

Focus on understanding:

> **What is connected, how is it connected, and why was it designed that way?**

---

# 🌐 What Is a Network Type?

Networks can be categorized in several ways.

One of the easiest is by looking at:

- Geographic size
- Purpose
- Technology
- Ownership

For example, a network inside one office is very different from a network connecting offices across several states.

Some common network types include:

```text
LAN
WAN
WLAN
PAN
MAN
SAN
```

Let's look at each one.

---

# 🏢 LAN — Local Area Network

A **Local Area Network**, or **LAN**, connects devices within a relatively small geographic area.

Examples include:

- A home
- A small office
- A school classroom
- A business building
- A single floor of an office
- A data center

A simple LAN might look like:

```text
PC ───────┐
          │
Laptop ───┼── Switch ─── Router
          │
Printer ──┘
```

The devices inside the local network communicate through networking equipment such as switches and routers.

---

# 🧠 Real-World LAN Example

Imagine a small company with:

```text
40 Computers
10 Printers
3 Servers
5 Wireless Access Points
Several Switches
1 Firewall
```

These devices may all be part of the company's local network.

That network is a:

> **LAN**

---

# 🏠 Your Home Network Is Usually a LAN

A typical home network might include:

```text
Laptop
Phone
Smart TV
Game Console
Printer
```

connected through a home router.

Even though the router provides Internet access, the devices inside your home are still communicating on a local network.

---

# 📡 WLAN — Wireless Local Area Network

A **Wireless Local Area Network**, or **WLAN**, is a LAN that uses wireless networking technology.

In most cases, this means:

> **Wi-Fi**

Example:

```text
Laptop )))
         \
Phone ))) --- Wireless Access Point --- Network
         /
Tablet )))
```

A WLAN is not necessarily a completely separate network from the wired LAN.

Often, wireless and wired devices are part of the same broader local network.

---

# 🧠 LAN vs. WLAN

Consider an office.

Desktop computers may connect using Ethernet:

```text
Desktop
   │
Ethernet
   │
Switch
```

Laptops may connect through Wi-Fi:

```text
Laptop
   )))
Wireless Access Point
```

Both may ultimately connect to the same business network.

The difference is primarily the connection method.

---

# 🌎 WAN — Wide Area Network

A **Wide Area Network**, or **WAN**, connects networks across larger geographic areas.

Examples include:

- Two company offices in different cities
- Branch locations across several states
- International corporate networks
- Provider networks
- Connections between remote facilities

Example:

```text
Office A LAN
     │
     ▼
   Router
     │
     │
     WAN
     │
     ▼
   Router
     │
     ▼
Office B LAN
```

The WAN connects the two local networks.

---

# 🏢 Business WAN Example

Imagine a company with locations in:

```text
Chicago
Dallas
Atlanta
Denver
```

Each office may have its own LAN.

The company may use WAN technologies or VPN connections to connect those locations.

```text
Chicago LAN
      │
      ├────────┐
      │        │
Dallas LAN ─── WAN ─── Atlanta LAN
      │
      └──────── Denver LAN
```

We'll study WAN technologies much later in the course.

---

# 🌍 Is the Internet a WAN?

The Internet is much larger and more complex than a single traditional enterprise WAN.

However, it demonstrates the same broad concept:

> Networks connected across very large geographic areas.

For beginner networking purposes, thinking of a WAN as a network that connects geographically separated networks is useful.

---

# 📱 PAN — Personal Area Network

A **Personal Area Network**, or **PAN**, is a very small network centered around an individual person.

Examples include:

- Bluetooth headphones connected to a phone
- Smartwatch connected to a phone
- Wireless keyboard connected to a computer
- Personal hotspot connections

Example:

```text
Smartwatch
     \
      \
Phone ─── Headphones
      \
       \
      Laptop
```

PANs usually cover a very short distance.

---

# 🏙️ MAN — Metropolitan Area Network

A **Metropolitan Area Network**, or **MAN**, covers an area larger than a LAN but smaller than a traditional WAN.

A MAN might connect locations across:

- A city
- A large campus
- A metropolitan region

Example:

```text
Building A
    │
    │
City Network
    │
    ├──── Building B
    │
    └──── Building C
```

You may encounter the term on certification exams even though many IT environments simply describe these networks using LAN/WAN terminology.

---

# 💾 SAN — Storage Area Network

A **Storage Area Network**, or **SAN**, is a specialized high-speed network used to provide access to storage.

A SAN commonly connects:

```text
Servers
   │
   ▼
Storage Network
   │
   ▼
Storage Arrays
```

SANs are commonly found in:

- Data centers
- Virtualization environments
- Enterprise infrastructure

A SAN is different from simply sharing a folder over the network.

Its purpose is specifically centered around providing network-based storage infrastructure.

We'll keep SAN concepts high-level in this course.

---

# 📋 Network Type Summary

| Type | Name | General Purpose |
|---|---|---|
| LAN | Local Area Network | Connect devices in a local area |
| WLAN | Wireless Local Area Network | Connect local devices using wireless networking |
| WAN | Wide Area Network | Connect geographically separated networks |
| PAN | Personal Area Network | Connect devices around an individual |
| MAN | Metropolitan Area Network | Connect networks across a city or metro area |
| SAN | Storage Area Network | Provide dedicated network access to storage |

---

# 🧠 Quick Scenario

A company has one office building with:

- 25 PCs
- 4 printers
- 2 servers
- 3 switches

What type of network is this primarily?

```text
A. WAN

B. LAN

C. PAN

D. MAN
```

Answer:

> **LAN**

---

# 🧠 Another Scenario

A company connects its Chicago office to its Dallas office.

What type of network is being created between the locations?

```text
A. PAN

B. SAN

C. WAN

D. WLAN
```

Answer:

> **WAN**

---

# 👥 Client-Server Networks

Network type describes things such as size or purpose.

We can also describe networks based on **how resources are provided**.

One common model is:

> **Client-server**

In a client-server network, dedicated systems provide services to other devices.

Example:

```text
          File Server
              │
              │
PC ──────── Switch ─────── Laptop
              │
              │
          Print Server
```

Clients request services.

Servers provide them.

---

# 🖥️ Common Server Roles

Servers may provide services such as:

- Authentication
- Files
- Printing
- Websites
- Email
- DNS
- DHCP
- Databases
- Applications

A business environment often relies heavily on client-server networking.

---

# 🤝 Peer-to-Peer Networks

Another model is:

> **Peer-to-peer**

In a peer-to-peer network, devices can share resources directly with one another without relying on a dedicated centralized server for that specific resource.

Example:

```text
Computer A
    │
    ├──────── Computer B
    │
    └──────── Computer C
```

Computer A might share a folder directly with Computer B.

Computer B could also share another resource back.

---

# 🧠 Peer-to-Peer Example

Imagine two home computers.

Computer A shares a folder:

```text
\\ComputerA\Photos
```

Computer B connects directly to that shared folder.

There is no dedicated file server involved.

This is a simple peer-to-peer example.

---

# ⚖️ Client-Server vs. Peer-to-Peer

| Client-Server | Peer-to-Peer |
|---|---|
| Centralized services | Direct sharing |
| Easier centralized management | Simple for small environments |
| Common in businesses | Common in small/home environments |
| Can scale well | Becomes harder to manage at scale |
| Dedicated infrastructure may be used | Dedicated server may not be required |

Neither concept means every communication on the network must work exactly that way.

These are broad architecture models.

---

# 🗺️ What Is a Network Topology?

A **network topology** describes how devices and connections are arranged.

In simple terms:

> **What connects to what?**

For example:

```text
PC ─── Switch ─── Router
```

is a very simple topology.

A larger network may look like:

```text
PC ───────┐
          │
PC ───── Switch ───── Router ───── Internet
          │
Printer ──┘
```

Understanding the topology helps you understand the path traffic may take.

---

# 🧩 Physical vs. Logical Topology

There are two useful ways to think about topology.

## Physical Topology

The **physical topology** describes how devices and cables are physically arranged.

Example:

```text
PC
 │
Cable
 │
Switch
```

It answers questions such as:

- Which cable connects to which port?
- Which switch is in which room?
- Where is the router physically located?
- Which access point covers which area?

---

# 🧠 Logical Topology

The **logical topology** describes how network communication is organized or how traffic flows.

The physical layout and logical layout aren't always identical.

For now, think of the difference as:

```text
Physical topology
=
How things are physically connected

Logical topology
=
How communication is organized
```

This distinction becomes much more important as networks become more advanced.

---

# ⭐ Star Topology

The **star topology** is one of the most common network designs you'll encounter.

Devices connect to a central device.

Example:

```text
          PC
          │
          │
PC ──── Switch ──── Printer
          │
          │
        Laptop
```

The switch is at the center.

Each endpoint has its own connection to that central device.

---

# ✅ Advantages of a Star Topology

Star topologies are popular because they are generally easy to manage and troubleshoot.

If one computer's cable fails:

```text
          PC
          │
          X
PC ──── Switch ──── Printer
          │
        Laptop
```

the rest of the network may continue working.

The failure affects one connection rather than every device.

---

# ⚠️ Star Topology Weakness

The central device is very important.

Suppose the central switch fails:

```text
          PC
          │
          │
PC ──── SWITCH X ──── Printer
          │
        Laptop
```

Many connected devices may lose communication.

This introduces an important networking idea:

> **Single Point of Failure**

A single point of failure is a component whose failure can cause a larger service interruption.

We'll revisit this idea many times.

---

# 🚌 Bus Topology

In a traditional **bus topology**, devices share a common communication path.

Conceptually:

```text
PC ───── PC ───── PC ───── PC
```

Older Ethernet technologies used designs that resembled this topology.

Bus networks aren't the normal design for modern switched Ethernet LANs.

However, understanding the topology is still useful historically and conceptually.

---

# ⚠️ Bus Topology Problem

Because devices rely on the shared path, problems with that path can affect multiple devices.

For example:

```text
PC ───── PC ── X ── PC ───── PC
```

A failure in the shared medium may cause significant communication problems.

---

# 🔄 Ring Topology

In a **ring topology**, devices are connected in a circular pattern.

Example:

```text
       PC A
      /    \
     /      \
  PC D      PC B
     \      /
      \    /
       PC C
```

Traffic may travel around the ring.

Ring-based technologies have historically been used in networking.

Modern enterprise Ethernet networks usually don't connect end-user computers in a traditional ring like this.

However, ring concepts can still appear in certain network designs and technologies.

---

# 🕸️ Mesh Topology

In a **mesh topology**, devices have multiple connections between them.

A simplified mesh might look like:

```text
Router A ───── Router B
   │  \         /  │
   │    \     /    │
   │      \ /      │
   │      / \      │
   │    /     \    │
   │  /         \  │
Router C ───── Router D
```

Mesh designs can provide multiple possible paths.

---

# ✅ Why Use Mesh?

Suppose one connection fails.

Instead of communication stopping completely:

```text
A ─── X ─── B
```

traffic may have another path:

```text
A
 \
  C
   \
    B
```

This improves:

> **Redundancy**

Redundancy means having alternate components or paths available if one fails.

---

# 🧠 Full Mesh vs. Partial Mesh

A **full mesh** means every device connects directly to every other device.

Example:

```text
A ───── B
|\     /|
| \   / |
|  \ /  |
|  / \  |
| /   \ |
|/     \|
C ───── D
```

This provides many paths but can become expensive and complicated.

---

## Partial Mesh

A **partial mesh** provides multiple paths without connecting every device directly to every other device.

Example:

```text
A ───── B
│       │
│       │
C ───── D
 \     /
   \ /
    E
```

Many real-world networks use some form of partial redundancy rather than complete full mesh designs.

---

# 🔀 Hybrid Topology

Most real networks aren't perfect textbook examples.

They combine several designs.

This is called a:

> **Hybrid topology**

For example:

```text
PC ───┐
      │
PC ─ Switch A
      │
      │
    Router
      │
      │
   Switch B
      │
Laptop ─┐
Printer ─┘
```

Each local switch area resembles a star.

Multiple switches and routers may connect those areas into a larger design.

The overall result is a hybrid network.

---

# ↔️ Point-to-Point Connection

A **point-to-point** connection links two endpoints directly.

Example:

```text
Router A ───────── Router B
```

This design is commonly associated with direct links between networking devices.

A point-to-point connection is simple:

```text
Device A
    │
    │
Device B
```

There are only two endpoints on that connection.

---

# 🧠 Topology Is About Relationships

Don't memorize diagrams without understanding them.

Ask:

```text
What is the central device?

Does every endpoint connect individually?

Are there multiple possible paths?

Is there one shared path?

What happens if one link fails?

What happens if one central device fails?
```

These questions help you identify the topology and understand its weaknesses.

---

# 🔧 Why Topology Matters to IT

Suppose a user says:

> **"My computer cannot reach the network."**

If the network uses a star topology:

```text
User PC
   │
   ▼
Switch
   │
   ▼
Router
```

you can begin investigating the path.

Maybe:

```text
PC NIC
   ↓
Cable
   ↓
Switch Port
   ↓
Switch
   ↓
Router
```

Knowing the topology tells you **where to look**.

---

# 🧠 Troubleshooting Scenario 1

Consider this network:

```text
PC A ───┐
        │
PC B ─ Switch ─ Router
        │
PC C ───┘
```

PC A cannot connect.

PC B and PC C work normally.

What should you suspect first?

Probably something specific to PC A's connection, such as:

- PC A's network adapter
- Its cable
- Its switch port
- Its network configuration

The central switch is less likely to be completely down because other computers are working.

---

# 🧠 Troubleshooting Scenario 2

Now imagine:

```text
PC A ───┐
        │
PC B ─ Switch X ─ Router
        │
PC C ───┘
```

All three PCs lose connectivity at the same time.

What has changed?

The shared device is now an important suspect.

> **The switch may be a common point of failure.**

This is why topology matters during troubleshooting.

---

# 📐 Reading a Basic Network Diagram

You will see diagrams throughout this course.

For example:

```text
PC-01 ───┐
         │
PC-02 ─ SW-01 ─ R-01 ─ Internet
         │
PRN-01 ──┘
```

Common naming conventions might include:

```text
PC   = Computer
SW   = Switch
R    = Router
PRN  = Printer
AP   = Wireless Access Point
FW   = Firewall
SRV  = Server
```

There is no universal naming scheme that every organization must use.

Organizations often create their own standards.

The important thing is consistency.

---

# 🗺️ Example Small-Business Network

A small office network might look like:

```text
                    Internet
                       │
                       │
                    Firewall
                       │
                       │
                     Switch
          ┌────────────┼────────────┐
          │            │            │
          ▼            ▼            ▼
       PC-01         PC-02          AP
                                     )))
                                   Laptop
                                     )))
                                    Phone
```

This network contains both:

- Wired LAN connections
- Wireless LAN connections

The topology is primarily star-based around the central switch.

---

# 🌎 Example Multi-Site Business

Now imagine:

```text
Chicago Office
     │
     ▼
 Chicago Router
     │
     │
     WAN
     │
     ▼
 Dallas Router
     │
     ▼
Dallas Office
```

Each office contains its own:

> LAN

The connection between the offices is:

> WAN connectivity

---

# 🧠 Network Types Can Exist Together

One organization might simultaneously have:

```text
LAN
WLAN
WAN
PAN
SAN
```

For example:

```text
Company Network
│
├── LAN
│   └── Office desktops and printers
│
├── WLAN
│   └── Laptops and phones
│
├── WAN
│   └── Connection to branch office
│
├── PAN
│   └── Employee Bluetooth devices
│
└── SAN
    └── Data center storage
```

These aren't necessarily competing network types.

They describe different parts or purposes of the environment.

---

# 🛡️ Design Affects Reliability

Consider these two networks.

## Network A

```text
PC ─── Switch ─── Router
```

There is one path.

## Network B

```text
             Router A
            /        \
PC ─ Switch            Internet
            \        /
             Router B
```

Network B introduces additional paths.

That may improve resilience, but it also increases:

- Cost
- Configuration complexity
- Troubleshooting complexity

Networking design often involves balancing:

```text
Cost
Performance
Reliability
Security
Complexity
Scalability
```

There is rarely one perfect design for every organization.

---

# 📈 Scalability

A network that works for five computers may not be appropriate for 500 computers.

Good network design considers:

> **Scalability**

Scalability means the ability of a system to grow while continuing to function effectively.

For example:

```text
5 Devices
   ↓
50 Devices
   ↓
500 Devices
   ↓
5,000 Devices
```

As networks grow, they require more planning.

This eventually includes:

- More switches
- Routing
- VLANs
- Subnetting
- Redundancy
- Monitoring
- Security controls
- Documentation

We'll build toward all of those concepts.

---

# 🧠 Don't Design Networks From Memory Alone

You may see diagrams like:

```text
Star
Mesh
Ring
Bus
```

on exams.

But in real IT work, the more important skill is being able to look at a network and ask:

```text
Where does traffic need to go?

Which devices are shared?

Which connections are critical?

Where are the possible failure points?

Are there alternate paths?

How would I troubleshoot this?
```

That is how topology becomes useful rather than just something to memorize.

---

# 🔧 Terms Introduced in This Lesson

Make sure you recognize:

```text
LAN
WLAN
WAN
PAN
MAN
SAN

Client-Server
Peer-to-Peer

Topology
Physical Topology
Logical Topology

Star
Bus
Ring
Mesh
Hybrid
Point-to-Point

Redundancy
Single Point of Failure
Scalability
```

You don't need to be an expert on all of them yet.

---

# 🧠 Knowledge Check

Try answering these before looking at the answers.

### 1.

What type of network usually connects devices within a single office or building?

### 2.

What type of network connects geographically separated locations?

### 3.

What does WLAN stand for?

### 4.

What type of network is commonly associated with Bluetooth devices around one person?

### 5.

What is the purpose of a SAN?

### 6.

What network topology connects endpoint devices to a central device?

### 7.

What is a major weakness of a basic star topology?

### 8.

What topology provides multiple potential paths between devices?

### 9.

What is a hybrid topology?

### 10.

What is the difference between physical and logical topology?

---

# ✅ Knowledge Check Answers

### 1.

**LAN — Local Area Network**

---

### 2.

**WAN — Wide Area Network**

---

### 3.

**Wireless Local Area Network**

---

### 4.

**PAN — Personal Area Network**

---

### 5.

A SAN provides specialized network connectivity for storage systems.

---

### 6.

**Star topology**

---

### 7.

The central device can become a single point of failure.

---

### 8.

**Mesh topology**

---

### 9.

A hybrid topology combines characteristics of multiple topology types.

---

### 10.

Physical topology describes how devices are physically connected, while logical topology describes how communication is organized or flows through the network.

---

# 🧪 Troubleshooting Challenge

Consider this network:

```text
PC-01 ─────┐
           │
PC-02 ─── Switch ─── Router
           │
PC-03 ─────┘
```

PC-01 and PC-02 work normally.

PC-03 cannot communicate with anything.

Which is the better first approach?

### A.

Replace the router immediately.

### B.

Investigate the PC-03 adapter, cable, configuration, and switch port.

### C.

Replace the switch immediately.

### D.

Rebuild the entire network.

Answer:

> **B**

Because other computers connected through the same switch and router are working, begin with components unique to PC-03.

---

# 🧪 Troubleshooting Challenge 2

Now all computers connected to the same switch stop communicating at the same time.

Which device becomes a stronger suspect?

> **The shared switch**

Again, topology helps narrow the investigation.

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- A LAN connects devices within a local area.
- A WLAN is a wireless local network.
- A WAN connects geographically separated networks.
- A PAN connects devices around an individual.
- A MAN covers a metropolitan area.
- A SAN is designed for network-based storage.
- Client-server networks use centralized services.
- Peer-to-peer networks allow direct resource sharing.
- A topology describes how devices and connections are arranged.
- Star topology is extremely common in modern LANs.
- Mesh designs provide alternate paths.
- Hybrid networks combine topology types.
- Central devices may become single points of failure.
- Network topology is useful for troubleshooting.
- Real networks often combine several network types and designs.

---

# 🎓 Network+ Exam Tip

Network+ may give you a diagram or scenario rather than directly asking:

> "What is a star topology?"

For example:

> Every workstation has its own Ethernet cable connected to one central switch.

That describes a:

**Star topology**

Or:

> A business has offices in two different states connected through provider connectivity.

That connection is part of a:

**WAN**

Try to associate each term with a real design rather than memorizing definitions alone.

---

# 🌐 Cisco Companion

Cisco Networking Academy can provide additional visual and interactive networking practice.

➡️ [Cisco Networking Companion](../resources/cisco-companion.md)

Cisco material is supplemental.

The primary hands-on activity for this lesson will happen in **Lab 02**, where you'll begin using Cisco Packet Tracer.

---

# 🛠️ Project Progress

You're working toward:

➡️ **Project 01 — Build Your First Network**

Project 01 comes after Lesson 05.

Concepts from this lesson you'll use in that project include:

- Network types
- Network diagrams
- Star topology
- Device relationships
- Physical connections

---

# 🎥 Optional Video Resource

Professor Messer provides a short Network+ video that reinforces the topology concepts in this lesson.

### Professor Messer — Network Topologies

**CompTIA Network+ N10-009 — Network Topologies (4:42)**

➡️ [Professor Messer — N10-009 Network+ Training Course](https://www.professormesser.com/network-plus/n10-009/n10-009-video/n10-009-training-course/)

> ⭐ **Optional**
>
> Look for **Network Topologies** under Section 1.6.
>
> The video reinforces star, mesh, hybrid, and other topology concepts from this lesson.
>
> You do not need to watch it before completing Lab 02.

---

# 🧪 Next Step — Complete the Lab

Now you'll begin building networks instead of only reading about them.

➡️ **[Lab 02 — Network Types and Topologies](../labs/lab-02-network-types-and-topologies.md)**

In Lab 02, you'll:

- Open Cisco Packet Tracer
- Learn the basic Packet Tracer interface
- Add network devices
- Add computers
- Add a switch
- Connect devices
- Build your first star topology
- Identify LAN components
- Experiment with topology changes
- Begin reading and creating simple network diagrams

This will be your first **Cisco Packet Tracer lab**.

---

# ➡️ After the Lab

When Lab 02 is complete, continue to:

**Lesson 03 — Network Devices**

There you'll take a closer look at:

- Switches
- Routers
- Firewalls
- Wireless access points
- Modems
- Gateways
- Layer 3 switches
- Proxies
- Load balancers
- IDS/IPS

---

# 📚 Return to Course

➡️ [Networking Lessons](README.md)

➡️ [Networking Labs](../labs/README.md)