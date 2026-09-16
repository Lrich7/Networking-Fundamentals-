# 🏆 Project 04 — Small Business Network Capstone

Welcome to the **final project of Networking Fundamentals**.

This project brings together everything you have learned throughout the course.

Unlike previous labs:

> **You will NOT be given every configuration command.**

You have been hired as the network technician for a fictional company:

# 🏢 Northstar Services

Northstar is opening a new office.

Your job is to:

```text
DESIGN

BUILD

CONFIGURE

SECURE

TEST

TROUBLESHOOT

DOCUMENT
```

the network.

---

# 🎯 Project Objectives

You will demonstrate your ability to:

- Design a small-business network
- Create an IP addressing plan
- Subnet networks
- Create VLANs
- Configure switching
- Configure trunks
- Configure inter-VLAN routing
- Configure DHCP
- Configure DNS
- Configure servers
- Configure wireless connectivity
- Separate corporate and guest wireless
- Connect to a simulated WAN
- Configure routing
- Apply basic security controls
- Test connectivity
- Establish a baseline
- Troubleshoot multiple failures
- Document the finished network
- Create an incident report
- Explain your design decisions

---

# 🧰 Required Tool

Use:

> **Cisco Packet Tracer**

---

# ⏱️ Estimated Time

Plan for approximately:

> **2–4 hours**

Do not rush.

This is a capstone.

---

# 🏢 BUSINESS REQUIREMENTS

Northstar Services has approximately:

```text
40 Employees

10 Servers / Infrastructure Devices

25 Guest Devices

10 Network Management Devices
```

The company requires separate networks for:

```text
Employees

Servers

Guests

Management
```

---

# 🗺️ REQUIREMENT 1 — BUILD THE NETWORK

Your network must include at least:

```text
1 Edge Router

2 Switches

1 Wireless Access Point

1 Server

4 Employee PCs

2 Guest Wireless Clients

1 Simulated ISP Router
```

You may add additional devices if desired.

---

# 🗺️ Suggested Physical Design

You may use:

```text
                    INTERNET / ISP
                          │
                          ▼
                       R-EDGE
                          │
                          ▼
                       SW-CORE
                       /     \
                      /       \
                SW-ACCESS     SERVER
                   │
              Employee PCs
                   │
                   AP
                 ))) )))
               Wireless
```

You may improve this design.

---

# 🧱 REQUIREMENT 2 — CREATE VLANS

Create at least:

| VLAN | Purpose |
|---:|---|
| 10 | Employees |
| 20 | Servers |
| 50 | Guests |
| 99 | Management |

Choose appropriate VLAN names.

---

# 🧮 REQUIREMENT 3 — DESIGN THE IP PLAN

You are given:

```text
192.168.100.0/24
```

Your challenge:

> **Subnet this network to support the required VLANs.**

Requirements:

```text
Employees:
40 devices

Servers:
10 devices

Guests:
25 devices

Management:
10 devices
```

---

# 🧠 Your Task

Determine appropriate subnet sizes.

Document:

| VLAN | Network | Prefix | Mask | Gateway | Usable Range | Broadcast |
|---:|---|---|---|---|---|---|
| 10 | | | | | | |
| 20 | | | | | | |
| 50 | | | | | | |
| 99 | | | | | | |

---

# 💡 Hint

Remember:

```text
/26
/27
/28
```

support different numbers of usable hosts.

Use what you learned about:

> **VLSM — Variable Length Subnet Masking**

---

# 🚫 Do Not Continue Blindly

Before configuring devices:

> **Finish the IP addressing table.**

A good network begins with a good addressing plan.

---

# 🔀 REQUIREMENT 4 — SWITCHING

Configure:

- VLANs
- Access ports
- Trunks
- Appropriate VLAN assignments

Verify using commands such as:

```text
show vlan brief
```

and:

```text
show interfaces trunk
```

---

# 🛣️ REQUIREMENT 5 — INTER-VLAN ROUTING

