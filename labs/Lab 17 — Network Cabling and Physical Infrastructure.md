# 🧪 Lab 17 — Network Cabling and Physical Infrastructure

Welcome to **Lab 17 of Networking Fundamentals**.

This lab is different from many previous labs.

You cannot realistically learn structured cabling by pretending every physical task happens inside Packet Tracer.

Instead, this lab combines:

```text
Network Design
+
Cable Selection
+
Distance Planning
+
Patch-Panel Documentation
+
PoE Planning
+
Windows Inspection
+
Packet Tracer Troubleshooting
```

The goal is to start thinking like the technician responsible for the physical network.

---

# 🎯 Lab Objectives

You will:

- Design physical connectivity for a small office
- Choose appropriate copper cabling
- Determine when fiber should be used
- Work with MDF and IDF concepts
- Create patch-panel documentation
- Trace a connection from workstation to switch
- Identify cable-distance problems
- Calculate basic PoE requirements
- Inspect Windows adapter link information
- Identify common Layer 1 failures
- Troubleshoot Packet Tracer physical connectivity
- Document a physical network problem

---

# ⏱️ Estimated Time

**60–90 minutes**

---

# 🧰 Tools

Use:

- Your computer
- PowerShell
- Cisco Packet Tracer
- Calculator
- Lesson 17 notes

Optional, if available in an authorized environment:

- Ethernet patch cable
- Cable tester
- Tone generator/probe
- Patch panel
- Network switch

Do not disconnect or modify production cabling just to complete this lab.

---

# 🏢 LAB SCENARIO

You are helping install networking for a fictional company:

> **Northstar Services**

The building contains:

```text
Floor 1
Main Network Room
Reception
Offices
Conference Rooms

Floor 2
Offices
Training Room
Wireless Access Points
Security Cameras
```

The main network room is on Floor 1.

---

# 🗄️ PART 1 — IDENTIFY THE MDF

The main network room contains:

```text
ISP Connection
Firewall
Core Switch
Patch Panels
UPS
Fiber Equipment
```

Should this location be considered:

### A. MDF
### B. IDF

Record:

```text
____________________________
```

---

# ✅ Answer

> **MDF**

It is the primary distribution point for the site.

---

# 📏 PART 2 — DISTANCE PROBLEM

The farthest Floor 2 office is approximately:

```text
135 meters
```

of cable path from the MDF.

Question:

> Should you run one standard copper Ethernet channel directly from the MDF to that office?

```text
YES / NO
```

---

# ✅ Answer

> **No**

A standard twisted-pair Ethernet channel is generally limited to:

```text
100 meters
```

We need another design.

---

# 🏢 PART 3 — ADD AN IDF

Create an IDF on Floor 2.

The design becomes:

```text
                 FLOOR 1

                   ISP
                    │
                 FIREWALL
                    │
               CORE SWITCH
                    │
                   MDF
                    │
                    │
                 FIBER
                    │
                    ▼

                 FLOOR 2

                   IDF
                    │
              ACCESS SWITCH
               /    |     \
              /     |      \
            PCs     APs    Cameras
```

---

# 🧠 Question

Why is fiber a good choice between the MDF and IDF?

Record at least two reasons:

```text
1. ____________________________

2. ____________________________
```

Possible answers include:

- Longer distance
- High bandwidth
- Resistance to EMI
- Common backbone/uplink medium

---

# 🧵 PART 4 — SELECT THE FIBER

The MDF and IDF are:

```text
160 meters
```

apart by the actual cable pathway.

This is within the capability of many appropriate multimode fiber Ethernet implementations.

For this fictional office, choose:

```text
Multimode Fiber
```

for the building backbone.

---

# 🧠 Important

This does **not** mean:

> Multimode always works at every 160-meter link speed.

Fiber distance depends on:

```text
Fiber Type
+
Ethernet Standard
+
Transceiver
+
Wavelength
```

