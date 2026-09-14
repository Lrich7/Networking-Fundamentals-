# 🚀 Project 01 — Build Your First Network

Welcome to your first **Networking Fundamentals Project**.

This project brings together everything you learned in:

```text
Lesson 01 — Networking Basics
Lesson 02 — Network Types & Topologies
Lesson 03 — Network Devices
Lesson 04 — The OSI Model
Lesson 05 — TCP/IP & Network Communication
```

and Labs 01–05.

Unlike the guided labs, this project gives you a goal and a set of requirements.

You decide how to build the network.

---

# 🎯 Project Goal

Design, build, test, troubleshoot, and document a small business network in:

> 🌐 **Cisco Packet Tracer**

Your finished network must support:

- Two separate LANs
- Wired computers
- A server
- A router
- Ethernet switches
- Basic IPv4 addressing
- Default gateways
- Communication within each LAN
- Communication between LANs
- Basic troubleshooting
- Network documentation

The goal is not simply to make the green lights appear.

You should be able to explain:

> **Why the network works.**

---

# 🎓 Network+ Focus

This project reinforces Network+ concepts including:

- LANs
- Network topologies
- Routers
- Switches
- NICs
- IPv4 addressing
- Default gateways
- Ethernet
- MAC addressing concepts
- OSI model
- TCP/IP model
- ICMP
- Network diagrams
- Troubleshooting
- Documentation

---

# 🧰 Tools

Use:

- Cisco Packet Tracer
- Packet Tracer Command Prompt
- Packet Tracer Simulation Mode
- Your notes
- Lessons 01–05 as reference material

You may also use:

- Windows Command Prompt
- PowerShell
- Wireshark

for comparison with your real computer, but they aren't required to complete the Packet Tracer network.

---

# ⏱️ Estimated Time

Approximately:

**60–90 minutes**

Take longer if needed.

This is a project, not a race.

---

# 🏢 Scenario

A small company is opening a new office.

The company wants two network areas:

```text
OFFICE NETWORK

Employees
```

and:

```text
SERVER NETWORK

Business Servers
```

Employees need to communicate with one another and access the server network.

Management wants the network to be:

- Simple
- Easy to understand
- Easy to troubleshoot
- Properly documented

You have been asked to build the initial network.

---

# 📋 Business Requirements

Your network must contain at least:

```text
3 Employee PCs

1 Server

2 Switches

1 Router
```

The required logical design is:

```text
EMPLOYEE LAN
      │
      ▼
   SWITCH
      │
      ▼
   ROUTER
      │
      ▼
   SWITCH
      │
      ▼
 SERVER LAN
```

You may choose the exact physical arrangement.

---

# 🌐 Required Networks

Use these two IPv4 networks.

## Employee LAN

```text
192.168.10.0/24
```

## Server LAN

```text
192.168.20.0/24
```

Don't worry about calculating `/24`.

For this project:

```text
/24
=
255.255.255.0
```

You'll learn exactly why during the IPv4 and subnetting lessons.

---

# 📍 Addressing Requirements

You must create your own addressing plan.

Use these rules.

---

## Employee LAN

Router interface:

```text
192.168.10.1
```

Employee PCs must use addresses between:

```text
192.168.10.10
```

and:

```text
192.168.10.50
```

---

## Server LAN

Router interface:

```text
192.168.20.1
```

The server must use an address between:

```text
192.168.20.10
```

and:

```text
192.168.20.50
```

---

# 📝 Complete Your Addressing Plan

Before building the network, fill this out.

| Device | IP Address | Subnet Mask | Default Gateway |
|---|---|---|---|
| Router — Employee Interface | 192.168.10.1 | 255.255.255.0 | — |
| Router — Server Interface | 192.168.20.1 | 255.255.255.0 | — |
| Employee PC 1 | | 255.255.255.0 | 192.168.10.1 |
| Employee PC 2 | | 255.255.255.0 | 192.168.10.1 |
| Employee PC 3 | | 255.255.255.0 | 192.168.10.1 |
| Server | | 255.255.255.0 | 192.168.20.1 |

