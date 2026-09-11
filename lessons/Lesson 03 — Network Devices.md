# 📘 Lesson 03 — Network Devices

Welcome to **Lesson 03 of Networking Fundamentals**.

In the first two lessons, you learned what networks are, how devices communicate, and how networks can be arranged.

In Lab 02, you also built your first network:

```text
             PC-01
               │
               │
PC-02 ─────── SW-01 ─────── PC-03
```

You used a **switch** to connect the computers.

But switches are only one piece of network infrastructure.

A real network may contain:

```text
NICs
Switches
Routers
Wireless Access Points
Firewalls
Modems
Gateways
Layer 3 Switches
Proxies
Load Balancers
IDS/IPS
```

This lesson explains what these devices do, where they belong, and how recognizing their role can help you troubleshoot network problems.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain the purpose of a Network Interface Card
- Explain the difference between a hub and a switch
- Understand the historical role of network bridges
- Explain what a switch does
- Explain what a router does
- Understand the difference between switches and routers
- Explain the purpose of a Layer 3 switch
- Explain the purpose of a wireless access point
- Understand the basic role of a wireless controller
- Explain what a firewall does
- Explain the purpose of a modem
- Understand the meaning of gateway
- Explain the purpose of a proxy server
- Explain what a load balancer does
- Understand IDS and IPS
- Recognize common network devices in diagrams
- Identify likely failure points during troubleshooting

---

# 🎓 Network+ Focus

Network devices are an important part of **CompTIA Network+ N10-009**.

You should be able to recognize the purpose of devices such as:

- Routers
- Layer 2 switches
- Layer 3 switches
- Firewalls
- IDS/IPS
- Load balancers
- Proxy servers
- Network-attached storage
- Wireless access points
- Wireless controllers
- VPN concentrators

Network+ questions may not simply ask:

> **What is a router?**

Instead, you may receive a scenario and need to determine which device is appropriate.

Focus on:

> **What problem does this device solve?**

---

# 🔌 Network Interface Card — NIC

Every device needs some method of connecting to a network.

A **Network Interface Card**, commonly called a:

> **NIC**

provides that network interface.

Examples include:

```text
Ethernet NIC
Wi-Fi Adapter
Fiber Network Adapter
Virtual Network Adapter
```

Modern computers often have network interfaces built directly into the system.

---

# 🖥️ Example

A desktop computer may have:

```text
PC
 │
 ▼
Ethernet NIC
 │
 ▼
Ethernet Cable
 │
 ▼
Switch
```

A laptop may instead use:

```text
Laptop
   │
   ▼
Wi-Fi Adapter
   )))
Wireless Access Point
```

Both devices need a network interface.

They simply use different technologies.

---

# 🔢 NICs and MAC Addresses

Network interfaces typically have a:

> **MAC Address**

Example:

```text
A4-B1-C1-12-34-56
```

You saw the **Physical Address** field during Lab 01.

We'll study MAC addresses and Ethernet communication in detail during:

> **Lesson 06 — Ethernet and MAC Addressing**

For now, remember:

```text
NIC
 ↓
Network Interface
 ↓
MAC Address
 ↓
Network Communication
```

---

# 🔌 Hub

Before modern Ethernet switches became standard, networks often used devices called:

> **Hubs**

A hub connects multiple Ethernet devices.

But hubs are not very intelligent.

When a hub receives traffic, it essentially repeats that traffic out its other ports.

Conceptually:

```text
        PC-A
          │
          │
PC-B ─── HUB ─── PC-C
          │
        PC-D
```

If PC-A sends traffic:

```text
PC-A
  │
  ▼
 HUB
 / | \
▼  ▼  ▼
B  C  D
```

The hub repeats the traffic broadly.

---

# ⚠️ Why Hubs Became Uncommon

Hubs create several problems.

They:

- Share bandwidth
- Create unnecessary traffic
- Operate within one collision domain
- Don't intelligently forward Ethernet frames
- Don't learn MAC addresses like switches do