Always check the specifications of the actual equipment.

---

# 🔌 PART 5 — SELECT COPPER CABLING

Northstar wants new horizontal cabling capable of supporting modern business networking and future upgrades.

Choose:

### A. Cat3
### B. Cat5
### C. Cat6
### D. Telephone cable

Record:

```text
____________________________
```

---

# ✅ Answer

For this project:

> **Cat6**

Cat6 is a reasonable modern choice for general office horizontal Ethernet cabling.

In environments specifically designed around 10 Gb over full copper channel distances, Cat6a may be selected instead.

---

# 📏 PART 6 — CHECK CABLE RUNS

The Floor 2 IDF has these cable-path distances:

| Location | Permanent Cable |
|---|---:|
| Office 201 | 32 m |
| Office 202 | 48 m |
| Training Room | 67 m |
| AP-201 | 74 m |
| Camera-201 | 86 m |
| Office 220 | 94 m |

Assume each connection will also require approximately:

```text
6 meters
```

of combined patch cords.

Calculate total channel lengths.

---

# ✏️ Complete

| Location | Permanent | Patch | Total |
|---|---:|---:|---:|
| Office 201 | 32 m | 6 m | |
| Office 202 | 48 m | 6 m | |
| Training Room | 67 m | 6 m | |
| AP-201 | 74 m | 6 m | |
| Camera-201 | 86 m | 6 m | |
| Office 220 | 94 m | 6 m | |

---

# ✅ Answers

| Location | Total |
|---|---:|
| Office 201 | 38 m |
| Office 202 | 54 m |
| Training Room | 73 m |
| AP-201 | 80 m |
| Camera-201 | 92 m |
| Office 220 | **100 m** |

---

# ⭐ Observation

Office 220 is exactly at:

```text
100 meters
```

There is no useful distance margin.

In a real installation, you would want to verify:

- Actual measured pathway
- Patch-cord lengths
- Cable quality
- Installation standard
- Certification results

---

# 🧱 PART 7 — TRACE A CONNECTION

A workstation connection should follow:

```text
PC-201
   │
   ▼
Patch Cable
   │
   ▼
Wall Jack
   │
   ▼
Horizontal Cabling
   │
   ▼
Patch Panel
   │
   ▼
Patch Cable
   │
   ▼
Access Switch
```

---

# 🧠 Question

Which portion should generally remain permanently installed?

### A. User patch cable
### B. Horizontal building cabling
### C. Switch patch cable

Answer:

> **B — Horizontal building cabling**

---

# 🏷️ PART 8 — BUILD A LABELING SYSTEM

Use this naming pattern:

```text
Floor-Room-Jack
```

Examples:

```text
2-201-A
2-201-B
2-202-A
```

Create labels for:

```text
Office 201 — Jack A
Office 201 — Jack B
Office 202 — Jack A
Training Room — Jack A
AP-201
Camera-201
```

---

# ✏️ Record

```text
Office 201 A:
____________________________

Office 201 B:
____________________________

Office 202 A:
____________________________

Training Room A:
____________________________

AP-201:
____________________________

Camera-201:
____________________________
```

A consistent scheme matters more than matching one universal naming standard.

---

# 📋 PART 9 — PATCH PANEL DOCUMENTATION

Assume Floor 2 uses:

```text
Patch Panel:
PP-02
```

Create:

| Patch Panel Port | Destination | Switch Port |
|---:|---|---|
| 01 | Office 201-A | SW-IDF-01 Gi1/0/1 |
| 02 | Office 201-B | SW-IDF-01 Gi1/0/2 |
| 03 | Office 202-A | SW-IDF-01 Gi1/0/3 |
| 04 | Training Room-A | SW-IDF-01 Gi1/0/4 |
| 05 | AP-201 | SW-IDF-01 Gi1/0/5 |
| 06 | Camera-201 | SW-IDF-01 Gi1/0/6 |