Do not assign the same IP address to two devices.

---

# ✏️ Device Naming

Use meaningful names.

Example:

```text
PC-01
PC-02
PC-03

SW-01
SW-02

R-01

SRV-01
```

You may create your own naming convention if you prefer.

The important thing is:

> **Be consistent.**

---

# 🗺️ Phase 1 — Design the Network

Before opening Packet Tracer, sketch the topology.

Your drawing should identify:

- PCs
- Switches
- Router
- Server
- Employee LAN
- Server LAN

Do not simply copy a finished diagram from a lab.

Create your own layout based on the requirements.

---

# 🧠 Design Questions

Before building, answer:

### Why do the employee PCs need a switch?

```text
____________________________________________________

____________________________________________________
```

### Why is a router required?

```text
____________________________________________________

____________________________________________________
```

### Why does the server need a default gateway?

```text
____________________________________________________

____________________________________________________
```

### What topology will the LAN portions primarily use?

```text
____________________________________________________
```

---

# 🌐 Phase 2 — Build the Network

Open:

> **Cisco Packet Tracer**

Create the network using your design.

You must include:

```text
3 PCs
2 Switches
1 Router
1 Server
```

---

# ⚠️ No Step-by-Step Cabling Instructions

Unlike the earlier labs, this project will not tell you exactly:

```text
Click this device
Choose this port
Connect to this port
```

Use what you learned in Labs 02–04.

Think about:

- Which devices connect to switches
- Which interfaces are needed
- Which cable type is appropriate
- Which router interfaces connect the LANs

If something doesn't work:

> **Troubleshoot it.**

That's part of the project.

---

# 🔌 Phase 3 — Verify Physical Connectivity

Before configuring IP addresses, verify:

```text
Devices powered on

Interfaces connected

Switch links operational

Router interfaces connected
```

Think:

> **OSI Layer 1**

Do not troubleshoot Layer 3 configuration while Layer 1 is broken.

---

# 📍 Phase 4 — Configure IPv4

Configure every device according to your addressing plan.

Remember:

## Employee PCs

Must use:

```text
192.168.10.x
```

Default gateway:

```text
192.168.10.1
```

---

## Server

Must use:

```text
192.168.20.x
```

Default gateway:

```text
192.168.20.1
```

---

## Router

Must have an interface in both networks:

```text
192.168.10.1
```

and:

```text
192.168.20.1
```

Ensure both router interfaces are operational.

---

# 🧠 Checkpoint — Explain the Router

Complete:

```text
The router needs an address on the Employee LAN because:

____________________________________________________
```

```text
The router needs an address on the Server LAN because:

____________________________________________________
```

---

# 🧪 Phase 5 — Test Local Employee Connectivity

From Employee PC 1:

Ping Employee PC 2.

Then ping Employee PC 3.

Record:

| Test | Result |
|---|---|
| PC 1 → PC 2 | PASS / FAIL |
| PC 1 → PC 3 | PASS / FAIL |

If either test fails, troubleshoot before continuing.

---

# 🚪 Phase 6 — Test the Default Gateway

From each employee PC, ping:

```text
192.168.10.1
```

Record:

| Device | Gateway Test |
|---|---|
| PC 1 | PASS / FAIL |
| PC 2 | PASS / FAIL |
| PC 3 | PASS / FAIL |

---

# 🗄️ Phase 7 — Test the Server Gateway

From SRV-01, ping:

```text
192.168.20.1
```

Record:

```text
PASS / FAIL
```

---

# 🌐 Phase 8 — Test Routed Communication

Now test from an employee PC to the server.

Example:

```cmd
ping SERVER_IP
```

Record:

```text
PC-01 → SRV-01

PASS / FAIL
```

Test from another employee PC.

Record:

```text
PC-02 → SRV-01

PASS / FAIL
```

---

# 🧠 Explain the Traffic Path