Modern Ethernet networks normally use:

> **Switches**

instead.

You should still recognize hubs because they may appear in networking history and certification questions.

---

# 🌉 Network Bridge

A **bridge** connects network segments and can make forwarding decisions using MAC addresses.

Conceptually:

```text
Network Segment A
       │
       ▼
     Bridge
       │
       ▼
Network Segment B
```

Bridges were an important step between simple repeaters/hubs and modern switches.

A bridge can examine MAC addresses and decide whether traffic needs to cross between segments.

---

# 🧠 Bridge vs. Switch

A modern Ethernet switch can be thought of conceptually as:

> **A multiport bridge**

Traditional bridges usually connected relatively few segments.

Switches expanded this idea to many ports with much better performance.

Today, dedicated Ethernet bridges are much less common in typical LAN designs.

---

# 🔀 Switch

You've already used a switch in Packet Tracer.

A **switch** connects devices within a network and intelligently forwards Ethernet frames.

Example:

```text
             PC-01
               │
               │
PC-02 ─────── SW-01 ─────── PC-03
               │
             Printer
```

Unlike a hub, a switch learns information about connected devices.

Specifically, it learns:

> **MAC addresses**

---

# 🧠 How a Switch Thinks

Imagine:

```text
PC-A ─ Port 1
PC-B ─ Port 2
PC-C ─ Port 3
```

The switch may learn:

```text
MAC Address        Port

AA-AA-AA-AA-AA-AA  Port 1
BB-BB-BB-BB-BB-BB  Port 2
CC-CC-CC-CC-CC-CC  Port 3
```

This information is stored in a:

> **MAC Address Table**

When traffic needs to reach PC-B, the switch can forward it toward the appropriate port.

---

# 🔎 Switches Operate Primarily at Layer 2

Traditional Ethernet switches primarily operate at:

> **OSI Layer 2 — Data Link**

Layer 2 networking relies heavily on:

> **MAC addresses**

Don't worry if the OSI layers aren't familiar yet.

That's exactly what **Lesson 04** is about.

For now:

```text
Switch
   ↓
Layer 2
   ↓
MAC Addresses
```

---

# 🏢 Where Are Switches Used?

Switches are everywhere in business networks.

For example:

```text
Desktop ───┐
           │
Printer ─ Switch ─ Router
           │
Server ────┘
```

Large organizations may have:

- Access switches
- Distribution switches
- Core switches

We'll gradually introduce these larger designs later.

---

# 🚦 Managed vs. Unmanaged Switches

Switches can broadly be categorized as:

## Unmanaged

Usually:

- Plug-and-play
- Minimal configuration
- Common in simple environments

## Managed

Provide configuration and monitoring capabilities.

Managed switches may support:

- VLANs
- Spanning Tree Protocol
- Port security
- Link aggregation
- SNMP
- Quality of Service
- Port monitoring
- Administrative management

Enterprise networks commonly use managed switches.

---

# ⚡ Power over Ethernet — PoE

Some switches can provide electrical power through Ethernet cabling.

This is called:

> **PoE — Power over Ethernet**

PoE is commonly used for:

- Wireless access points
- IP phones
- Security cameras
- IoT devices

Example:

```text
PoE Switch
    │
    │ Ethernet
    │ Data + Power
    ▼
Wireless Access Point
```

This means the device may not need a separate electrical power adapter.

---

# 🧠 Real-World Troubleshooting Clue

Suppose an IP phone suddenly loses both:

- Network connectivity
- Power

If the phone receives power through PoE, you might investigate:

```text
Ethernet Cable
Switch Port
PoE Configuration
Switch
```

instead of immediately assuming the phone itself failed.

Understanding the device relationship helps troubleshooting.

---

# 🚦 Router

A **router** connects different IP networks.

Example:

```text
LAN A
  │
  ▼
Router
  │
  ▼
LAN B
```

Routers examine IP addressing information and determine where traffic should go next.

---

# 🌐 Router Example

Consider:

```text
PC
192.168.10.10
      │
      ▼
    Switch
      │
      ▼
    Router
      │
      ▼
   Internet
```

The PC can communicate locally through the switch.

When it needs to reach another network, traffic may be sent toward the:

> **Router**

---

# 🚪 Remember the Default Gateway?

In Lesson 01, you learned about the:

> **Default Gateway**

In many networks, the default gateway is a router or Layer 3 device.

Example:

```text
PC
192.168.10.10

Default Gateway
192.168.10.1
       │
       ▼
     Router
       │
       ▼
Other Networks
```

The router provides a path toward networks outside the local subnet.

---

# 🔀 Switch vs. Router

This distinction is extremely important.

## Switch

Primarily connects devices within a local Ethernet network.

```text
PC ─── Switch ─── Printer
```

Think:

> **MAC addresses**

---

## Router

Connects different IP networks.

```text
Network A
    │
    ▼
 Router
    │
    ▼
Network B
```

Think:

> **IP addresses**

A simple memory aid:

```text
Switch
=
Devices within networks

Router
=
Different networks
```

This is simplified, but it's an excellent starting point.

---

# 🧠 Troubleshooting Example

Suppose:

```text
PC-A ───┐
        │
PC-B ─ Switch ─ Router ─ Internet
        │
PC-C ───┘
```

PC-A can communicate with PC-B and PC-C.

But none of the computers can reach anything outside the local network.

Which device becomes particularly interesting?

> **The router / gateway path**

The local switch appears to be providing local connectivity.

---

# 🔀 Layer 3 Switch

A **Layer 3 switch** combines traditional switching capabilities with routing functionality.

It can perform:

- Layer 2 switching
- Layer 3 routing

Conceptually:

```text
VLAN 10
   │
   ▼
Layer 3 Switch
   │
   ▼
VLAN 20
```

Layer 3 switches are commonly used in enterprise networks to route traffic between VLANs.

We'll explore VLANs later in:

> **Lesson 12 — VLANs and Network Segmentation**

---

# 🧠 Layer 2 vs. Layer 3

For now, remember:

```text
Layer 2 Switch
      ↓
MAC Addresses
      ↓
Ethernet Frames
```

while:

```text
Layer 3 Device
      ↓
IP Addresses
      ↓
Routing
```

Lesson 04 will make these layers much clearer.

---

# 📡 Wireless Access Point

A **Wireless Access Point**, or:

> **AP**

allows wireless devices to connect to a network.

Example:

```text
Laptop )))
         \
Phone ))) AP ─── Switch
         /
Tablet )))
```

The AP connects wireless clients to the wired network infrastructure.

---

# 📡 Access Point vs. Wireless Router

These are often confused.

A dedicated access point primarily provides:

> **Wireless network access**

A typical consumer wireless router may combine several functions:

```text
Router
+
Switch
+
Wireless Access Point
+
Firewall
+
DHCP Server
```

into one physical device.

This is why a home "router" seems to do so many things.

In business environments, these roles are often handled by separate systems.

---

# 🎛️ Wireless LAN Controller

Large wireless environments may have many access points.

Managing each one individually would be difficult.

A:

> **Wireless LAN Controller — WLC**

can provide centralized management for wireless infrastructure.

Conceptually:

```text
         WLC
          │
    ┌─────┼─────┐
    │     │     │
   AP1   AP2   AP3
   )))   )))   )))
```

Controllers can help manage:

- Wireless configuration
- SSIDs
- Security settings
- Radio settings
- Access points
- Client behavior

Modern cloud-managed wireless systems can provide similar centralized capabilities.

---

# 🧱 Firewall

A **firewall** controls network traffic based on security rules.

It can allow or block traffic based on criteria such as:

- Source
- Destination
- Protocol
- Port
- Connection state
- Application
- Security policy

Example:

```text
Internal Network
       │
       ▼
    Firewall
       │
       ▼
    Internet
```

The firewall acts as a security control between network areas.

---

# 🛡️ Firewall Example

Suppose an organization wants:

```text
Employees
    ↓
HTTPS
    ↓
Internet
```

to be allowed.

But it doesn't want arbitrary inbound Internet connections reaching employee computers.

Firewall policies help enforce those rules.

---

# 🔥 Firewalls Aren't Only at the Internet Edge

Firewalls can also exist between internal network segments.

Example:

```text
User Network
     │
     ▼
  Firewall
     │
     ▼
Server Network
```

This can help protect sensitive systems even from other internal networks.

---

# 🧠 Troubleshooting Warning

Firewalls are often blamed when something doesn't work.

Sometimes correctly.

Sometimes not.

Don't immediately assume:

> **"The firewall blocked it."**

Instead determine:

```text
What traffic is failing?

Source?

Destination?

Protocol?

Port?

Does another path work?

What evidence points toward the firewall?
```

Troubleshooting should remain evidence-based.

---

# 📞 Modem

A **modem** allows communication across certain provider technologies by converting or adapting signals as required by the service.

The term comes historically from:

> **Modulator / Demodulator**

Examples include:

- Cable modem
- DSL modem
- Cellular modem

A home connection might look like:

```text
Internet Provider
       │
       ▼
     Modem
       │
       ▼
     Router
       │
       ▼
      LAN
```

Some provider devices combine modem and router functionality into one device.

---

# 🚪 Gateway

The word:

> **Gateway**

can have several networking meanings.

At a basic level, a gateway provides access from one network or system toward another.

You've already encountered:

> **Default Gateway**

Example:

```text
PC
 │
 ▼
Default Gateway
 │
 ▼
Other Network
```

A router commonly performs this role.

But "gateway" can also describe systems that translate or connect different technologies or services.

Context matters.

---

# 🗄️ Network-Attached Storage — NAS

A **Network-Attached Storage** device provides storage accessible over a network.

Example:

```text
PC ───────┐
          │
Laptop ─ Switch ─ NAS
          │
Server ───┘
```

A NAS may provide:

- Shared folders
- File storage
- Backups
- Media storage
- Centralized data access

NAS devices are common in:

- Homes
- Small businesses
- Enterprise environments

---

# 🧠 NAS vs. SAN

These terms are easy to confuse.

## NAS

Provides storage through normal network file-sharing services.

Think:

> **Files over the network**

## SAN

Provides specialized network-based storage infrastructure, often using block-level storage.

Think:

> **Dedicated storage network**

We'll keep this distinction high-level for now.

---

# 🔄 Proxy Server

A **proxy server** acts as an intermediary between a client and another destination.

Instead of:

```text
Client ───────── Website
```

communication may look like:

```text
Client
   │
   ▼
 Proxy
   │
   ▼
Website
```

The proxy communicates on behalf of the client.

---

# 🧠 Why Use a Proxy?

Proxies may provide:

- Content filtering
- Access control
- Logging
- Caching
- Privacy
- Security inspection

There are several types of proxies.

At this point, understand the basic concept:

> **The proxy sits between systems and handles communication on behalf of another device.**

---

# ⚖️ Load Balancer

A **load balancer** distributes traffic across multiple servers or resources.

Without load balancing:

```text
Users
  │
  ▼
Server
```

One server handles everything.

With load balancing:

```text
              Server 1
             /
Users ─ Load Balancer ─ Server 2
             \
              Server 3
```

Traffic can be distributed among several servers.

---

# 🎯 Why Use Load Balancing?

Load balancing can improve:

- Performance
- Scalability
- Availability
- Reliability

Suppose Server 2 fails.

```text
              Server 1
             /
Users ─ Load Balancer ─ Server 2 X
             \
              Server 3
```

