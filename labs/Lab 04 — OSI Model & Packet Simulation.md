# 🧪 Lab 04 — OSI Model & Packet Simulation

Welcome to **Lab 04 of Networking Fundamentals**.

In Lesson 04, you learned the seven layers of the OSI model.

Now you're going to use **Cisco Packet Tracer Simulation Mode** to see several of those concepts in action.

Instead of simply memorizing:

```text
Layer 3 = IP
Layer 2 = MAC
Layer 1 = Physical
```

you're going to inspect simulated network traffic and see how devices use that information.

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Build a small routed network
- Identify Layer 1 connectivity
- Identify Layer 2 Ethernet information
- Identify Layer 3 IP information
- Generate ICMP traffic
- Use Packet Tracer Simulation Mode
- Follow traffic through switches and routers
- Inspect Packet Tracer PDU information
- Recognize encapsulation
- Recognize decapsulation
- Understand why Layer 2 information changes across routed links
- Understand why Layer 3 addressing identifies end hosts
- Use the OSI model during troubleshooting

---

# 🎓 Network+ Focus

This lab reinforces:

- OSI model
- Layer 1
- Layer 2
- Layer 3
- Ethernet
- MAC addressing
- IPv4
- Routers
- Switches
- Frames
- Packets
- ICMP
- Encapsulation
- Troubleshooting methodology

---

# ⏱️ Estimated Time

Approximately:

**45–60 minutes**

---

# 🗺️ Lab Topology

Build:

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

R-01 will connect:

```text
192.168.10.0/24
```

and:

```text
192.168.20.0/24
```

---

# 🌐 Part 1 — Create a New Packet Tracer Project

Open:

**Cisco Packet Tracer**

Create a new blank project.

---

# 🖥️ Part 2 — Add the Endpoints

Add two PCs.

Rename:

```text
PC-01
PC-02
```

Place PC-01 on the left and PC-02 on the right.

---

# 🔀 Part 3 — Add the Switches

Add two 2960 switches.

Rename:

```text
SW-01
SW-02
```

Arrange:

```text
PC-01 ─── SW-01

SW-02 ─── PC-02
```

---

# 🚦 Part 4 — Add the Router

Add a router with at least two Ethernet interfaces.

Rename:

```text
R-01
```

Place it between the switches:

```text
PC-01 ─── SW-01 ─── R-01 ─── SW-02 ─── PC-02
```

---

# 🔌 Part 5 — Connect the Network

Use appropriate Ethernet connections.

Connect:

```text
PC-01
  ↓
SW-01
```

```text
SW-01
  ↓
R-01
```

```text
R-01
  ↓
SW-02
```

```text
SW-02
  ↓
PC-02
```

Wait for the links to become operational.

---

# 1️⃣ OSI CHECKPOINT — LAYER 1

Before configuring any IP addresses, you've already created:

> **Layer 1 connectivity**

You have:

- Network interfaces
- Ethernet connections
- Switch ports
- Router interfaces
- Physical/link connectivity

Ask:

### Are all links connected?

```text
YES / NO
```

### Are the interfaces operational?

```text
YES / NO
```

If not, fix Layer 1 before continuing.

---

# 📍 Part 6 — Configure R-01

Configure the interface toward SW-01:

```text
IP Address:
192.168.10.1

Subnet Mask:
255.255.255.0
```

Enable the interface.

Configure the interface toward SW-02:

```text
IP Address:
192.168.20.1

Subnet Mask:
255.255.255.0
```

Enable the interface.

---

# 🖥️ Part 7 — Configure PC-01

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

# 🖥️ Part 8 — Configure PC-02

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

# 3️⃣ OSI CHECKPOINT — LAYER 3

You now have Layer 3 addressing.

```text
PC-01
192.168.10.10
       │
       ▼
192.168.10.1
     R-01
192.168.20.1
       │
       ▼
PC-02
192.168.20.10
```

Answer:

### PC-01 IPv4 address:

```text
____________________________
```

### PC-01 default gateway:

```text
____________________________
```

### PC-02 IPv4 address:

```text
____________________________
```

### PC-02 default gateway:

```text
____________________________
```

---

# 📡 Part 9 — Verify Connectivity

On PC-01 open:

**Desktop → Command Prompt**

Run:

```cmd
ping 192.168.20.10
```

If the first attempt has a timeout, try again.

Record:

```text
PC-01 → PC-02

PASS / FAIL
```

Do not continue until the ping succeeds.

---

# 🔍 Part 10 — Switch to Simulation Mode

Switch from:

> **Realtime**

to:

> **Simulation**

This is where the lab becomes interesting.

Packet Tracer can now show network events as they occur.

---

# 🧹 Part 11 — Filter the Traffic

Simulation Mode may display many protocols.

If your Packet Tracer version provides event filters, focus primarily on:

> **ICMP**

You may also see:

> **ARP**

ARP is important and we'll study it more later.

For now, don't worry if ARP traffic appears before ICMP.

---

# ✉️ Part 12 — Create an ICMP Packet

Use:

> **Add Simple PDU**

Select:

```text
PC-01
```

then:

```text
PC-02
```

You've created a simulated ping.

---

# ▶️ Part 13 — Advance One Event at a Time

Use:

> **Capture/Forward**

or the equivalent control in your Packet Tracer version.

Do not immediately run the entire simulation.

Advance it slowly.

Watch the packet move:

```text
PC-01
  ↓
SW-01
  ↓
R-01
  ↓
SW-02
  ↓
PC-02
```

---

# 🔵 Part 14 — Observe SW-01

When the traffic reaches SW-01, inspect the event/PDU information if available.

Look for information associated with:

> **Ethernet**

and:

> **MAC addresses**

Remember:

```text
SWITCH
   ↓
LAYER 2
   ↓
MAC ADDRESS
   ↓
FRAME
```

---

# 📝 Layer 2 Observation

What device are you examining?

```text
____________________________
```

Which OSI layer is primarily associated with Ethernet switching?

```text
____________________________
```

What type of address is important here?

```text
____________________________
```

What is the Layer 2 PDU called?

```text
____________________________
```

---

# 🔴 Part 15 — Observe R-01

Advance the simulation until traffic reaches:

```text
R-01
```

Inspect the PDU/event information.

Look for IPv4 information.

You should see addressing involving:

```text
192.168.10.10
```

and:

```text
192.168.20.10
```

Remember:

```text
ROUTER
   ↓
LAYER 3
   ↓
IP ADDRESS
   ↓
PACKET
```

---

# 📝 Layer 3 Observation

Which device are you examining?

```text
____________________________
```

Which OSI layer is primarily associated with routing?

```text
____________________________
```

What type of address is important?

```text
____________________________
```

What is the Layer 3 PDU called?

```text
____________________________
```

---

# 🧠 Part 16 — Source and Destination IP

Write down:

### Source IPv4 Address

```text
____________________________
```

### Destination IPv4 Address

```text
____________________________
```

For our ping, you should observe:

```text
Source:
192.168.10.10

Destination:
192.168.20.10
```

These identify the communicating endpoints at Layer 3.

---

# 🔎 Part 17 — Look at Layer 2 Addresses

Now inspect the Layer 2 information at different points in the path.

You may notice something important:

> **The Layer 2 source and destination information can change as traffic crosses routed network segments.**

Why?

Because Ethernet frames are used for delivery on each local link.

Conceptually:

```text
PC-01
   │
   │ Ethernet Frame #1
   ▼
R-01
   │
   │ Ethernet Frame #2
   ▼
PC-02
```

The router removes the incoming Layer 2 frame, processes the Layer 3 packet, and builds a new Layer 2 frame for the next network.

---

# 🧠 Very Important Concept

The IP communication is conceptually:

```text
192.168.10.10
       ↓
192.168.20.10
```

But the Ethernet delivery changes from link to link.

This is why:

```text
IP Address
=
Layer 3 logical addressing
```

while:

```text
MAC Address
=
Layer 2 local-link addressing
```

You'll explore this much more in later lessons.

---

# 📦 Part 18 — Encapsulation at PC-01

When PC-01 sends communication, think:

```text
Application/Data
       ↓
Layer 4 Information
       ↓
Layer 3 IP Information
       ↓
Layer 2 Ethernet Information
       ↓
Layer 1 Transmission
```

This process is:

> **Encapsulation**

Conceptually:

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

For this ICMP exercise, don't worry if Packet Tracer doesn't show a TCP/UDP segment—ICMP is carried directly using IP rather than TCP or UDP.

The important point is that multiple layers of information are involved.

---

# 📭 Part 19 — Decapsulation at PC-02