Describe the path from an employee PC to the server.

Fill in:

```text
Employee PC
     ↓
____________________
     ↓
____________________
     ↓
____________________
     ↓
Server
```

You should be able to identify:

- Employee switch
- Router
- Server switch

---

# 🧱 Phase 9 — Identify the OSI Layers

For the path between PC-01 and SRV-01, identify examples of:

### Layer 1 — Physical

```text
____________________________________
```

### Layer 2 — Data Link

```text
____________________________________
```

### Layer 3 — Network

```text
____________________________________
```

### Layer 4 — Transport

```text
____________________________________
```

### Layer 7 — Application

```text
____________________________________
```

You don't need a perfect real-world example at every layer.

Use the concepts you've learned so far.

---

# 🌐 Phase 10 — Map the Network to TCP/IP

Complete:

| TCP/IP Layer | Example from Your Network |
|---|---|
| Application | |
| Transport | |
| Internet | |
| Network Access | |

---

# 🔍 Phase 11 — Use Simulation Mode

Switch Packet Tracer to:

> **Simulation Mode**

Generate a Simple PDU from:

```text
PC-01
```

to:

```text
SRV-01
```

Advance the simulation slowly.

Observe the path.

---

# 📝 Record the Path

```text
PC-01
   ↓
____________________
   ↓
____________________
   ↓
____________________
   ↓
SRV-01
```

---

# 🧠 Observation Questions

Which device forwards traffic inside the Employee LAN?

```text
____________________________________
```

Which device moves traffic between the Employee LAN and Server LAN?

```text
____________________________________
```

Which device forwards traffic inside the Server LAN?

```text
____________________________________
```

---

# 🔎 Phase 12 — Inspect the PDU

In Simulation Mode, inspect the packet information.

Identify:

```text
Source IP:

____________________________________

Destination IP:

____________________________________
```

If Ethernet information is visible, identify:

```text
Source MAC:

____________________________________

Destination MAC:

____________________________________
```

---

# 🧠 Explain the Difference

Why do IP addresses and MAC addresses have different jobs?

```text
____________________________________________________

____________________________________________________

____________________________________________________
```

---

# 💥 Phase 13 — Troubleshooting Challenge 1

Once the network works, intentionally disconnect:

> **One employee PC from the switch**

Do not change anything else.

Test the network.

Answer:

### Which device stopped working?

```text
____________________________________
```

### Which devices continued working?

```text
____________________________________
```

### Which part of the topology was broken?

```text
____________________________________
```

### Which OSI layer was most obviously affected?

```text
____________________________________
```

Repair the problem and verify connectivity.

---

# 💥 Phase 14 — Troubleshooting Challenge 2

Change one employee PC's default gateway to:

```text
192.168.10.254
```

Do not change its IP address.

Test:

```text
Ping another employee PC
```

and:

```text
Ping the server
```

Record:

| Test | Result |
|---|---|
| Employee PC → Local Employee PC | PASS / FAIL |
| Employee PC → Server | PASS / FAIL |

---

# 🧠 Explain the Result

Why might local communication still work while remote communication fails?

```text
____________________________________________________

____________________________________________________

____________________________________________________
```

Which OSI layer contains the incorrect configuration?

```text
____________________________________
```

Restore the correct gateway:

```text
192.168.10.1
```

---

# 💥 Phase 15 — Troubleshooting Challenge 3

Disconnect the router from the Server LAN.

Now test:

```text
PC-01 → PC-02
```

and:

```text
PC-01 → SRV-01
```

Record:

| Test | Result |
|---|---|
| PC-01 → PC-02 | PASS / FAIL |
| PC-01 → SRV-01 | PASS / FAIL |

---

# 🧠 What Does This Prove?

Complete:

```text
The Employee LAN is:

WORKING / NOT WORKING
```

```text
The path to the Server LAN is:

WORKING / NOT WORKING
```

What shared component or path should you investigate?

```text
____________________________________
```

Repair the connection.

---

