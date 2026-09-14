# 📘 Lesson 04 — The OSI Model

Welcome to **Lesson 04 of Networking Fundamentals**.

So far, you've learned:

- What networks are
- Network types and topologies
- Common network devices
- How switches connect devices
- How routers connect networks
- How wireless access points connect wireless clients
- How to build basic networks in Cisco Packet Tracer

You've also encountered terms such as:

```text
Ethernet
MAC Address
IP Address
Frame
Packet
Switch
Router
Port
Cable
```

Now we're going to organize those concepts using one of the most important models in networking:

> **The OSI Model**

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Name the seven OSI layers
- Describe the basic function of each layer
- Identify common protocols and technologies associated with each layer
- Explain encapsulation
- Explain decapsulation
- Understand Protocol Data Units
- Explain why switches are associated with Layer 2
- Explain why routers are associated with Layer 3
- Understand the role of TCP and UDP at Layer 4
- Understand how applications interact with networking
- Use the OSI model as a troubleshooting framework
- Recognize common Network+ OSI scenarios

---

# 🎓 Network+ Focus

The OSI model is important for **CompTIA Network+ N10-009**.

You should understand:

- The seven layers
- What happens at each layer
- Which devices operate at particular layers
- MAC addresses vs. IP addresses
- Frames vs. packets
- TCP and UDP
- Encapsulation and decapsulation
- Troubleshooting by layer

Don't memorize only:

```text
7
6
5
4
3
2
1
```

Understand what each layer represents.

---

# 🧱 The Seven OSI Layers

The OSI model contains seven layers:

| Layer | Name |
|---:|---|
| 7 | Application |
| 6 | Presentation |
| 5 | Session |
| 4 | Transport |
| 3 | Network |
| 2 | Data Link |
| 1 | Physical |

From top to bottom:

```text
7 — Application
        ↓
6 — Presentation
        ↓
5 — Session
        ↓
4 — Transport
        ↓
3 — Network
        ↓
2 — Data Link
        ↓
1 — Physical
```

When receiving data, you can think about the process in the opposite direction:

```text
1 — Physical
        ↓
2 — Data Link
        ↓
3 — Network
        ↓
4 — Transport
        ↓
5 — Session
        ↓
6 — Presentation
        ↓
7 — Application
```

---

# 🧠 Why Does the OSI Model Exist?

Networks contain many different technologies.

The OSI model gives us a framework for understanding how those technologies interact.

Instead of viewing networking as one giant process:

```text
Computer
   ↓
???
   ↓
Internet
```

we can divide communication into layers:

```text
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

Each layer has responsibilities.

---

# 🟣 Layer 7 — Application

Layer 7 is:

> **Application**

This is the layer closest to the user and software applications.

Common protocols associated with the application layer include:

- HTTP
- HTTPS
- DNS
- DHCP
- FTP
- SMTP
- IMAP
- POP3
- SSH
- SNMP

Example:

```text
Web Browser
    ↓
HTTPS
    ↓
Network Communication
```

When you open a website, the browser uses application-layer protocols to communicate.

---

# 🧠 Layer 7 Troubleshooting

Examples of Layer 7 problems might include:

- Website service unavailable
- DNS application service failure
- Authentication problems
- Incorrect application configuration
- Server application not responding

Suppose:

```text
ping server
```

works, but the website hosted on that server doesn't.

That tells you something important:

> Basic network connectivity may exist even though the application service is failing.

---

# 🔵 Layer 6 — Presentation

Layer 6 is:

> **Presentation**

This layer deals conceptually with how data is represented.

Responsibilities can include:

- Data formatting
- Encoding
- Encryption
- Decryption
- Compression
- Decompression

Think:

> **How should the data be represented?**

Examples may involve:

```text
Encryption
Character Encoding
Data Formats
Compression
```

---

# 🧠 Presentation Example

Imagine sending:

```text
Hello
```

The receiving system needs to interpret those bytes correctly.

Presentation-related functions help systems agree on how information should be represented.

Encryption can also transform:

```text
Readable Data
      ↓