The load balancer may continue directing traffic toward healthy servers.

This reduces dependence on a single server.

---

# 👀 IDS — Intrusion Detection System

An:

> **IDS — Intrusion Detection System**

monitors network or system activity for suspicious behavior.

Think:

> **Detect and alert**

Conceptually:

```text
Network Traffic
      │
      ▼
     IDS
      │
      ▼
   Analysis
      │
      ▼
    Alert
```

An IDS typically focuses on identifying suspicious activity rather than directly stopping every detected event.

---

# 🛑 IPS — Intrusion Prevention System

An:

> **IPS — Intrusion Prevention System**

can detect suspicious traffic and take action to block or prevent it.

Think:

> **Detect and stop**

Conceptually:

```text
Network Traffic
      │
      ▼
     IPS
      │
   Inspect
   /     \
Allow   Block
```

---

# 🧠 IDS vs. IPS

A simple way to remember:

```text
IDS
=
Detection
=
"Something suspicious happened."
```

```text
IPS
=
Prevention
=
"Something suspicious happened,
and I'm taking action."
```

Real security architectures can be more complicated, but this distinction is useful for Network+.

---

# 🔐 VPN Concentrator

A **VPN concentrator** handles many VPN connections.

For example:

```text
Remote Worker ── VPN ──┐
                       │
Remote Worker ── VPN ──┼── VPN Concentrator ─ Corporate Network
                       │
Remote Worker ── VPN ──┘
```

Its job may include:

- Establishing VPN tunnels
- Encryption
- Authentication
- Managing remote connections

Modern firewalls and other security appliances often include VPN functionality, so a dedicated VPN concentrator isn't always a separate physical box.

---

# 🧰 One Device Can Perform Multiple Roles

This is extremely important.

A physical device doesn't always perform only one function.

A modern firewall appliance might provide:

```text
Firewall
Router
VPN Concentrator
IDS/IPS
Web Filtering
NAT
```

A home wireless router may provide:

```text
Router
Switch
Access Point
Firewall
DHCP
NAT
```

So don't always assume:

> **One box = one networking function**

Instead ask:

> **What roles is this device performing?**

---

# 🏢 Example Small-Business Network

Consider:

```text
                    Internet
                       │
                       ▼
                  ISP Modem
                       │
                       ▼
                    Firewall
                       │
                       ▼
                     Router
                       │
                       ▼
                     SW-01
           ┌───────────┼───────────┐
           │           │           │
           ▼           ▼           ▼
         PC-01       Server        AP-01
                                   )))
                              ┌─────┴─────┐
                              │           │
                           Laptop       Phone
```

Different devices perform different roles.

---

# 🧠 Identify the Devices

In the previous network:

### Modem

Provides connectivity toward the ISP technology.

### Firewall

Controls traffic according to security policies.

### Router

Routes traffic between IP networks.

### Switch

Connects devices within the LAN.

### Access Point

Provides wireless connectivity.

### NICs

Allow individual devices to connect to the network.

---

# 🧭 Follow the Path

Suppose the laptop opens a website.

The path might resemble:

```text
Laptop
  )))
Access Point
   │
   ▼
 Switch
   │
   ▼
 Router
   │
   ▼
Firewall
   │
   ▼
 Modem
   │
   ▼
Internet
   │
   ▼
Web Server
```

Every device in the path has a job.

Understanding those jobs helps you determine where communication may be failing.

---

# 🔧 Troubleshooting Scenario 1

Consider:

```text
PC-01 ───┐
         │
PC-02 ─ Switch ─ Router ─ Internet
         │
PC-03 ───┘
```

PC-01 cannot communicate.

PC-02 and PC-03 work normally.

Where should you begin?

Look at things unique to PC-01:

```text
NIC
Cable
Switch Port
IP Configuration
```

Replacing the router would not be a logical first step.

---

# 🔧 Troubleshooting Scenario 2