# 🧪 Phase 16 — Unknown Problem Challenge

Now create one additional problem yourself.

Choose only one:

- Disconnect a cable
- Disable a router interface
- Enter the wrong subnet mask
- Enter the wrong IP address
- Enter the wrong default gateway

Then pretend you didn't know exactly what broke.

Follow this process:

```text
Identify the symptom
      ↓
Determine what works
      ↓
Determine what fails
      ↓
Form a theory
      ↓
Test the theory
      ↓
Repair the problem
      ↓
Verify connectivity
```

---

# 📝 Troubleshooting Report

Document your problem.

### Problem

```text
____________________________________________________
```

### Initial Symptoms

```text
____________________________________________________

____________________________________________________
```

### What Still Worked?

```text
____________________________________________________
```

### What Failed?

```text
____________________________________________________
```

### Theory

```text
____________________________________________________
```

### Root Cause

```text
____________________________________________________
```

### Solution

```text
____________________________________________________
```

### Verification

```text
____________________________________________________
```

---

# 📐 Phase 17 — Create the Final Network Diagram

Create a clean logical diagram.

Include:

- Device names
- Router
- Switches
- PCs
- Server
- Network names
- IPv4 addresses
- Router interface addresses

Your diagram might resemble this general structure:

```text
EMPLOYEE LAN
192.168.10.0/24

PC-01 ──┐
        │
PC-02 ─ SW-01 ───── R-01
        │             │
PC-03 ──┘             │
                      │
                      │
                    SW-02
                      │
                      │
                    SRV-01

SERVER LAN
192.168.20.0/24
```

Do not simply copy this diagram.

Use your actual device arrangement and addressing.

---

# 📋 Phase 18 — Create a Device Inventory

Complete:

| Device | Type | Purpose |
|---|---|---|
| PC-01 | Workstation | |
| PC-02 | Workstation | |
| PC-03 | Workstation | |
| SW-01 | Switch | |
| R-01 | Router | |
| SW-02 | Switch | |
| SRV-01 | Server | |

---

# 📍 Phase 19 — Final Addressing Table

Complete your final table.

| Device | Interface | IP Address | Subnet Mask | Gateway |
|---|---|---|---|---|
| PC-01 | | | | |
| PC-02 | | | | |
| PC-03 | | | | |
| R-01 | Employee LAN | 192.168.10.1 | 255.255.255.0 | — |
| R-01 | Server LAN | 192.168.20.1 | 255.255.255.0 | — |
| SRV-01 | | | | |

---

# ✅ Phase 20 — Final Verification

Your project isn't complete until every required test passes.

## Employee LAN

```text
PC-01 → PC-02       PASS / FAIL
PC-01 → PC-03       PASS / FAIL
PC-02 → PC-03       PASS / FAIL
```

## Gateways

```text
PC-01 → Employee Gateway      PASS / FAIL
PC-02 → Employee Gateway      PASS / FAIL
PC-03 → Employee Gateway      PASS / FAIL

SRV-01 → Server Gateway       PASS / FAIL
```

## Routed Communication

```text
PC-01 → SRV-01       PASS / FAIL
PC-02 → SRV-01       PASS / FAIL
PC-03 → SRV-01       PASS / FAIL
```

All required tests should:

> **PASS**

before you call the project complete.

---

# 💾 Phase 21 — Save Your Packet Tracer Project

Save as:

```text
project-01-build-your-first-network.pkt
```

Keep the file locally with your training work.

You do not need to upload your personal completed project to the public repository.

---

# 📦 Project Deliverables

By the end of Project 01, you should have:

- ✅ Working Packet Tracer network
- ✅ Three employee PCs
- ✅ Two switches
- ✅ One router
- ✅ One server
- ✅ Two IPv4 networks
- ✅ Completed addressing table
- ✅ Working default gateways
- ✅ Successful local connectivity
- ✅ Successful routed connectivity
- ✅ Logical network diagram
- ✅ Device inventory
- ✅ Troubleshooting report
- ✅ Completed final verification tests