---

# 🔍 PART 10 — TRACE A TROUBLE TICKET

Ticket:

> "The computer plugged into Office 202 Jack A has no network connection."

Using your documentation, trace:

```text
Office 202-A
      ↓
PP-02 Port ______
      ↓
SW-IDF-01 Port ______
```

---

# ✅ Answer

```text
Office 202-A
      ↓
PP-02 Port 03
      ↓
SW-IDF-01 Gi1/0/3
```

This is why documentation matters.

---

# 🧠 Without Documentation

The troubleshooting process might become:

```text
48 cables
+
48 switch ports
+
No labels
=
Guessing
```

Good documentation saves time.

---

# ⚡ PART 11 — POE PLANNING

SW-IDF-01 has:

```text
PoE Budget:
120 watts
```

Connected devices:

| Device | Quantity | Power Each |
|---|---:|---:|
| Wireless AP | 3 | 18 W |
| IP Phone | 6 | 7 W |
| Camera | 4 | 10 W |

Calculate the total.

---

# ✏️ AP Power

```text
3 × 18 W
=
________ W
```

Answer:

```text
54 W
```

---

# ✏️ Phone Power

```text
6 × 7 W
=
________ W
```

Answer:

```text
42 W
```

---

# ✏️ Camera Power

```text
4 × 10 W
=
________ W
```

Answer:

```text
40 W
```

---

# 🧮 Total

```text
54
+
42
+
40
=
136 W
```

---

# 🚨 Problem

Switch budget:

```text
120 W
```

Required:

```text
136 W
```

Shortfall:

```text
16 W
```

---

# 🧠 Question

Is this design acceptable?

> **No**

The expected device demand exceeds the switch's available PoE budget.

---

# 🔧 Possible Solutions

Depending on the actual environment:

- Use a switch with a larger PoE budget
- Add another PoE switch
- Redistribute powered devices
- Use appropriate external power where supported
- Reevaluate actual device power requirements

Do not assume:

> "The switch has PoE, so every connected device can receive unlimited power."

---

# 💻 PART 12 — WINDOWS LINK INSPECTION

On your Windows computer, open PowerShell.

Run:

```text
Get-NetAdapter
```

Find your active adapter.

Record:

```text
Adapter Name:

____________________________


Status:

____________________________


Link Speed:

____________________________
```

---

# 🔍 PART 13 — MORE ADAPTER INFORMATION

Run:

```text
Get-NetAdapter | Format-Table Name, InterfaceDescription, Status, LinkSpeed
```

Look for:

```text
Status
LinkSpeed
```

---

# 🧠 Question

If an Ethernet adapter reports:

```text
Disconnected
```

should DNS be your first troubleshooting step?

> **No**

Investigate physical connectivity first.

---

# 🧪 PART 14 — PACKET TRACER PHYSICAL LAB

Open Cisco Packet Tracer.

Build:

```text
PC-01
  │
  ▼
SW-01
  │
  ▼
R-01
```

Use appropriate Ethernet connections.

Wait for links to become active.

---

# 🔍 PART 15 — VERIFY SWITCH STATUS

On SW-01:

```text
enable
```

Then:

```text
show interfaces status
```

Identify the ports connected to:

```text
PC-01
R-01
```

Record:

```text
PC Port:
____________________________

Router Port:
____________________________
```

---

# 🌐 PART 16 — BASIC ADDRESSING

Configure:

## PC-01

```text
192.168.10.10/24

Gateway:
192.168.10.1
```

## R-01

```text
192.168.10.1/24
```

Enable the router interface.

Verify:

```text
PC-01
   ↓
ping
   ↓
192.168.10.1
```

Expected:

> **Success**

---

# 💥 PART 17 — FAILURE 1: DISCONNECTED CABLE

Delete or disconnect the cable between:

```text
PC-01
and
SW-01
```

Test:

```text
ping 192.168.10.1
```