Encrypted Data
      ↓
Transmission
```

The receiving side can reverse the process.

---

# 🟢 Layer 5 — Session

Layer 5 is:

> **Session**

This layer conceptually manages communication sessions between systems.

Responsibilities can include:

- Establishing sessions
- Maintaining sessions
- Managing dialogs
- Ending sessions

Think:

> **Managing the conversation**

Conceptually:

```text
Start Session
     ↓
Communicate
     ↓
Maintain Session
     ↓
End Session
```

In real modern networking stacks, the boundaries between Layers 5–7 are not always as clean as the model suggests.

That's okay.

Remember that the OSI model is primarily a:

> **Conceptual framework**

---

# 🟡 Layer 4 — Transport

Layer 4 is:

> **Transport**

Two extremely important protocols operate here:

```text
TCP
UDP
```

Layer 4 deals with communication between applications across hosts.

Concepts include:

- Segmentation
- Reliability
- Flow control
- Error recovery
- Ports
- Connection-oriented communication
- Connectionless communication

---

# 🚚 TCP

TCP stands for:

> **Transmission Control Protocol**

TCP provides reliable, connection-oriented communication.

Conceptually:

```text
Establish Connection
        ↓
Send Data
        ↓
Confirm Delivery
        ↓
Retransmit if Needed
```

You'll study TCP in much greater detail later.

---

# ⚡ UDP

UDP stands for:

> **User Datagram Protocol**

UDP is connectionless and has less overhead than TCP.

Conceptually:

```text
Send Data
   ↓
Continue
```

UDP doesn't provide TCP's built-in delivery guarantees.

That can make it useful for applications where speed and low overhead are important.

---

# 🚪 Layer 4 Ports

Layer 4 also introduces:

> **Port Numbers**

Examples include:

```text
HTTP   80
HTTPS  443
SSH    22
DNS    53
```

Think of an IP address as helping identify the host and a port as helping identify the service/application communication endpoint.

We'll cover ports extensively in:

> **Lesson 10 — TCP, UDP, Ports, and Protocols**

---

# 🔴 Layer 3 — Network

Layer 3 is:

> **Network**

This layer is where:

> **IP addressing and routing**

become extremely important.

Examples include:

- IPv4
- IPv6
- Routing
- Routers
- Logical addressing

Remember your Lab 03 network:

```text
192.168.10.0/24
       │
       ▼
      R-01
       │
       ▼
192.168.20.0/24
```

R-01 moved traffic between different IP networks.

That's a:

> **Layer 3 function**

---

# 🚦 Routers and Layer 3

A router examines Layer 3 addressing information and determines where traffic should go.

Remember:

```text
Router
   ↓
Layer 3
   ↓
IP Addresses
   ↓
Routing
```

This is one of the most important associations to remember.

---

# 📦 Layer 3 PDU — Packet

The Protocol Data Unit commonly associated with Layer 3 is:

> **Packet**

So:

```text
Layer 3
   ↓
Packet
```

You'll frequently hear:

> **IP packet**

---

# 🔵 Layer 2 — Data Link

Layer 2 is:

> **Data Link**

This layer is heavily associated with:

- Ethernet
- MAC addresses
- Ethernet frames
- Switches
- VLANs
- Local network delivery

Remember:

```text
Switch
   ↓
Layer 2
   ↓
MAC Addresses
```

---

# 🔀 Switches and Layer 2

A traditional Ethernet switch learns which MAC addresses are reachable through its ports.

Conceptually:

```text
MAC A → Port 1

MAC B → Port 2

MAC C → Port 3
```

The switch uses that information when forwarding Ethernet frames.

---

# 📦 Layer 2 PDU — Frame

The PDU commonly associated with Layer 2 is:

> **Frame**

Specifically, with Ethernet:

> **Ethernet Frame**

So:

```text
Layer 2
   ↓