When PC-02 receives the communication, the process is reversed.

```text
BITS
 ↓
FRAME
 ↓
PACKET
 ↓
DATA
```

This is:

> **Decapsulation**

The destination processes the information and generates a reply.

---

# 🔄 Part 20 — Watch the Reply

Continue advancing the simulation.

PC-02 should generate an ICMP response.

Watch it travel back:

```text
PC-02
  ↓
SW-02
  ↓
R-01
  ↓
SW-01
  ↓
PC-01
```

This time:

```text
Source IP:
192.168.20.10
```

and:

```text
Destination IP:
192.168.10.10
```

---

# 🧠 Part 21 — Complete the OSI Map

Fill in:

| Layer | Name | What You Observed |
|---:|---|---|
| 7 | __________ | Application/Data |
| 6 | __________ | Data representation concept |
| 5 | __________ | Session concept |
| 4 | __________ | Transport concept |
| 3 | __________ | IP / Router |
| 2 | __________ | Ethernet / MAC / Switch |
| 1 | __________ | Interfaces / Connections |

---

# 🧪 Part 22 — Break Layer 1

Return to:

> **Realtime Mode**

Disconnect the cable between:

```text
PC-01
```

and:

```text
SW-01
```

Try:

```cmd
ping 192.168.20.10
```

Record:

```text
PASS / FAIL
```

Which OSI layer did you intentionally break?

```text
____________________________
```

Answer:

> **Layer 1 — Physical**

---

# 🔧 Part 23 — Repair Layer 1

Reconnect the cable.

Wait for the link to become operational.

Ping again:

```cmd
ping 192.168.20.10
```

Verify connectivity.

---

# 🧪 Part 24 — Break Layer 3

Now change PC-01's default gateway from:

```text
192.168.10.1
```

to an incorrect address such as:

```text
192.168.10.254
```

Keep the cable connected.

Test:

```cmd
ping 192.168.20.10
```

Record:

```text
PASS / FAIL
```

---

# 🧠 What's Different?

Layer 1 still works.

The cable is connected.

The switch connection works.

But the Layer 3 configuration is incorrect.

Which layer should you investigate?

> **Layer 3 — Network**

---

# 🔧 Part 25 — Repair Layer 3

Restore:

```text
Default Gateway:
192.168.10.1
```

Test again:

```cmd
ping 192.168.20.10
```

Verify:

```text
PASS
```

---

# 🧪 Part 26 — Compare the Failures

### Failure A

```text
Cable Disconnected
```

Primary layer:

```text
Layer 1
```

### Failure B

```text
Incorrect Default Gateway
```

Primary layer:

```text
Layer 3
```

Both failures may result in:

> **"The network doesn't work."**

But the causes exist at completely different layers.

That's why the OSI model is useful.

---

# 🧠 Troubleshooting Challenge

A user reports:

> "I can't access the server."

You discover:

```text
Ethernet link = UP

IP address = Correct

Subnet mask = Correct

Default gateway = Correct

Ping to gateway = Successful

Ping to server = Successful

Website on server = Not loading
```

Would replacing the Ethernet cable be your first move?

```text
YES / NO
```

Why?

```text
____________________________________________________

____________________________________________________
```

The evidence suggests that lower-layer connectivity is functioning.

The problem may exist higher in the stack.

---

# 🏆 Optional Challenge — Follow ARP

Return to Simulation Mode.

Clear the simulation events if necessary.

Generate traffic again.

Watch for:

> **ARP**

ARP helps IPv4 devices discover Layer 2 MAC information associated with local IPv4 communication.

Don't worry about understanding every detail yet.

Just observe:

```text
IP Information
      ↓
Need Local MAC Information
      ↓
ARP
      ↓
Ethernet Delivery
```

We'll study ARP properly in:

> **Lesson 06 — Ethernet and MAC Addressing**

---

# 🏆 Optional Challenge — Inspect Both Sides of the Router

Capture traffic immediately before and after R-01.

Compare:

### Layer 3

```text
Source IP
Destination IP
```

with:

### Layer 2

```text
Source MAC
Destination MAC
```

Ask:

> Which addressing information stayed associated with the end-to-end IP communication?

and:

> Which addressing information changed for the new local Ethernet segment?

This is an excellent preview of routing.

---

# 💾 Part 27 — Save the Lab

Save your Packet Tracer project locally as:

```text
lab-04-osi-model.pkt
```