Expected:

> **Failure**

---

# 🔍 Investigate

Ask:

```text
Is PC physically connected?

Is there link?

Does the switch show the port connected?
```

Check:

```text
show interfaces status
```

---

# 🧠 Root Cause

```text
Layer 1
Physical connection
```

---

# 🔧 Repair

Reconnect the cable.

Wait for link.

Retest.

---

# 💥 PART 18 — FAILURE 2: ADMINISTRATIVELY DISABLED PORT

On SW-01, find the PC port.

Then:

```text
configure terminal
interface fa0/1
 shutdown
end
```

Use your actual port number.

---

# 🔍 Investigate

Run:

```text
show interfaces status
```

and inspect the port.

The physical cable is present.

But:

> The switch interface has been disabled.

---

# ⭐ Important Distinction

A cable can be connected while the interface is still unusable.

Layer 1 troubleshooting includes:

```text
Physical Cable
+
Interface State
```

---

# 🔧 Repair

```text
configure terminal
interface fa0/1
 no shutdown
end
```

Retest.

---

# 💥 PART 19 — FAILURE 3: ROUTER INTERFACE SHUTDOWN

On R-01:

```text
configure terminal
interface g0/0
 shutdown
end
```

Use the actual connected interface.

From PC-01:

```text
ping 192.168.10.1
```

---

# 🔍 Investigate

On R-01:

```text
show ip interface brief
```

Look for:

```text
administratively down
```

---

# 🔧 Repair

```text
configure terminal
interface g0/0
 no shutdown
end
```

Verify:

```text
show ip interface brief
```

Then retest.

---

# 🔀 PART 20 — CABLE TYPE REVIEW

Historically:

```text
PC → Switch
```

typically used:

> **Straight-through**

while:

```text
Switch → Switch
```

could require:

> **Crossover**

Modern equipment commonly supports:

> **Auto-MDI/MDIX**

which reduces the need to manually select crossover cables.

---

# 🧠 Question

Why should you still learn crossover cables?

Record:

```text
________________________________

________________________________
```

Suggested answer:

> **They may appear on certification exams and when working with legacy equipment.**

---

# 🔬 PART 21 — INSPECT INTERFACE DETAILS

On SW-01:

```text
show interfaces
```

Locate your PC-facing interface.

Look for information related to:

```text
Status
Protocol
Duplex
Speed
Errors
```

---

# 📝 Record

```text
Interface:

____________________________


Status:

____________________________


Duplex:

____________________________


Speed:

____________________________
```

Packet Tracer output varies depending on the device model.

---

# 💥 PART 22 — TROUBLESHOOTING SCENARIO

You receive:

> "Office 201 has no network."

You find:

```text
PC powered on
NIC enabled
No Ethernet link
Wall cable connected
Switch port configured correctly
```

What should you investigate next?

Potential areas:

```text
Patch cable

Wall jack

Horizontal cabling

Patch panel connection

Switch patch cable

Physical switch port
```

---

# 🧭 PART 23 — TROUBLESHOOT IN ORDER

Use:

```text
PC
 ↓
PC Patch Cable
 ↓
Wall Jack
 ↓
Horizontal Cable
 ↓
Patch Panel
 ↓
Switch Patch Cable
 ↓
Switch Port
```

Check each part systematically.

---

# 🧪 PART 24 — KNOWN-GOOD CABLE

Suppose you replace:

```text
PC Patch Cable
```

with a known-good cable.

The link immediately comes up.

What is the likely root cause?

> **The original patch cable**

---

# ⭐ Important Troubleshooting Technique

Substitution is powerful:

```text
Suspected Component
       ↓
Known-Good Component
       ↓
Retest
```

But change one thing at a time when practical.

---

# 🔊 PART 25 — CABLE IDENTIFICATION SCENARIO

You have:

```text
24 unlabeled Ethernet cables
```

in an old network closet.