Now:

```text
PC-01 ───┐
         │
PC-02 ─ Switch ─ Router X ─ Internet
         │
PC-03 ───┘
```

All PCs can communicate locally.

None can reach remote networks.

The router/default gateway path becomes a stronger suspect.

---

# 🔧 Troubleshooting Scenario 3

Suppose:

```text
Wired PCs
   │
   ▼
 Switch
   │
   ├──── Router ─── Internet
   │
   └──── AP X
```

Wired computers work.

Wireless devices cannot connect.

Which component should become particularly interesting?

> **The wireless access point**

Again, understand the topology and identify what affected systems have in common.

---

# 🔧 Troubleshooting Scenario 4

Suppose:

```text
Phone ─────┐
Camera ─── PoE Switch
AP ────────┘
```

All three devices suddenly lose power.

What do they have in common?

> **The PoE switch**

That shared dependency becomes an important troubleshooting clue.

---

# 🗺️ Device Quick Reference

| Device | Primary Purpose |
|---|---|
| NIC | Connects a device to a network |
| Hub | Repeats traffic to connected ports |
| Bridge | Connects Layer 2 network segments |
| Switch | Connects LAN devices and forwards frames |
| Layer 3 Switch | Switching plus routing |
| Router | Connects different IP networks |
| Access Point | Connects wireless clients |
| Wireless Controller | Centrally manages wireless infrastructure |
| Firewall | Controls network traffic based on security rules |
| Modem | Interfaces with certain provider technologies |
| Gateway | Provides access between networks/systems |
| NAS | Provides network-accessible file storage |
| Proxy | Acts as an intermediary |
| Load Balancer | Distributes traffic across resources |
| IDS | Detects suspicious activity |
| IPS | Detects and can block suspicious activity |
| VPN Concentrator | Handles multiple VPN connections |

---

# 🧠 Knowledge Check

Try answering these before looking at the answers.

### 1.

Which device primarily connects devices inside an Ethernet LAN?

### 2.

Which device connects different IP networks?

### 3.

Which device provides wireless network connectivity?

### 4.

Which device controls traffic based on security rules?

### 5.

Which device repeats received traffic broadly rather than intelligently forwarding based on MAC addresses?

### 6.

What does PoE allow an Ethernet connection to carry in addition to data?

### 7.

Which device distributes incoming traffic across several servers?

### 8.

What is the primary difference between an IDS and IPS?

### 9.

Which device might centrally manage many wireless access points?

### 10.

Which device combines Layer 2 switching with Layer 3 routing?

---

# ✅ Knowledge Check Answers

### 1.

**Switch**

### 2.

**Router**

### 3.

**Wireless Access Point**

### 4.

**Firewall**

### 5.

**Hub**

### 6.

**Electrical power**

### 7.

**Load Balancer**

### 8.

An IDS primarily detects and alerts, while an IPS can detect and take action to block suspicious traffic.

### 9.

**Wireless LAN Controller**

### 10.

**Layer 3 Switch**

---

# 🎓 Network+ Challenge

A company wants a device that can inspect network traffic and automatically block traffic identified as malicious.

Which device best fits the requirement?

### A. Hub

### B. IDS

### C. IPS

### D. Access Point

Answer:

> **C — IPS**

---

A company operates three web servers and wants user traffic distributed among them.

Which device should be used?

### A. Load Balancer

### B. Modem

### C. Wireless Controller

### D. Layer 2 Switch

Answer:

> **A — Load Balancer**

---

Employees need wireless connectivity to the existing wired LAN.

Which device should be deployed?

### A. Proxy

### B. Access Point

### C. IDS

### D. Modem

Answer:

> **B — Access Point**

---

A company needs to connect two different IP networks.

Which device is primarily designed for this purpose?

### A. Hub

### B. Layer 2 Switch

### C. Router

### D. Wireless Access Point

Answer:

> **C — Router**

---