Devices in authorized VLANs must communicate through a Layer 3 device.

You may use:

```text
Router-on-a-Stick
```

or another supported Packet Tracer Layer 3 design.

---

# 📦 REQUIREMENT 6 — DHCP

Employee and guest devices must receive addressing automatically.

DHCP must provide:

```text
IP Address

Subnet Mask

Default Gateway

DNS Server
```

Infrastructure devices may use static addresses.

---

# 🖥️ REQUIREMENT 7 — SERVER

Configure at least one server.

The server must provide:

```text
DNS

HTTP
```

Create a DNS record:

```text
intranet.northstar.local
```

pointing to the internal web server.

---

# 🌐 REQUIREMENT 8 — WAN

Connect the edge router to:

> **ISP-RTR**

Use a separate point-to-point network.

Example:

```text
10.0.0.0/30
```

You may use another appropriate subnet.

---

# 🛣️ REQUIREMENT 9 — DEFAULT ROUTING

Northstar's edge router must know how to send unknown external traffic toward:

> **ISP-RTR**

Configure the appropriate route.

---

# 📡 REQUIREMENT 10 — CORPORATE WI-FI

Create:

```text
Northstar-Corp
```

Corporate wireless clients should receive access appropriate for employee devices.

Use secure wireless authentication supported by your Packet Tracer equipment.

---

# 👥 REQUIREMENT 11 — GUEST WI-FI

Create or logically represent:

```text
Northstar-Guest
```

Guest devices must be separated from protected corporate resources.

---

# 🛡️ REQUIREMENT 12 — GUEST SECURITY

Guest devices should:

```text
✓ Receive DHCP

✓ Reach permitted external resources

X Reach protected server resources

X Reach management resources
```

Implement appropriate:

```text
ACL

or

Routing / Security Policy
```

to enforce the design.

---

# 🔐 REQUIREMENT 13 — DEVICE SECURITY

Implement reasonable basic security.

At minimum:

- Disable unused switch ports
- Use secure administrative access concepts
- Avoid unnecessary active ports
- Save device configurations
- Protect management access

Optional:

- SSH
- Local administrator account
- Encrypted passwords
- Login banner
- Management VLAN
- Port security

---

# 🔐 REQUIREMENT 14 — MANAGEMENT NETWORK

Network infrastructure should use:

```text
VLAN 99
```

for management where practical.

Document which devices have management addresses.

---

# 📊 REQUIREMENT 15 — ESTABLISH A BASELINE

Before troubleshooting, create a baseline.

Record:

| Test | Normal Result |
|---|---|
| Employee DHCP | |
| Guest DHCP | |
| Employee Gateway | |
| Server Gateway | |
| DNS Resolution | |
| HTTP | |
| Inter-VLAN Routing | |
| WAN | |
| Guest → Server | |
| Switch Trunks | |

---

# 📸 CHECKPOINT

Save your working Packet Tracer network as:

```text
project-04-working-baseline.pkt
```

Do not continue until:

> **Every expected test passes.**

---

# 📋 REQUIREMENT 16 — NETWORK DOCUMENTATION

Create a device inventory.

| Device | Type | Management IP | Location | Purpose |
|---|---|---|---|---|
| R-EDGE | Router | | | |
| SW-CORE | Switch | | | |
| SW-ACCESS | Switch | | | |
| AP-01 | AP | | | |
| SERVER-01 | Server | | | |

Add your other devices.

---

# 🗺️ REQUIREMENT 17 — LOGICAL DIAGRAM

Document your logical design.

Example format:

```text
                  ISP
                   │
                   ▼
                R-EDGE
                   │
                   ▼
                SW-CORE
               /   |   \
              /    |    \
          VLAN10 VLAN20 VLAN50
             │      │      │
        Employees Servers Guests
```

Your actual diagram should reflect your design.

---

# 🔌 REQUIREMENT 18 — PORT DOCUMENTATION

Create:

| Switch | Port | Connected Device | VLAN | Purpose |
|---|---|---|---:|---|
| SW-CORE | | | | |
| SW-CORE | | | | |
| SW-ACCESS | | | | |

Document every important connection.

---

# 🧠 REQUIREMENT 19 — EXPLAIN YOUR DESIGN

Answer:

### Why did you separate employees and servers?

```text
____________________________________

____________________________________
```

### Why did you create a guest VLAN?

```text
____________________________________

____________________________________
```

### Why is the management network separate?

```text
____________________________________

____________________________________
```

### Why did you choose your subnet sizes?

```text
____________________________________

____________________________________
```

---

# 💥 TROUBLESHOOTING PHASE

Your network is now operational.

You are going to simulate support incidents.

For each ticket:

> **Break the specified configuration intentionally, troubleshoot it, and document the repair.**

---

# 🎫 TICKET 1 — ONE EMPLOYEE OFFLINE

Symptoms:

```text
PC-EMP1:
No Network

Everyone Else:
Working
```

Create a Layer 1 failure.

Troubleshoot it.

Document:

```text
Scope:

Theory:

Test:

Root Cause:

Solution:

Verification:
```

---

# 🎫 TICKET 2 — WRONG NETWORK

Symptoms:

```text
PC-EMP2 receives an address
but
it is on the Guest subnet.
```

Create a VLAN assignment problem.

Troubleshoot it without immediately looking at the configuration you changed.

---

# 🎫 TICKET 3 — EMPLOYEES HAVE NO DHCP

Symptoms:

```text
All Employee PCs:
No valid DHCP configuration

Guests:
Working
```

Create a DHCP configuration problem.

Determine why only:

```text
VLAN 10
```

is affected.

---

# 🎫 TICKET 4 — SERVER NAME DOESN'T WORK

Symptoms:

```text
ping <server-IP>
✓

intranet.northstar.local
X
```

Create a DNS problem.

Troubleshoot it.

---

# 🎫 TICKET 5 — SERVER VLAN UNREACHABLE

Symptoms:

```text
Employees:
Gateway works

Server:
Unreachable
```

Create a routing or VLAN 20 problem.

Use:

```text
show ip interface brief

show ip route

show vlan brief

show interfaces trunk
```

as appropriate.

---

# 🎫 TICKET 6 — MULTIPLE VLANS FAIL

Create a trunk problem.

Symptoms should affect more than one VLAN.

Use scope to identify that this is probably not:

```text
One PC
```

---

# 🎫 TICKET 7 — INTERNET/WAN DOWN

Symptoms:

```text
Internal Network:
Works

Internal DNS:
Works

Internal Server:
Works

External Connectivity:
Fails
```

Create a WAN failure.

Troubleshoot the path toward ISP-RTR.

---

# 🎫 TICKET 8 — SECURITY INCIDENT

Symptoms:

```text
Guest Device
      ↓
Can Reach
      ↓
Protected Server
```

This is not a connectivity outage.

It is a:

> **Security-control failure**

Find and repair the segmentation problem.

---

# 🎫 TICKET 9 — MANAGEMENT EXPOSURE

Imagine a guest device can access the management network.

Determine what control should prevent this.

Document your recommended correction.

---

# 🎫 TICKET 10 — MYSTERY INCIDENT

Have someone else modify one network setting without telling you what they changed.

If working alone:

1. Save your baseline.
2. Choose one configuration area randomly.
3. Make one change.
4. Wait several minutes or work on another section.
5. Return and troubleshoot from symptoms.

Possible areas:

```text
Cable

VLAN

Trunk

Gateway

DHCP

DNS

Route

ACL

WAN Interface
```

---

# 🧭 TROUBLESHOOTING RULE

For every ticket, use:

```text
IDENTIFY
   ↓
SCOPE
   ↓
THEORY
   ↓
TEST
   ↓
PLAN
   ↓
FIX
   ↓
VERIFY
   ↓
DOCUMENT
```

---

# 🚫 Do Not Troubleshoot Like This