Frame
```

---

# ⚫ Layer 1 — Physical

Layer 1 is:

> **Physical**

This layer deals with transmitting bits through physical or radio media.

Examples include:

- Copper cabling
- Fiber
- Radio signals
- Connectors
- Electrical signals
- Optical signals
- Physical interfaces
- Network transceivers

Think:

```text
Bits
 ↓
Signal
 ↓
Medium
```

---

# 🔌 Layer 1 Troubleshooting

Layer 1 is a very useful troubleshooting starting point.

Questions include:

```text
Is the cable connected?

Is the port active?

Does the NIC have link?

Is the fiber connected correctly?

Does the device have power?

Is the wireless signal available?
```

Sometimes the most complicated-looking network problem is simply:

> **A disconnected cable**

---

# 🧱 OSI Model Summary

| Layer | Name | Examples |
|---:|---|---|
| 7 | Application | HTTP, HTTPS, DNS, DHCP, SMTP |
| 6 | Presentation | Encoding, encryption, compression |
| 5 | Session | Session establishment and management |
| 4 | Transport | TCP, UDP, ports |
| 3 | Network | IP, routing, routers |
| 2 | Data Link | Ethernet, MAC addresses, switches |
| 1 | Physical | Cable, fiber, radio, signals |

---

# 📦 Protocol Data Units — PDUs

As data moves through the networking stack, different names are commonly used.

| OSI Layer | PDU |
|---|---|
| 7–5 | Data |
| 4 | Segment / Datagram |
| 3 | Packet |
| 2 | Frame |
| 1 | Bits |

A useful sequence is:

```text
Data
 ↓
Segment
 ↓
Packet
 ↓
Frame
 ↓
Bits
```

---

# 🧠 TCP vs. UDP PDU

At Layer 4:

TCP commonly uses:

> **Segment**

UDP commonly uses:

> **Datagram**

So you may see:

```text
TCP Segment

UDP Datagram
```

---

# 📦 Encapsulation

When a computer sends data, information is added as the data moves down the networking stack.

This is called:

> **Encapsulation**

Conceptually:

```text
Application Data
       ↓
Transport Header Added
       ↓
Network Header Added
       ↓
Data Link Header/Trailer Added
       ↓
Bits Transmitted
```

Or:

```text
DATA
 ↓
SEGMENT
 ↓
PACKET
 ↓
FRAME
 ↓
BITS
```

---

# 📬 Think of Shipping a Package

Imagine mailing an item.

You start with:

```text
Item
```

Then place it inside:

```text
Box
```

Then add:

```text
Address Label
```

Then the shipping system moves it toward the destination.

Networking does something conceptually similar.

Each layer adds information needed for communication.

---

# 📭 Decapsulation

The receiving device reverses the process.

This is:

> **Decapsulation**

Conceptually:

```text
Bits Received
      ↓
Frame Processed
      ↓
Packet Processed
      ↓
Segment Processed
      ↓
Application Data
```

So:

```text
Sender
ENCAPSULATES
     ↓
Network
     ↓
Receiver
DECAPSULATES
```

---

# 🌐 Example — Opening a Website

Suppose:

```text
PC-01
```

opens a website on:

```text
SRV-01
```

Conceptually:

```text
Browser
   ↓
Application Data
   ↓
TCP
   ↓
IP
   ↓
Ethernet
   ↓
Physical Network
```

Traffic travels through the network.

At the server:

```text
Physical Network
       ↓
Ethernet
       ↓
IP
       ↓
TCP
       ↓
Web Application
```

---

# 🗺️ Following Traffic Through the Network

Consider:

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

Different devices care about different information.

---

## PC-01

Uses the networking stack to create and encapsulate data.

---

## SW-01

Primarily examines Layer 2 information:

> **MAC addresses**

---

## R-01

Primarily examines Layer 3 information:

> **IP addresses**

---

## SW-02

Again uses Layer 2 forwarding.

---

## SRV-01

Receives and decapsulates the communication.

---

# 🔀 Switch vs. Router — OSI View

This should now make more sense:

```text
SWITCH
   ↓