# 🧠 Exam Tip — Think Function First

Network+ may describe what an organization needs rather than naming the technology.

For example:

> **"The company needs to distribute web requests across multiple application servers."**

Think:

```text
Distribute Traffic
       ↓
Multiple Servers
       ↓
Load Balancer
```

Or:

> **"Security wants suspicious network traffic automatically blocked."**

Think:

```text
Detect
+
Prevent
=
IPS
```

Don't memorize only the device name.

Associate it with its **function**.

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- NICs connect individual devices to networks.
- Hubs repeat traffic and are largely obsolete in modern Ethernet LANs.
- Bridges connect Layer 2 network segments.
- Switches intelligently forward Ethernet frames.
- Switches learn MAC addresses.
- Routers connect different IP networks.
- Default gateways commonly point toward routers or Layer 3 devices.
- Layer 3 switches combine switching and routing.
- Access points connect wireless clients.
- Wireless controllers can centrally manage APs.
- Firewalls enforce network security rules.
- Modems interface with certain provider technologies.
- Gateways provide paths between networks or systems.
- NAS devices provide network-accessible storage.
- Proxies act as intermediaries.
- Load balancers distribute traffic.
- IDS detects suspicious activity.
- IPS can detect and block suspicious activity.
- VPN concentrators manage VPN connections.
- One physical appliance may perform several networking roles.

---

# 🌐 Cisco Companion

Cisco Packet Tracer is particularly useful for this lesson because you'll be able to identify and connect several types of network infrastructure.

➡️ **[Cisco Networking Companion](../resources/cisco-companion.md)**

In Lab 03, you'll return to Packet Tracer and expand the small network you created in Lab 02.

---

# 🛠️ Project Progress

You're still working toward:

> **Project 01 — Build Your First Network**

So far you've learned:

```text
Lesson 01
Networking Basics
      ↓
Lesson 02
Network Types & Topologies
      ↓
Lesson 03
Network Devices
```

You're beginning to understand both:

> **How networks are arranged**

and:

> **What the devices inside them actually do**

Lessons 04 and 05 will explain what happens to data as it travels through those devices.

---

# 🎥 Optional Video Resource

Professor Messer's Network+ N10-009 training includes material covering networking devices.

### Professor Messer — Networking Devices

Use this as optional reinforcement after completing the lesson.

➡️ [Professor Messer — Network+ N10-009 Training Course](https://www.professormesser.com/network-plus/n10-009/n10-009-video/n10-009-training-course/)

> ⭐ **Optional**
>
> Look for the networking-device material in the N10-009 course.
>
> Focus on understanding the purpose of each device rather than memorizing definitions.
>
> You do not need to watch the video before completing Lab 03.

---

# 🧪 Next Step — Complete the Lab

Now you'll work with these devices in Cisco Packet Tracer.

➡️ **[Lab 03 — Network Devices](../labs/lab-03-network-devices.md)**

In Lab 03, you'll:

- Open your Packet Tracer environment
- Add switches
- Add a router
- Add PCs
- Add a server
- Add a wireless access point
- Identify network interfaces
- Connect network devices
- Compare switches and routers
- Examine device interfaces
- Build a larger network diagram
- Identify network-device roles
- Troubleshoot device failures

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
🟡 NEXT: Lab 03 — Network Devices
        ↓
⬜ Lesson 04 — The OSI Model
```

---

# ➡️ After the Lab

After completing Lab 03, continue to:

**📘 Lesson 04 — The OSI Model**

That's where we'll finally explain why you've been seeing terms such as:

```text
Layer 2
Layer 3
Ethernet Frame
MAC Address
IP Address
```

You'll learn how the **seven OSI layers** provide a framework for understanding network communication and troubleshooting.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Packet Tracer Files](../packet-tracer/README.md)**

➡️ **[Cisco Networking Companion](../resources/cisco-companion.md)**

➡️ **[Return to Main README](../README.md)**