```text
Change random setting
        ↓
Didn't work
        ↓
Change another setting
        ↓
Reboot everything
```

Instead:

> **Use evidence.**

---

# 📝 INCIDENT REPORT TEMPLATE

Complete at least **three full incident reports**.

```text
INCIDENT NUMBER:

________________________________


DATE/TIME:

________________________________


REPORTED PROBLEM:

________________________________


USERS AFFECTED:

________________________________


SCOPE:

________________________________


WHAT STILL WORKED:

________________________________


WHAT FAILED:

________________________________


INITIAL THEORY:

________________________________


TESTS PERFORMED:

________________________________


TOOLS / COMMANDS USED:

________________________________


ROOT CAUSE:

________________________________


CORRECTIVE ACTION:

________________________________


VERIFICATION:

________________________________


PREVENTIVE ACTION:

________________________________


ESCALATION REQUIRED?

YES / NO


IF YES, WHY?

________________________________
```

---

# 📊 MONITORING CHALLENGE

Assume your monitoring system normally reports:

```text
WAN Latency:
20 ms

Packet Loss:
0%

WAN Utilization:
25%

Router CPU:
20%
```

It now reports:

```text
WAN Latency:
140 ms

Packet Loss:
6%

WAN Utilization:
98%

Router CPU:
22%
```

---

# 🧠 Questions

### What changed?

```text
________________________________
```

### Which metric remained relatively normal?

```text
________________________________
```

### What might be causing the user complaints?

```text
________________________________
```

### What would you investigate next?

```text
________________________________
```

---

# 📜 LOG ANALYSIS CHALLENGE

You receive:

```text
10:04:01
WAN interface down

10:04:03
VPN tunnel disconnected

10:04:04
External monitoring lost

10:05:12
Users report Internet outage
```

What event occurred first?

```text
________________________________
```

What is the likely relationship between the events?

```text
________________________________

________________________________
```

---

# 🧗 ESCALATION CHALLENGE

You determine:

```text
LAN:
Working

Firewall:
Working

WAN Interface:
Up

ISP Gateway:
Unreachable

No Local Changes:
Confirmed
```

What information should you provide to the ISP?

Write your escalation:

```text
________________________________

________________________________

________________________________

________________________________
```

---

# 📋 FINAL TECHNICAL VERIFICATION

Complete this table:

| Test | Expected | Actual | Pass? |
|---|---|---|---|
| Employee DHCP | Valid address | | |
| Guest DHCP | Valid address | | |
| Employee → Gateway | Reachable | | |
| Employee → Server | Reachable | | |
| Employee DNS | Resolves | | |
| Employee HTTP | Loads | | |
| Guest → Server | Blocked | | |
| Guest → Management | Blocked | | |
| WAN | Reachable | | |
| Trunks | Operational | | |
| VLANs | Correct | | |
| Unused Ports | Disabled | | |

---

# 📁 FINAL PROJECT FILES

Your finished project should include:

```text
project-04-final.pkt

Network Diagram

IP Addressing Table

VLAN Table

Device Inventory

Switch Port Table

Baseline Results

Incident Reports

Final Verification Checklist
```

If storing everything in GitHub, your project folder might look like:

```text
projects/
│
├── project-04-small-business-network-capstone.md
│
└── packet-tracer/
    └── project-04-final.pkt
```

---

# 🏆 FINAL PROJECT CHECKLIST

## Design

- [ ] I created a logical network design
- [ ] I created an addressing plan
- [ ] I used VLSM
- [ ] I documented subnet ranges
- [ ] I created a VLAN plan

## Switching

- [ ] I created VLANs
- [ ] I configured access ports
- [ ] I configured trunks
- [ ] I verified VLAN membership

## Routing

- [ ] I configured inter-VLAN routing
- [ ] I configured WAN routing
- [ ] I verified routing tables

## Services

- [ ] I configured DHCP
- [ ] I configured DNS
- [ ] I configured HTTP
- [ ] I tested name resolution

## Wireless