Layer 2
   ↓
MAC Address
   ↓
Frame
```

while:

```text
ROUTER
   ↓
Layer 3
   ↓
IP Address
   ↓
Packet
```

That's why understanding the OSI model helps you understand network devices.

---

# 🛠️ OSI as a Troubleshooting Tool

The OSI model isn't just something to memorize for exams.

It can help organize troubleshooting.

Suppose a user says:

> **"The Internet doesn't work."**

That's not enough information.

Start investigating.

---

# 1️⃣ Layer 1 — Physical

Ask:

```text
Is the device powered on?

Is the Ethernet cable connected?

Does the NIC show link?

Is Wi-Fi enabled?

Is the switch port active?
```

---

# 2️⃣ Layer 2 — Data Link

Investigate:

```text
Is the switch port correct?

Is the VLAN correct?

Is the MAC address being learned?

Is Ethernet functioning?
```

---

# 3️⃣ Layer 3 — Network

Investigate:

```text
Does the device have an IP address?

Is the subnet mask correct?

Is the default gateway correct?

Can it reach the gateway?

Is routing functioning?
```

---

# 4️⃣ Layer 4 — Transport

Investigate:

```text
Is the required TCP/UDP port reachable?

Is a firewall blocking the port?

Is the service listening?
```

---

# 5️⃣–7️⃣ Upper Layers

Investigate:

```text
Is the application running?

Is authentication working?

Is encryption working?

Is the service configured correctly?
```

---

# 🧠 Troubleshooting Example

A user's PC shows:

```text
No link light
```

Which layer should immediately become interesting?

> **Layer 1 — Physical**

---

Another user can:

```text
ping 8.8.8.8
```

but cannot browse to a website by name.

Physical connectivity clearly exists.

IP connectivity may exist.

Now you might investigate:

> **DNS / upper-layer services**

instead of replacing the Ethernet cable.

---

# 🔍 Bottom-Up Troubleshooting

One troubleshooting approach is:

```text
Layer 1
   ↓
Layer 2
   ↓
Layer 3
   ↓
Layer 4
   ↓
Layers 5–7
```

Start with physical connectivity and move upward.

This is called:

> **Bottom-Up Troubleshooting**

---

# 🔍 Top-Down Troubleshooting

You can also start with the application:

```text
Layer 7
   ↓
Layer 6
   ↓
Layer 5
   ↓
Layer 4
   ↓
Layer 3
   ↓
Layer 2
   ↓
Layer 1
```

This is:

> **Top-Down Troubleshooting**

Which approach is best depends on the problem.

---

# 🔍 Divide and Conquer

Another method is to start somewhere in the middle.

For example:

```text
Can I ping the default gateway?
```

If yes, several lower-layer functions are probably working.

You can then focus farther up or farther along the network path.

This is often called:

> **Divide and Conquer**

---

# 🧠 Don't Treat the OSI Model Too Literally

Real networking doesn't always fit perfectly into seven isolated boxes.

Protocols and technologies can cross conceptual boundaries.

Layers 5–7 especially are often combined in real-world protocol stacks.

The OSI model is valuable because it gives us:

```text
Common Language
      +
Troubleshooting Framework
      +