---

# 🏆 Optional Challenge 1 — Add a Wireless Network

Add:

```text
AP-01
```

and:

```text
LAPTOP-01
```

Connect the AP to the Employee LAN.

Configure the laptop with a valid:

```text
192.168.10.x
```

address.

Verify that the laptop can reach:

- Employee PCs
- Default gateway
- SRV-01

---

# 🏆 Optional Challenge 2 — Add a Second Server

Add:

```text
SRV-02
```

to the Server LAN.

Assign an unused address within:

```text
192.168.20.10–192.168.20.50
```

Verify that every employee PC can reach both servers.

---

# 🏆 Optional Challenge 3 — Remove a Failure Point

Look at your network.

Ask:

> **Which devices are single points of failure?**

Write down at least two.

```text
1. _________________________________

2. _________________________________
```

How might a real business reduce those risks?

```text
____________________________________________________

____________________________________________________
```

You don't need to redesign the network yet.

We'll study redundancy later.

---

# 🎓 Network+ Challenge

A workstation can communicate with other PCs on:

```text
192.168.10.0/24
```

but cannot communicate with a server on:

```text
192.168.20.0/24
```

Which setting should be checked early in the troubleshooting process?

### A. Local keyboard layout

### B. Default gateway

### C. Computer hostname only

### D. Monitor settings

Answer:

> **B — Default gateway**

---

# 🎓 Network+ Challenge 2

Which device primarily connects the two IP networks in your project?

### A. Switch

### B. Router

### C. NIC

### D. Access point

Answer:

> **B — Router**

---

# 🎓 Network+ Challenge 3

Which device primarily forwards Ethernet frames inside the Employee LAN?

### A. Router

### B. Switch

### C. Modem

### D. Proxy

Answer:

> **B — Switch**

---

# 🎓 Network+ Challenge 4

A cable between PC-01 and SW-01 is disconnected.

Which OSI layer is most directly affected?

### A. Layer 1

### B. Layer 3

### C. Layer 4

### D. Layer 7

Answer:

> **A — Physical**

---

# 🧠 Final Reflection

Answer these in your own words.

### What was the hardest part of the project?

```text
____________________________________________________

____________________________________________________
```

### What networking concept makes more sense now than it did before?

```text
____________________________________________________

____________________________________________________
```

### If the network stopped working tomorrow, where would you start troubleshooting?

```text
____________________________________________________

____________________________________________________
```

---

# 🏁 Project Complete

You have completed:

> **🚀 Project 01 — Build Your First Network**

You have now designed, built, tested, broken, repaired, and documented a small routed network.

That's a major step beyond simply memorizing networking terminology.

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS

✅ Lesson 01
✅ Lab 01

✅ Lesson 02
✅ Lab 02

✅ Lesson 03
✅ Lab 03

✅ Lesson 04
✅ Lab 04

✅ Lesson 05
✅ Lab 05

✅ PROJECT 01 — BUILD YOUR FIRST NETWORK

            ↓

🔵 PHASE 2 — ADDRESSING & COMMUNICATION

🟡 NEXT:
Lesson 06 — Ethernet & MAC Addressing

⬜ Lab 06 — Ethernet & MAC Addressing

⬜ Lesson 07 — IPv4 Addressing

⬜ Lab 07 — IPv4 Addressing

⬜ Lesson 08 — Subnetting Fundamentals
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 06 — Ethernet and MAC Addressing**

In Lesson 06, you'll dig much deeper into the Layer 2 communication you've already seen.

You'll learn:

- Ethernet
- MAC addresses
- Ethernet frames
- Unicast
- Broadcast
- Multicast
- ARP
- Switch MAC address tables
- Local network delivery

Then Lab 06 will combine:

```text
Windows
+
Packet Tracer
+
Wireshark
```

to let you inspect Ethernet and MAC addressing from three different perspectives.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](README.md)**

➡️ **[Return to Main README](../README.md)**