- [ ] I created corporate wireless
- [ ] I created or represented guest wireless
- [ ] I secured wireless access

## Security

- [ ] I segmented guests
- [ ] I protected server resources
- [ ] I protected management resources
- [ ] I disabled unused ports
- [ ] I saved configurations

## Monitoring

- [ ] I created a baseline
- [ ] I interpreted monitoring metrics
- [ ] I analyzed logs
- [ ] I identified abnormal behavior

## Troubleshooting

- [ ] I solved Ticket 1
- [ ] I solved Ticket 2
- [ ] I solved Ticket 3
- [ ] I solved Ticket 4
- [ ] I solved Ticket 5
- [ ] I solved Ticket 6
- [ ] I solved Ticket 7
- [ ] I solved Ticket 8
- [ ] I completed the security analysis
- [ ] I completed the mystery incident
- [ ] I completed at least three incident reports

## Documentation

- [ ] I documented devices
- [ ] I documented IP addresses
- [ ] I documented VLANs
- [ ] I documented switch ports
- [ ] I documented the topology
- [ ] I completed final verification

---

# 🎓 FINAL REFLECTION

Answer these without looking back through the lessons if possible.

### 1. What happens when a computer communicates with a device on the same subnet?

```text
________________________________

________________________________
```

### 2. What happens when the destination is on another subnet?

```text
________________________________

________________________________
```

### 3. What role does ARP play?

```text
________________________________
```

### 4. What role does DHCP play?

```text
________________________________
```

### 5. What role does DNS play?

```text
________________________________
```

### 6. Why do we use VLANs?

```text
________________________________
```

### 7. Why does a router need a routing table?

```text
________________________________
```

### 8. Why is a default gateway required?

```text
________________________________
```

### 9. What is the difference between bandwidth and latency?

```text
________________________________
```

### 10. Why establish a baseline?

```text
________________________________
```

### 11. Why should guest devices be segmented?

```text
________________________________
```

### 12. Why should unused switch ports be disabled?

```text
________________________________
```

### 13. Why are configuration backups important?

```text
________________________________
```

### 14. What is the first thing you should determine when troubleshooting?

```text
________________________________
```

### 15. Why document the solution?

```text
________________________________
```

---

# 🏁 PROJECT 04 COMPLETE

If you successfully completed this project, you have worked through the complete path:

```text
END DEVICE
    │
    ▼
PHYSICAL CONNECTION
    │
    ▼
SWITCH
    │
    ▼
VLAN
    │
    ▼
IP ADDRESS
    │
    ▼
DEFAULT GATEWAY
    │
    ▼
ROUTER
    │
    ▼
FIREWALL / ACL
    │
    ▼
WAN
    │
    ▼
REMOTE NETWORK
    │
    ▼
APPLICATION
```

You have also worked with:

```text
Ethernet

MAC Addresses

ARP

IPv4

Subnetting

IPv6 Concepts

DHCP

DNS

Switching

VLANs

Trunking

Routing

Wireless

WAN

VPN Concepts

Network Security

Monitoring

Logs

Troubleshooting

Documentation
```

---

# 🏆 NETWORKING FUNDAMENTALS COMPLETE

```text
┌──────────────────────────────────────────────┐
│                                              │
│          NETWORKING FUNDAMENTALS             │
│                                              │
│              COURSE COMPLETE                 │
│                                              │
│               Lessons 1–20                   │
│                                              │
│              Labs 1–20                       │
│                                              │
│             Projects 1–4                     │
│                                              │
└──────────────────────────────────────────────┘
```

But this is not really the end.

You now have the foundation needed to move deeper into:

```text
CompTIA Network+ N10-009

Cisco Networking

Microsoft Azure Networking

Network Security

Firewalls

VPNs

Cloud Networking

Enterprise Networking
```

Most importantly, when someone says:

> **"The network isn't working."**

you now know how to start answering the much more useful question:

> **"Which part of the network isn't working?"**

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](README.md)**

➡️ **[Return to Main README](../README.md)**