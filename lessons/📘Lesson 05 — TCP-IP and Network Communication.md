# 📘 Lesson 05 — TCP/IP and Network Communication

Welcome to **Lesson 05 of Networking Fundamentals**.

In Lesson 04, you learned the **OSI model** and used it to organize network communication into seven conceptual layers.

Now we're going to look at the model that more closely describes how modern IP networks actually operate:

> **The TCP/IP Model**

You'll also follow a complete network communication from an application on one computer to an application on another.

This lesson brings together many of the concepts you've already seen:

```text
Applications
TCP
UDP
IP Addresses
MAC Addresses
Ethernet
Switches
Routers
Frames
Packets
Encapsulation
Decapsulation
```

By the end, these pieces should begin to feel like parts of one system instead of separate networking terms.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain what the TCP/IP model is
- Name the four TCP/IP layers
- Compare the TCP/IP model to the OSI model
- Explain the purpose of the Application layer
- Explain the purpose of the Transport layer
- Explain the purpose of the Internet layer
- Explain the purpose of the Network Access layer
- Understand how applications communicate across networks
- Explain how TCP and UDP fit into network communication
- Explain how IP provides logical addressing
- Explain how Ethernet provides local delivery
- Describe encapsulation through the TCP/IP model
- Describe decapsulation at the destination
- Follow traffic through switches and routers
- Understand the difference between local and remote communication
- Use the TCP/IP model during troubleshooting

---

# 🎓 Network+ Focus

This lesson reinforces concepts important to **CompTIA Network+ N10-009**.

Pay particular attention to:

- TCP/IP
- TCP
- UDP
- IPv4
- IPv6
- Ethernet
- MAC addressing
- Encapsulation
- Network communication
- Application protocols
- Ports
- Routers
- Switches
- Local vs. remote communication

A Network+ question may describe a communication problem and expect you to understand which part of the TCP/IP process is involved.

The goal isn't simply to memorize four layers.

Understand:

> **What job is being performed at each stage?**

---

# 🌐 What Is TCP/IP?

TCP/IP stands for:

> **Transmission Control Protocol / Internet Protocol**

TCP and IP are two important protocols, but the term **TCP/IP** is commonly used to describe the entire family of protocols used by modern IP networks.

The Internet itself relies on TCP/IP.

Your:

- Windows computer
- Phone
- Router
- Server
- Cloud application
- Website

all rely on TCP/IP networking.

---

# 🧱 The TCP/IP Model

A common four-layer TCP/IP model is:

| Layer | Name |
|---:|---|
| 4 | Application |
| 3 | Transport |
| 2 | Internet |
| 1 | Network Access |

From top to bottom:

```text
Application
     ↓
Transport
     ↓
Internet
     ↓
Network Access
```

Data moves down this stack when being sent.

At the destination, it moves back upward.

---

# 🔄 TCP/IP vs. OSI

The OSI model uses:

> **7 layers**

The TCP/IP model commonly uses:

> **4 layers**

They describe many of the same networking concepts but organize them differently.

---

# 🗺️ Model Comparison

| OSI Model | TCP/IP Model |
|---|---|
| Layer 7 — Application | Application |
| Layer 6 — Presentation | Application |
| Layer 5 — Session | Application |
| Layer 4 — Transport | Transport |
| Layer 3 — Network | Internet |
| Layer 2 — Data Link | Network Access |
| Layer 1 — Physical | Network Access |

Conceptually:

```text
OSI                           TCP/IP

7 Application ───────┐
6 Presentation ──────┼───── Application
5 Session ───────────┘

4 Transport ──────────────── Transport

3 Network ────────────────── Internet

2 Data Link ─────────┐
1 Physical ──────────┴────── Network Access
```

---

# 🧠 Why Learn Both?

You might wonder:

> Why learn OSI if TCP/IP is what networks actually use?

Because the two models are useful in different ways.

The **OSI model** is excellent for:

- Learning concepts
- Troubleshooting
- Discussing technologies by layer
- Certification questions

The **TCP/IP model** is excellent for understanding:

- Real Internet communication
- Modern protocol stacks
- How applications use IP networks

Think of them as:

```text
OSI
=
Teaching and Troubleshooting Framework
```

```text
TCP/IP
=
Practical Internet Protocol Model
```

---

# 🟣 TCP/IP Application Layer

The TCP/IP **Application layer** combines concepts represented by OSI Layers:

```text
7 — Application
6 — Presentation
5 — Session
```

This layer contains protocols used directly by applications and services.

Examples include:

- HTTP
- HTTPS
- DNS
- DHCP
- SSH
- SMTP
- IMAP
- POP3
- FTP
- SNMP
- NTP

---

# 🌎 Application Example

Suppose you open:

```text
https://example.com
```

Your browser is an application.

It may use:

> **HTTPS**

to communicate with a web server.

Conceptually:

```text
Browser
   ↓
HTTPS
   ↓
TCP/IP Stack
```

---

# 🟡 TCP/IP Transport Layer

The Transport layer corresponds closely with:

> **OSI Layer 4**

Two major protocols live here:

```text
TCP
UDP
```

The Transport layer helps applications communicate between systems.

Important concepts include:

- Ports
- Connections
- Segmentation
- Reliability
- Delivery behavior

---

# 🚚 TCP — Transmission Control Protocol

TCP is:

> **Connection-oriented**

and designed for reliable delivery.

TCP can provide mechanisms such as:

- Sequencing
- Acknowledgments
- Retransmission
- Flow control

Conceptually:

```text
Sender
  │
  │ Establish Connection
  ▼
Receiver
  │
  │ Send Data
  ▼
Acknowledgment
```

We'll explore TCP more deeply in Lesson 10.

---

# ⚡ UDP — User Datagram Protocol

UDP is:

> **Connectionless**

It has less overhead than TCP.

UDP doesn't provide the same built-in reliability mechanisms.

Conceptually:

```text
Sender
   │
   ├──── Datagram
   │
   ├──── Datagram
   │
   └──── Datagram
```

The sender doesn't establish a TCP-style connection first.

---

# ⚖️ TCP vs. UDP

| TCP | UDP |
|---|---|
| Connection-oriented | Connectionless |
| Reliable delivery features | No built-in delivery guarantee |
| Sequencing | Lower overhead |
| Acknowledgments | No TCP-style acknowledgments |
| Retransmission | Application may handle loss if needed |
| More overhead | Less overhead |

Neither is simply "better."

The correct choice depends on the application.

---

# 🚪 Ports

The Transport layer also uses:

> **Port Numbers**

Ports help identify application communication endpoints.

Examples:

```text
HTTP   → 80
HTTPS  → 443
SSH    → 22
DNS    → 53
```

Think:

```text
IP Address
=
Which host?
```

```text
Port
=
Which service/application?
```

---

# 🔴 TCP/IP Internet Layer

The TCP/IP Internet layer corresponds closely with:

> **OSI Layer 3 — Network**

This is where:

- IPv4
- IPv6
- IP addressing
- Routing

become important.

---

# 📍 IP Addresses

An IP address identifies a network interface within IP communication.

Examples:

```text
192.168.10.10
```

or:

```text
2001:db8::10
```

IP allows systems to communicate across different networks.

---

# 🚦 Routers Operate Here

Remember:

```text
Office Network
      │
      ▼
    Router
      │
      ▼
Server Network
```

Routers primarily make forwarding decisions using:

> **Layer 3 IP information**

In TCP/IP terminology, this falls within the:

> **Internet layer**

---

# 📦 The IP Packet

The PDU commonly associated with IP is:

> **Packet**

Conceptually:

```text
Application Data
       ↓
TCP Segment
       ↓
IP Packet
```

The IP packet contains information such as:

- Source IP address
- Destination IP address
- Other IP header information

---

# 🔵 TCP/IP Network Access Layer

The Network Access layer combines concepts represented by OSI:

```text
Layer 2 — Data Link
Layer 1 — Physical
```

This layer handles communication over the local network technology.

Examples include:

- Ethernet
- Wi-Fi
- MAC addresses
- Frames
- Network interfaces
- Copper cables
- Fiber
- Radio signals

---

# 🔀 Ethernet

Ethernet is one of the most common local network technologies.

Ethernet communication uses:

> **MAC addresses**

and:

> **Frames**

Remember:

```text
Switch
   ↓
Ethernet
   ↓
MAC Address
   ↓
Frame
```

---

# 📦 Full Encapsulation Process

Suppose an application sends information.

Conceptually:

```text
APPLICATION

Data
  ↓
TRANSPORT

TCP Segment
  ↓
INTERNET

IP Packet
  ↓
NETWORK ACCESS

Ethernet Frame
  ↓
Physical Transmission
```

This is:

> **Encapsulation**

---

# 📭 Decapsulation

At the destination, the process is reversed.

```text
Physical Transmission
        ↓
Ethernet Frame
        ↓
IP Packet
        ↓
TCP Segment
        ↓
Application Data
```

This is:

> **Decapsulation**

---

# 🌐 Following a Complete Communication

Consider this network:

```text
PC-01
192.168.10.10
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
PC-02
192.168.20.10
```

Suppose PC-01 sends application data to PC-02.

---

# 1️⃣ Application Creates Data

An application creates information.

At this stage, think:

> **Application Layer**

---

# 2️⃣ Transport Layer Handles Communication

TCP or UDP may be used.

For example:

```text
TCP
```

The Transport layer may add:

- Source port
- Destination port
- Sequence information
- Other transport information

The result can be thought of as:

> **TCP Segment**

---

# 3️⃣ Internet Layer Adds IP Information

IP adds addressing information.

Conceptually:

```text
Source IP:
192.168.10.10

Destination IP:
192.168.20.10
```

Now we have an:

> **IP Packet**

---

# 4️⃣ Network Access Adds Ethernet Information

Before leaving PC-01 on an Ethernet LAN, the IP packet needs Ethernet information.

The system creates an:

> **Ethernet Frame**

The frame contains MAC addressing appropriate for the local link.

---

# 🚪 Remote Destination

PC-01 recognizes that:

```text
192.168.20.10
```

is not on its local network.

It therefore sends the local Ethernet frame toward:

> **Its Default Gateway**

For example:

```text
192.168.10.1
```

---

# 🗺️ Layer 2 vs. Layer 3 Destination

This is extremely important.

PC-01 wants the **IP packet** to ultimately reach:

```text
192.168.20.10
```

But the first **Ethernet frame** needs to reach the router.

Conceptually:

```text
Layer 3 Destination
=
PC-02
192.168.20.10
```

while:

```text
Layer 2 Local Destination
=
R-01's local MAC address
```

---

# 🔀 SW-01 Receives the Frame

SW-01 examines Layer 2 information.

It primarily cares about:

> **MAC addresses**

The switch forwards the Ethernet frame toward R-01.

It doesn't make the routing decision.

---

# 🚦 R-01 Receives the Packet

R-01 receives the Ethernet frame.

The router removes the local Layer 2 framing and examines:

> **The IP Packet**

It sees:

```text
Destination:
192.168.20.10
```

The router determines where the packet should go next.

---

# 📦 Router Re-Encapsulation

R-01 creates new Layer 2 framing for the next local network.

Conceptually:

```text
Incoming:

Ethernet Frame A
      ↓
IP Packet

Router processes IP packet

Outgoing:

IP Packet
      ↓
Ethernet Frame B
```

The Layer 2 frame changes.

The IP packet continues toward its destination.

---

# 📭 PC-02 Decapsulates the Data

Eventually PC-02 receives the traffic.

It processes:

```text
Ethernet
    ↓
IP
    ↓
TCP/UDP
    ↓
Application
```

The application receives the information.

---

# 🧠 End-to-End vs. Local-Link Delivery

This gives us two useful ways to think about network communication.

## End-to-End

IP is concerned with communication between:

```text
Source Host
     ↓
Destination Host
```

Example:

```text
192.168.10.10
        ↓
192.168.20.10
```

---

## Local-Link Delivery

Ethernet communication occurs across individual local links.

For example:

```text
PC-01
   ↓
R-01
```

then another local-link delivery occurs toward the destination network.

The Ethernet information can change between links.

---

# 🏠 Local Communication

Suppose:

```text
PC-01
192.168.10.10
```

communicates with:

```text
PC-02
192.168.10.20
```

on the same local network.

Traffic may travel:

```text
PC-01
   │
   ▼
Switch
   │
   ▼
PC-02
```

A router isn't required to move that traffic between different IP networks because both hosts are local to one another.

---

# 🌎 Remote Communication

Now PC-01 communicates with:

```text
SRV-01
192.168.20.10
```

on another network.

The path becomes:

```text
PC-01
   │
   ▼
Switch
   │
   ▼
Router
   │
   ▼
Switch
   │
   ▼
SRV-01
```

Routing is required.

---

# 🔎 How Does a Computer Know Local vs. Remote?

The computer uses information including:

- Its own IP address
- Its subnet mask/prefix
- The destination IP address

to determine whether a destination is local or remote.

If local:

```text
Send locally
```

If remote:

```text
Send toward default gateway
```

You'll learn exactly how this works during the IPv4 and subnetting lessons.

---

# 📡 Communication Example — DNS

Suppose you enter:

```text
example.com
```

Your computer may need to ask a DNS server:

> **What IP address belongs to example.com?**

Conceptually:

```text
Application
    ↓
DNS Request
    ↓
Transport
    ↓
IP
    ↓
Ethernet / Wi-Fi
    ↓
Network
```

The response travels back through the stack.

---

# 🌎 Communication Example — HTTPS

After DNS resolution, your browser may communicate using:

```text
HTTPS
```

Conceptually:

```text
Browser
   ↓
HTTPS
   ↓
TCP
   ↓
IP
   ↓
Ethernet / Wi-Fi
   ↓
Network
```

Modern web traffic can also use HTTP/3 over QUIC/UDP, but TCP-based HTTPS remains an important model for learning TCP/IP communication.

---

# 🧠 One Task Can Use Many Protocols

Opening a website may involve technologies such as:

```text
DNS
 ↓
ARP
 ↓
IP
 ↓
TCP or UDP
 ↓
TLS
 ↓
HTTP
```

This is why a simple statement like:

> "The Internet isn't working."

doesn't tell an IT technician where the problem actually exists.

---

# 🛠️ Troubleshooting with TCP/IP

Suppose a user says:

> **The website isn't working.**

You can examine the problem by TCP/IP layer.

---

## 🔵 Network Access

Check:

```text
Is Ethernet connected?

Is Wi-Fi connected?

Does the NIC show link?

Is the switch port operational?
```

---

## 🔴 Internet

Check:

```text
Does the device have an IP address?

Is the subnet information correct?

Is the gateway correct?

Can the device reach the gateway?

Is routing working?
```

---

## 🟡 Transport

Check:

```text
Is the required TCP/UDP port reachable?

Is a firewall blocking it?

Is the remote service listening?
```

---

## 🟣 Application

Check:

```text
Is DNS working?

Is the application running?

Is authentication working?

Is the server responding correctly?
```

---

# 🧠 Troubleshooting Scenario 1

A computer has:

```text
IPv4:
192.168.10.25

Gateway:
192.168.10.1
```

It can ping:

```text
192.168.10.1
```

and:

```text
8.8.8.8
```

but cannot resolve:

```text
example.com
```

What should become particularly interesting?

> **DNS**

Basic IP connectivity appears to be functioning.

---

# 🧠 Troubleshooting Scenario 2

A computer has:

```text
169.254.15.40
```

and no usable default gateway.

Would you begin by troubleshooting HTTPS?

> **No**

You already have evidence of a more fundamental IP configuration problem.

Investigate that first.

---

# 🧠 Troubleshooting Scenario 3

A user can successfully:

```text
ping server
```

but the required web service doesn't respond.

This suggests:

- Basic IP connectivity may exist
- The host may be reachable
- The application/service or required port may need investigation

Remember:

> **One successful network test doesn't prove every layer is working.**

---

# 🔍 Packet Capture

One powerful way to observe TCP/IP communication is to:

> **Capture network traffic**

A protocol analyzer allows you to see communication such as:

```text
Ethernet
ARP
IPv4
IPv6
ICMP
DNS
TCP
UDP
TLS
```

One of the most widely used tools for this is:

> 🦈 **Wireshark**

That's what you'll use in Lab 05.

---

# 🦈 What Is Wireshark?

Wireshark is a:

> **Network Protocol Analyzer**

It allows you to capture and inspect network traffic.

Instead of only seeing:

```text
Browser → Website
```

you may see protocols such as:

```text
Ethernet
   ↓
IPv4
   ↓
TCP
   ↓
TLS
```

or:

```text
Ethernet
   ↓
IPv4
   ↓
UDP
   ↓
DNS
```

This makes otherwise invisible network communication visible.

---

# ⚠️ Packet Capture Safety

Packet captures can expose sensitive information.

Only capture traffic on:

- Networks you own
- Systems you administer
- Networks where you have explicit authorization

Do not capture other users' private traffic without permission.

For this course, Lab 05 focuses on:

> **Your own computer's traffic**

---

# 📋 TCP/IP Quick Reference

| TCP/IP Layer | Common Concepts |
|---|---|
| Application | HTTP, HTTPS, DNS, DHCP, SSH |
| Transport | TCP, UDP, Ports |
| Internet | IPv4, IPv6, Routing |
| Network Access | Ethernet, Wi-Fi, MAC, Frames, Physical media |

---

# 🗺️ OSI and TCP/IP Quick Reference

```text
OSI                         TCP/IP

7 Application ───────┐
6 Presentation ──────┼──── Application
5 Session ───────────┘

4 Transport ─────────────── Transport

3 Network ───────────────── Internet

2 Data Link ─────────┐
1 Physical ──────────┴───── Network Access
```

---

# 📦 Encapsulation Quick Reference

```text
Application
    DATA
      ↓
Transport
    SEGMENT / DATAGRAM
      ↓
Internet
    PACKET
      ↓
Network Access
    FRAME
      ↓
Physical Transmission
```

---

# 🧠 Knowledge Check

Try answering these before looking at the answers.

### 1.

How many layers are commonly used in the TCP/IP model?

### 2.

Which TCP/IP layer contains TCP and UDP?

### 3.

Which TCP/IP layer contains IP and routing?

### 4.

Which TCP/IP layer includes Ethernet and Wi-Fi?

### 5.

Which TCP/IP layer includes protocols such as HTTP and DNS?

### 6.

Which protocol is connection-oriented: TCP or UDP?

### 7.

What does an IP address help identify?

### 8.

What does a port help identify?

### 9.

What is encapsulation?

### 10.

What is decapsulation?

---

# ✅ Knowledge Check Answers

### 1.

**Four**

### 2.

**Transport**

### 3.

**Internet**

### 4.

**Network Access**

### 5.

**Application**

### 6.

**TCP**

### 7.

A network interface/endpoint within IP communication.

### 8.

An application or service communication endpoint.

### 9.

Adding protocol information as data moves down the networking stack for transmission.

### 10.

Processing protocol information as received data moves back up the networking stack.

---

# 🎓 Network+ Challenge 1

Which TCP/IP layer corresponds most closely with OSI Layer 3?

### A. Application

### B. Transport

### C. Internet

### D. Network Access

Answer:

> **C — Internet**

---

# 🎓 Network+ Challenge 2

A switch forwards Ethernet traffic using MAC addresses.

Which TCP/IP layer is primarily involved?

### A. Application

### B. Transport

### C. Internet

### D. Network Access

Answer:

> **D — Network Access**

---

# 🎓 Network+ Challenge 3

Which protocol provides connection-oriented, reliable communication?

### A. IP

### B. UDP

### C. TCP

### D. Ethernet

Answer:

> **C — TCP**

---

# 🎓 Network+ Challenge 4

A computer can communicate with its default gateway but cannot reach a remote IPv4 network.

Which TCP/IP layer should become particularly interesting?

### A. Application

### B. Transport

### C. Internet

### D. Network Access only

Answer:

> **C — Internet**

Routing and Layer 3 connectivity should be investigated.

---

# 🎓 Network+ Challenge 5

A web server's IP address responds to ping, but TCP port 443 is unavailable.

Which layer should you investigate closely?

### A. Network Access

### B. Internet

### C. Transport

### D. Physical only

Answer:

> **C — Transport**

The IP path may be functioning, but the required TCP service or path to the port still needs investigation.

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- TCP/IP is the protocol suite used by modern IP networks.
- A common TCP/IP model contains four layers.
- The Application layer contains application protocols.
- The Transport layer contains TCP and UDP.
- The Internet layer contains IP and routing.
- The Network Access layer includes Ethernet and Wi-Fi.
- TCP provides connection-oriented communication and reliability mechanisms.
- UDP provides connectionless communication with less protocol overhead.
- IP addresses provide logical addressing.
- Ports help identify application/service communication.
- Ethernet provides local-link delivery.
- Switches primarily forward Ethernet frames.
- Routers forward IP packets between networks.
- Encapsulation prepares data for transmission.
- Decapsulation processes received data at the destination.
- Local communication doesn't necessarily require a router.
- Remote network communication normally uses a default gateway.
- The TCP/IP model provides a useful troubleshooting framework.

---

# 🌐 Cisco Companion

Cisco Packet Tracer has helped you visualize network communication through simulation.

➡️ **[Cisco Networking Companion](../resources/cisco-companion.md)**

From this point forward, the course will increasingly combine:

```text
Packet Tracer
+
Real Windows Networking
+
PowerShell
+
Wireshark
```

This allows you to compare simulated networking with real network behavior.

---

# 🛠️ Project Progress

You're almost ready for:

> 🚀 **Project 01 — Build Your First Network**

You've now completed the five foundational lesson topics:

```text
Lesson 01
Networking Basics
      ↓
Lesson 02
Network Types & Topologies
      ↓
Lesson 03
Network Devices
      ↓
Lesson 04
OSI Model
      ↓
Lesson 05
TCP/IP & Network Communication
```

After Lab 05, you'll apply these concepts in your first larger project.

---

# 🎥 Optional Video Resource

For additional Network+ reinforcement:

### Professor Messer — Network+ N10-009 Training

➡️ [Professor Messer — N10-009 Training Course](https://www.professormesser.com/network-plus/n10-009/n10-009-video/n10-009-training-course/)

> ⭐ **Optional**
>
> Use Professor Messer as additional exam-focused reinforcement.
>
> Focus on understanding how network communication moves through the protocol stack rather than simply memorizing layer names.

---

# 🧪 Next Step — Complete Lab 05

Now you're going to move from:

> **Learning about packets**

to:

> **Inspecting real packets**

Lab 05 introduces **Wireshark** and lets you capture traffic generated by your own Windows computer.

You'll observe:

- Network interfaces
- Ethernet
- IPv4
- ICMP
- DNS
- TCP
- UDP
- Ports
- Source and destination addresses
- Encapsulation in real traffic

➡️ **[Lab 05 — TCP/IP & Wireshark Introduction](../labs/lab-05-tcp-ip-wireshark.md)**

---

# 📍 Course Progress

```text
✅ Lesson 01 — Networking Basics
        ↓
✅ Lab 01
        ↓
✅ Lesson 02 — Network Types & Topologies
        ↓
✅ Lab 02
        ↓
✅ Lesson 03 — Network Devices
        ↓
✅ Lab 03
        ↓
✅ Lesson 04 — The OSI Model
        ↓
✅ Lab 04
        ↓
✅ Lesson 05 — TCP/IP & Network Communication
        ↓
🟡 NEXT: Lab 05 — TCP/IP & Wireshark
        ↓
🚀 Project 01 — Build Your First Network
        ↓
⬜ Lesson 06 — Ethernet & MAC Addressing
```

---

# ➡️ After the Lab

After Lab 05, complete:

> 🚀 **Project 01 — Build Your First Network**

That project brings together:

- Network diagrams
- Topologies
- Network devices
- Switching
- Routing
- IPv4
- Default gateways
- OSI
- TCP/IP
- Connectivity testing
- Troubleshooting

After Project 01, you'll begin:

> 🔵 **Phase 2 — Addressing & Communication**

with:

> **📘 Lesson 06 — Ethernet and MAC Addressing**

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Cisco Networking Companion](../resources/cisco-companion.md)**

➡️ **[Return to Main README](../README.md)**