Conceptual Organization
```

not because every technology perfectly fits into one box.

---

# 🧠 OSI Memory Aid

A traditional mnemonic from Layer 7 down to Layer 1 is:

> **All People Seem To Need Data Processing**

```text
All          Application
People       Presentation
Seem         Session
To           Transport
Need         Network
Data         Data Link
Processing   Physical
```

Or create your own.

The best mnemonic is the one you actually remember.

---

# 🎓 Network+ Exam Tip

Don't stop at memorizing the layer number.

Associate the concepts:

```text
Layer 1
Physical
Cable / Signal / Bits
```

```text
Layer 2
Data Link
MAC / Switch / Frame
```

```text
Layer 3
Network
IP / Router / Packet
```

```text
Layer 4
Transport
TCP / UDP / Ports
```

These four associations are especially important.

---

# 🧠 Knowledge Check

### 1.

Which OSI layer is associated with physical cabling?

### 2.

Which layer is associated with MAC addresses?

### 3.

Which layer is associated with IP addresses?

### 4.

Which layer contains TCP and UDP?

### 5.

Which layer is closest to the end-user application?

### 6.

What is the Layer 2 PDU?

### 7.

What is the Layer 3 PDU?

### 8.

What is a TCP Layer 4 PDU commonly called?

### 9.

What process adds networking information as data moves down the stack?

### 10.

What process removes that information at the destination?

---

# ✅ Knowledge Check Answers

### 1.

**Layer 1 — Physical**

### 2.

**Layer 2 — Data Link**

### 3.

**Layer 3 — Network**

### 4.

**Layer 4 — Transport**

### 5.

**Layer 7 — Application**

### 6.

**Frame**

### 7.

**Packet**

### 8.

**Segment**

### 9.

**Encapsulation**

### 10.

**Decapsulation**

---

# 🎓 Network+ Challenge 1

A technician discovers that a user's Ethernet cable is damaged.

Which OSI layer is primarily affected?

### A. Layer 1

### B. Layer 2

### C. Layer 3

### D. Layer 7

Answer:

> **A — Layer 1**

---

# 🎓 Network+ Challenge 2

A switch is forwarding Ethernet traffic based on MAC addresses.

Which layer is primarily involved?

### A. Layer 1

### B. Layer 2

### C. Layer 3

### D. Layer 4

Answer:

> **B — Layer 2**

---

# 🎓 Network+ Challenge 3

A router is deciding where to send an IPv4 packet.

Which layer is primarily involved?

### A. Physical

### B. Data Link

### C. Network

### D. Application

Answer:

> **C — Network**

---

# 🎓 Network+ Challenge 4

A firewall rule blocks TCP port 443.

Which OSI layer is most directly associated with the TCP port number?

### A. Layer 1

### B. Layer 2

### C. Layer 3

### D. Layer 4

Answer:

> **D — Layer 4**

---

# 📝 Key Takeaways

Make sure you understand:

- The OSI model contains seven layers.
- Layer 7 is Application.
- Layer 6 is Presentation.
- Layer 5 is Session.
- Layer 4 is Transport.
- Layer 3 is Network.
- Layer 2 is Data Link.
- Layer 1 is Physical.
- TCP and UDP operate at Layer 4.
- IP addressing and routing are Layer 3 concepts.
- MAC addresses and Ethernet switching are Layer 2 concepts.
- Cabling and signals are Layer 1 concepts.
- Frames are associated with Layer 2.
- Packets are associated with Layer 3.
- TCP segments and UDP datagrams are associated with Layer 4.
- Encapsulation happens as data moves down the stack.
- Decapsulation happens as data moves up the receiving stack.
- The OSI model is useful for troubleshooting.

---

# 🧪 Next Step — Lab 04

Now you're going to **watch these concepts happen**.

In Lab 04, you'll use:

> **Cisco Packet Tracer Simulation Mode**

to inspect network communication.

You'll observe:

- Ethernet
- MAC addresses
- IP addresses
- ICMP
- Frames
- Packets
- Switch forwarding
- Router forwarding
- Encapsulation concepts
- Decapsulation concepts

➡️ **[Lab 04 — OSI Model & Packet Simulation](../labs/lab-04-osi-model.md)**

---

# 📍 Course Progress

```text
✅ Lesson 01
        ↓
✅ Lab 01
        ↓
✅ Lesson 02
        ↓
✅ Lab 02
        ↓
✅ Lesson 03
        ↓
✅ Lab 03
        ↓
✅ Lesson 04 — The OSI Model
        ↓
🟡 NEXT: Lab 04 — OSI Model & Packet Simulation
        ↓
⬜ Lesson 05 — TCP/IP & Network Communication
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Cisco Networking Companion](../resources/cisco-companion.md)**

➡️ **[Return to Main README](../README.md)**