You do **not** need to upload it to the course repository unless you're intentionally maintaining completed reference files.

The important part is that you built and inspected the network yourself.

---

# 🧠 Knowledge Check

### 1.

Which layer deals with physical connections?

### 2.

Which layer uses Ethernet frames and MAC addresses?

### 3.

Which layer uses IP addresses?

### 4.

Which device primarily operates at Layer 2 in this lab?

### 5.

Which device performs the Layer 3 routing function?

### 6.

What is the Layer 2 PDU?

### 7.

What is the Layer 3 PDU?

### 8.

What is encapsulation?

### 9.

What is decapsulation?

### 10.

Why can Layer 2 addressing change when traffic crosses a router?

---

# ✅ Knowledge Check Answers

### 1.

**Layer 1 — Physical**

### 2.

**Layer 2 — Data Link**

### 3.

**Layer 3 — Network**

### 4.

**Switch**

### 5.

**Router**

### 6.

**Frame**

### 7.

**Packet**

### 8.

The process of adding protocol information as data moves down the networking stack for transmission.

### 9.

The process of processing/removing protocol information as received data moves up the networking stack.

### 10.

The router forwards the Layer 3 packet onto a different local link and creates the appropriate Layer 2 frame for that link.

---

# 🎓 Network+ Challenge 1

A technician notices that a switch port has no link.

Which OSI layer should be investigated first?

### A. Application

### B. Transport

### C. Network

### D. Physical

Answer:

> **D — Physical**

---

# 🎓 Network+ Challenge 2

A device has the wrong default gateway.

Which layer is primarily affected?

### A. Layer 1

### B. Layer 2

### C. Layer 3

### D. Layer 7

Answer:

> **C — Layer 3**

---

# 🎓 Network+ Challenge 3

Which PDU is associated with Layer 2?

### A. Segment

### B. Packet

### C. Frame

### D. Bitstream session

Answer:

> **C — Frame**

---

# 🎓 Network+ Challenge 4

Which device primarily forwards Ethernet frames using MAC addresses?

### A. Router

### B. Switch

### C. Modem

### D. Load balancer

Answer:

> **B — Switch**

---

# 📝 Lab Review

In this lab, you:

- Built a routed network
- Verified Layer 1 connectivity
- Configured Layer 3 addressing
- Generated ICMP traffic
- Used Packet Tracer Simulation Mode
- Followed traffic through switches
- Followed traffic through a router
- Inspected Ethernet information
- Inspected IPv4 information
- Observed Layer 2 behavior
- Observed Layer 3 behavior
- Explored encapsulation
- Explored decapsulation
- Broke Layer 1
- Diagnosed the failure
- Broke Layer 3
- Diagnosed the failure
- Used the OSI model as a troubleshooting framework

---

# 🧠 What You Should Now See

Networking should be starting to look less like:

```text
Computer
   ↓
Magic
   ↓
Server
```

and more like:

```text
Application
     ↓
Transport
     ↓
IP Packet
     ↓
Ethernet Frame
     ↓
Physical Network
     ↓
Switch
     ↓
Router
     ↓
Switch
     ↓
Physical Network
     ↓
Ethernet
     ↓
IP
     ↓
Application
```

You don't need to know every detail yet.

The important part is that you can now begin asking:

> **At what layer is the problem occurring?**

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
✅ Lab 04 — OSI Model & Packet Simulation
        ↓
🟡 NEXT: Lesson 05 — TCP/IP & Network Communication
        ↓
⬜ Lab 05 — TCP/IP & Wireshark Introduction
        ↓
🚀 Project 01 — Build Your First Network
```

---

# ➡️ Next Lesson

Continue to:

**📘 Lesson 05 — TCP/IP & Network Communication**

In Lesson 05, you'll move from the conceptual seven-layer OSI model to the networking model actually used by modern TCP/IP networks.

You'll learn:

```text
Application
     ↓
Transport
     ↓
Internet
     ↓
Network Access
```

and compare it directly to:

```text
OSI
7 Layers
```

You'll also follow an entire communication process from application to destination.

After Lesson 05:

> 🔍 **Lab 05 will introduce Wireshark**

You'll capture and inspect **real traffic from your own computer**, moving us from simulation into actual packet analysis.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Cisco Networking Companion](../resources/cisco-companion.md)**

➡️ **[Return to Main README](../README.md)**