You need to determine which cable connects to:

```text
Conference Room Jack A
```

Which tool would help?

### A. Multimeter only
### B. Tone generator and probe
### C. Wireshark
### D. `nslookup`

Answer:

> **B — Tone generator and probe**

---

# 🧪 PART 26 — CABLE TESTER SCENARIOS

Match each problem.

### Scenario A

One conductor has no continuity.

```text
____________________________
```

Answer:

> **Open**

---

### Scenario B

Two conductors make unintended contact.

```text
____________________________
```

Answer:

> **Short**

---

### Scenario C

Conductors terminate on incorrect pins.

```text
____________________________
```

Answer:

> **Miswire**

---

### Scenario D

Pins may show continuity, but the proper twisted pairs were not maintained.

```text
____________________________
```

Answer:

> **Split pair**

---

# 🔦 PART 27 — FIBER TROUBLESHOOTING

Suppose the MDF-to-IDF fiber link is down.

Potential causes include:

```text
Disconnected fiber

Incorrect transceiver

Wrong fiber type

Incompatible wavelength

Dirty connector

Damaged fiber

Fiber polarity

Disabled interface

Failed transceiver
```

---

# 🧠 Important

Do not assume:

> "Fiber is fiber."

You must consider:

```text
Fiber
+
Transceiver
+
Connector
+
Wavelength
+
Speed
+
Distance
```

---

# ⚠️ PART 28 — FIBER SAFETY

Before working with fiber:

- Never stare into an active fiber connector
- Follow workplace safety procedures
- Protect connectors from contamination
- Handle fiber carefully
- Properly dispose of fiber scraps/shards

---

# 📝 PART 29 — DOCUMENT THE PHYSICAL NETWORK

Create a final table:

| Location | Jack | Patch Panel | Switch | Port | Cable |
|---|---|---|---|---|---|
| Office 201 | A | PP-02/01 | SW-IDF-01 | Gi1/0/1 | Cat6 |
| Office 201 | B | PP-02/02 | SW-IDF-01 | Gi1/0/2 | Cat6 |
| Office 202 | A | PP-02/03 | SW-IDF-01 | Gi1/0/3 | Cat6 |
| Training Room | A | PP-02/04 | SW-IDF-01 | Gi1/0/4 | Cat6 |
| AP-201 | — | PP-02/05 | SW-IDF-01 | Gi1/0/5 | Cat6 |
| Camera-201 | — | PP-02/06 | SW-IDF-01 | Gi1/0/6 | Cat6 |

---

# 🗺️ PART 30 — DOCUMENT THE BACKBONE

Record:

```text
MDF:

____________________________


IDF:

____________________________


Backbone Medium:

____________________________


Approximate Distance:

____________________________


Fiber Type:

____________________________


Transceiver Type:

____________________________
```

For the fictional design, an example is:

```text
MDF:
MDF-01

IDF:
IDF-02

Backbone:
Fiber

Distance:
160 m

Fiber:
Appropriate Multimode Fiber

Transceiver:
Compatible fiber transceiver selected for speed,
fiber type, wavelength, and distance
```

---

# 📝 PART 31 — TROUBLESHOOTING REPORT

Document one Layer 1 failure:

```text
Problem:

________________________________


Initial Symptoms:

________________________________


Link Light:

UP / DOWN


Physical Path Checked:

________________________________


Tools Used:

________________________________


Switch Port:

________________________________


Interface Status:

________________________________


Root Cause:

________________________________


Solution:

________________________________


Verification:

________________________________


What I Learned:

________________________________
```

---

# 🧠 PART 32 — EXPLAIN THE PHYSICAL PATH

Without looking back, explain what happens physically between a workstation and a switch in a structured-cabling environment.

Try to include:

```text
PC
Patch Cable
Wall Jack
Horizontal Cabling
Patch Panel
Patch Cable
Switch
```

If you can explain that path:

> You understand much more than simply "plug an Ethernet cable into the switch."

---

# 🎓 Network+ Challenge 1

What is the general maximum standard channel distance for twisted-pair Ethernet?

### A. 50 m
### B. 90 m
### C. 100 m
### D. 150 m

> **Answer: C — 100 m**

---

# 🎓 Network+ Challenge 2

Which cable category is designed to support 10 Gb Ethernet across a standard 100-meter copper channel?

### A. Cat3
### B. Cat5
### C. Cat5e
### D. Cat6a

> **Answer: D — Cat6a**

---

# 🎓 Network+ Challenge 3

Which fiber type is generally preferred for much longer distances?

### A. Multimode
### B. Single-mode
### C. Cat6
### D. Coax

> **Answer: B — Single-mode**

---

# 🎓 Network+ Challenge 4

Which device organizes permanent building cabling before short patch cords connect it to a switch?

> **Patch panel**

---

# 🎓 Network+ Challenge 5

Which tool is useful for locating an unknown cable?

> **Tone generator and probe**

---

# 🎓 Network+ Challenge 6

What technology allows an access point to receive data and electrical power through Ethernet?

> **PoE**

---

# 🎓 Network+ Challenge 7

A switch has:

```text
PoE Budget:
100 W
```

Connected devices require:

```text
125 W
```

What is the problem?

> **The connected devices' expected power demand exceeds the switch's PoE budget.**

---

# 🎓 Network+ Challenge 8

An Ethernet port has no link.

Which OSI layer should you investigate immediately?

> **Layer 1 — Physical**

---

# 🏆 LAB COMPLETION CHECKLIST

- [ ] I understand MDF vs. IDF
- [ ] I evaluated copper distance limits
- [ ] I selected an MDF-to-IDF backbone medium
- [ ] I selected office horizontal cabling
- [ ] I calculated Ethernet channel distances
- [ ] I traced a structured-cabling connection
- [ ] I created cable labels
- [ ] I created patch-panel documentation
- [ ] I traced a jack to its switch port
- [ ] I calculated a PoE budget
- [ ] I inspected a Windows network adapter
- [ ] I used `Get-NetAdapter`
- [ ] I built the Packet Tracer physical topology
- [ ] I inspected switch interface status
- [ ] I troubleshot a disconnected cable
- [ ] I troubleshot a shutdown switch port
- [ ] I troubleshot a shutdown router interface
- [ ] I reviewed straight-through vs. crossover
- [ ] I reviewed common cable faults
- [ ] I reviewed fiber troubleshooting
- [ ] I documented the physical network
- [ ] I completed a Layer 1 troubleshooting report

---

# 🏆 Lab 17 Complete

You have now worked through the physical path:

```text
Endpoint
   ↓
Patch Cable
   ↓
Wall Jack
   ↓
Horizontal Cabling
   ↓
Patch Panel
   ↓
Switch
   ↓
Fiber Uplink
   ↓
MDF / IDF Infrastructure
```

More importantly, you now know:

> **A networking problem does not automatically mean an IP problem.**

Sometimes the most useful troubleshooting question is simply:

> **"Do we have link?"**

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ COMPLETE

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES
✅ COMPLETE
✅ Project 03

🟠 PHASE 4 — NETWORK IMPLEMENTATION

✅ Lesson 17 — Network Cabling & Physical Infrastructure
✅ Lab 17 — Network Cabling & Physical Infrastructure

        ↓

🟡 NEXT:
Lesson 18 — Wireless Networking
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 18 — Wireless Networking**

Next we'll take the same network and remove the cable between the endpoint and switch.

You'll learn about:

```text
Wi-Fi
802.11 Standards
2.4 GHz
5 GHz
6 GHz
Channels
Channel Width
SSIDs
Access Points
Signal Strength
Interference
Roaming
WPA2
WPA3
Wireless Security
Wireless Troubleshooting
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**