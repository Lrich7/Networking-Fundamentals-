# 🏗️ Project 03 — Build a Routed Small-Business Network

Welcome to **Project 03 of Networking Fundamentals**.

You've completed:

> **Phase 3 — Switching, Routing & Services**

You now know enough to build something that starts to resemble a real small-business network.

This project combines:

```text
Switching
+
VLANs
+
Subnetting
+
Inter-VLAN Routing
+
DHCP
+
DNS
+
NAT/PAT
+
Internet Connectivity
+
Troubleshooting
```

This time, you will receive:

> **Business requirements instead of a complete step-by-step configuration.**

---

# 🎯 Project Objectives

You will:

- Design a small-business network
- Create multiple VLANs
- Create an IPv4 addressing plan
- Configure access ports
- Configure trunks
- Configure inter-VLAN routing
- Configure DHCP
- Configure DNS
- Configure NAT/PAT
- Configure an ISP connection
- Provide simulated Internet access
- Verify end-to-end communication
- Use Cisco verification commands
- Troubleshoot intentionally broken configurations
- Document the finished network

---

# 🎓 Network+ Skills Reinforced

This project reinforces:

- Ethernet
- Switching
- VLANs
- 802.1Q
- Trunking
- IPv4
- Subnetting
- Default gateways
- Routing
- DHCP
- DNS
- NAT
- PAT
- TCP/IP
- Ports
- Network documentation
- Troubleshooting

---

# ⏱️ Estimated Time

**2–3 hours**

It is completely reasonable to complete this project across multiple sessions.

---

# 🏢 PROJECT SCENARIO

You are the IT specialist for:

> **Northstar Services**

Northstar is a small company preparing a new office.

The office currently needs separate networks for:

```text
Employees

Servers

IT Management
```

The company also needs:

- Automatic employee addressing
- Internal DNS
- Inter-VLAN routing
- Internet connectivity
- NAT/PAT
- A documented addressing plan
- Basic troubleshooting documentation

---

# 📊 BUSINESS REQUIREMENTS

Management expects approximately:

```text
Employees:
Up to 50 devices

Servers:
Up to 20 devices

IT / Management:
Up to 10 devices
```

You have been given:

```text
192.168.100.0/24
```

for internal addressing.

Your job is to subnet it appropriately.

---

# 🧠 DESIGN REQUIREMENT

Use VLSM principles.

Choose subnet sizes that meet the requirements without simply assigning `/24` everywhere.

Determine appropriate prefixes for:

```text
50 hosts

20 hosts

10 hosts
```

---

# ✏️ PART 1 — CALCULATE SUBNET SIZES

Complete:

| Network | Required Hosts | Prefix | Usable Hosts |
|---|---:|---:|---:|
| Employees | 50 | | |
| Servers | 20 | | |
| IT Management | 10 | | |

---

# 🛑 CHECKPOINT 1

Calculate before continuing.

---

# ✅ CHECKPOINT 1 ANSWER

A practical design is:

| Network | Required | Prefix | Traditional Usable |
|---|---:|---:|---:|
| Employees | 50 | `/26` | 62 |
| Servers | 20 | `/27` | 30 |
| IT Management | 10 | `/28` | 14 |

---

# 🧮 PART 2 — CREATE THE VLSM PLAN

Starting with:

```text
192.168.100.0/24
```

allocate the largest network first.

Determine:

```text
Employee Network

Server Network

IT Network
```

---

# 🛑 CHECKPOINT 2

Try it yourself first.

---

# ✅ CHECKPOINT 2 ANSWER

Use:

## VLAN 10 — EMPLOYEES

```text
192.168.100.0/26
```

Usable:

```text
192.168.100.1
through
192.168.100.62
```

Broadcast:

```text
192.168.100.63
```

---

## VLAN 20 — SERVERS

```text
192.168.100.64/27
```

Usable:

```text
192.168.100.65
through
192.168.100.94
```

Broadcast:

```text
192.168.100.95
```

---

## VLAN 30 — IT-MGMT

```text
192.168.100.96/28
```

Usable:

```text
192.168.100.97
through
192.168.100.110
```

Broadcast:

```text
192.168.100.111
```

---

# 🏷️ PART 3 — VLAN PLAN

Use:

| VLAN | Name | Network |
|---:|---|---|
| 10 | EMPLOYEES | 192.168.100.0/26 |
| 20 | SERVERS | 192.168.100.64/27 |
| 30 | IT-MGMT | 192.168.100.96/28 |

---

# 🚪 DEFAULT GATEWAY PLAN

Use the first usable address in each subnet as its gateway.

Therefore:

```text
VLAN 10
192.168.100.1

VLAN 20
192.168.100.65

VLAN 30
192.168.100.97
```

---

# 🏗️ PART 4 — BUILD THE TOPOLOGY

Build approximately:

```text
PC-EMP01 ─┐
PC-EMP02 ─┼── SW-01 ───────┐
PC-EMP03 ─┘                 │
                            │
                          TRUNK
                            │
PC-IT01 ───── SW-02 ────────┘
                 │
                 ├── DNS-01
                 │
                 └── APP-01

                    │
                    │ TRUNK
                    ▼

                  R-EDGE
                    │
                    │
                    ▼
                  R-ISP
                    │
                    ▼
                 WEB-EXT
```

You may adjust exact switch ports.

The logical requirements matter more than matching a picture perfectly.

---

# 🧰 Required Devices

Use at least:

```text
2 Switches

1 Edge Router

1 ISP Router

3 Employee PCs

1 IT PC

1 DNS Server

1 Internal Application Server

1 External Web Server
```

---

# 🔧 PART 5 — CREATE THE VLANS

On both switches, create:

```text
VLAN 10
EMPLOYEES

VLAN 20
SERVERS

VLAN 30
IT-MGMT
```

You should know the Cisco commands from Lesson 12.

Use the lesson if you need a refresher.

---

# 🔌 PART 6 — ASSIGN ACCESS PORTS

Assign:

```text
Employee PCs
→ VLAN 10

DNS-01
APP-01
→ VLAN 20

PC-IT01
→ VLAN 30
```

Verify with:

```text
show vlan brief
```

---

# 🔗 PART 7 — CONFIGURE TRUNKS

Configure required switch-to-switch and switch-to-router links as trunks.

Verify:

```text
show interfaces trunk
```

The trunks must carry:

```text
VLAN 10
VLAN 20
VLAN 30
```

---

# 🛣️ PART 8 — CONFIGURE INTER-VLAN ROUTING

Use:

> **Router-on-a-Stick**

on R-EDGE.

Create subinterfaces for:

```text
VLAN 10

VLAN 20

VLAN 30
```

Use:

```text
192.168.100.1

192.168.100.65

192.168.100.97
```

as the respective gateway addresses.

---

# 💡 Reminder

Conceptually:

```text
interface g0/0.10
 encapsulation dot1Q 10
 ip address ...

interface g0/0.20
 encapsulation dot1Q 20
 ip address ...

interface g0/0.30
 encapsulation dot1Q 30
 ip address ...
```

The physical parent interface must also be enabled.

---

# 🧪 PART 9 — VERIFY ROUTING

Before adding DHCP or DNS, statically configure one endpoint in each VLAN.

Verify:

```text
Employee
→ Server

Employee
→ IT

IT
→ Server
```

All should route successfully.

If not, stop and troubleshoot.

---

# 🧠 Troubleshooting Areas

Check:

```text
VLAN membership

Trunks

IP address

Subnet mask

Default gateway

Router subinterface

802.1Q VLAN ID

Interface status
```

---

# 📦 PART 10 — CONFIGURE DHCP

Employee devices must receive addresses automatically.

Configure DHCP for:

```text
VLAN 10
```

The pool must provide:

- IPv4 address
- Subnet mask
- Default gateway
- DNS server

---

# 🗄️ DNS Server Address

Assign DNS-01 a static address in VLAN 20.

A suggested address is:

```text
192.168.100.70
```

Gateway:

```text
192.168.100.65
```

---

# 📦 DHCP REQUIREMENT

Employee clients should receive:

```text
Network:
192.168.100.0/26

Gateway:
192.168.100.1

DNS:
192.168.100.70
```

Exclude addresses needed for infrastructure.

---

# 🧪 PART 11 — VERIFY DHCP

Set employee PCs to:

> **DHCP**

Verify they receive valid addresses.

Record:

| Device | Address | Gateway | DNS |
|---|---|---|---|
| PC-EMP01 | | | |
| PC-EMP02 | | | |
| PC-EMP03 | | | |

---

# 🌐 PART 12 — CONFIGURE INTERNAL DNS

On DNS-01:

```text
Services
   ↓
DNS
   ↓
On
```

Create:

```text
app.northstar.local
```

pointing to APP-01.

Suggested APP-01 address:

```text
192.168.100.71
```

---

# 🌐 PART 13 — CONFIGURE APP-01

Use:

```text
IP:
192.168.100.71

Mask:
255.255.255.224

Gateway:
192.168.100.65

DNS:
192.168.100.70
```

Enable:

```text
HTTP
```

---

# 🧪 PART 14 — TEST INTERNAL DNS

From an employee PC, try:

```text
app.northstar.local
```

Expected:

> **Internal application loads by name**

This proves several systems are working together:

```text
DHCP
   ↓
DNS Configuration
   ↓
Routing
   ↓
DNS Resolution
   ↓
HTTP
```

---

# 🌎 PART 15 — BUILD THE OUTSIDE NETWORK

Connect R-EDGE to R-ISP.

Use:

```text
203.0.113.0/30
```

Suggested:

```text
R-ISP:
203.0.113.1

R-EDGE:
203.0.113.2
```

---

# 🌐 PART 16 — EXTERNAL SERVER

Create:

```text
WEB-EXT
```

behind R-ISP.

Use:

```text
198.51.100.10/24
```

Gateway:

```text
198.51.100.1
```

Enable HTTP.

---

# 🛣️ PART 17 — CONFIGURE DEFAULT ROUTING

R-EDGE needs:

```text
0.0.0.0/0
```

toward:

```text
203.0.113.1
```

Do not add private LAN routes to the simulated ISP.

---

# 🔄 PART 18 — CONFIGURE NAT/PAT

R-EDGE must translate internal networks.

Your NAT design must include:

```text
ip nat inside
```

on the LAN-facing side.

And:

```text
ip nat outside
```

on the ISP-facing side.

---

# 📋 NAT REQUIREMENT

PAT must support all three internal networks:

```text
192.168.100.0/26

192.168.100.64/27

192.168.100.96/28
```

You may create ACL entries that match the internal networks.

Then configure:

> **PAT / overload**

using R-EDGE's outside interface.

---

# 🧪 PART 19 — VERIFY INTERNET ACCESS

From:

```text
PC-EMP01
```

test:

```text
198.51.100.10
```

Then:

```text
PC-IT01
```

Then:

```text
APP-01
```

All should be able to reach the simulated external network if your design allows it.

---

# 🔍 PART 20 — INSPECT NAT

On R-EDGE:

```text
show ip nat translations
```

Then:

```text
show ip nat statistics
```

Record:

```text
Inside Global Address:

________________________________


Inside Local Address:

________________________________
```

---

# 🏆 MAJOR CHECKPOINT

Your network should now provide:

```text
VLAN Segmentation
        ↓
Inter-VLAN Routing
        ↓
DHCP
        ↓
DNS
        ↓
Internal Application Access
        ↓
Default Routing
        ↓
PAT
        ↓
External Connectivity
```

That is a substantial jump from Project 01.

---

# 💥 PART 21 — TROUBLESHOOTING CHALLENGE 1

Break one employee switch port by assigning it to:

```text
VLAN 20
```

instead of:

```text
VLAN 10
```

Do not immediately fix it.

Diagnose using:

```text
show vlan brief
```

Document the symptoms.

Then repair it.

---

# 💥 PART 22 — TROUBLESHOOTING CHALLENGE 2

Break the switch-to-router trunk.

For example, incorrectly configure the port as an access port.

Investigate:

```text
show interfaces trunk
```

Observe how multiple VLANs are affected.

Repair the trunk.

---

# 💥 PART 23 — TROUBLESHOOTING CHALLENGE 3

Change the DHCP DNS option to:

```text
192.168.100.75
```

instead of:

```text
192.168.100.70
```

Renew/reconfigure an employee client.

Test:

```text
Direct IP
vs.
Hostname
```

Expected pattern:

```text
IP Communication
✅

Name Resolution
❌
```

Find the root cause and repair DHCP.

---

# 💥 PART 24 — TROUBLESHOOTING CHALLENGE 4

Change:

```text
app.northstar.local
```

to point at an incorrect address.

Test name resolution.

Notice:

```text
DNS responds
```

but:

```text
DNS data is wrong
```

Repair the record.

---

# 💥 PART 25 — TROUBLESHOOTING CHALLENGE 5

Break the NAT ACL so it no longer matches:

```text
VLAN 10
```

Employee clients should still be able to:

```text
Reach internal networks
```

but external connectivity should fail.

Investigate:

```text
show access-lists

show ip nat translations

show ip nat statistics
```

Repair PAT.

---

# 💥 PART 26 — TROUBLESHOOTING CHALLENGE 6

Remove R-EDGE's default route.

Test:

```text
Internal communication
```

then:

```text
External communication
```

Expected:

```text
Internal
✅

External
❌
```

Use:

```text
show ip route
```

to identify the missing route.

Repair it.

---

# 🧭 PART 27 — FULL TROUBLESHOOTING WORKFLOW

For an employee who reports:

> "The network doesn't work."

Do not randomly change settings.

Work through:

```text
Physical Link
        ↓
Correct VLAN
        ↓
DHCP Address
        ↓
Subnet Mask
        ↓
Default Gateway
        ↓
Reach Gateway
        ↓
Inter-VLAN Routing
        ↓
DNS Configuration
        ↓
DNS Resolution
        ↓
Default Route
        ↓
NAT/PAT
        ↓
External Service
```

---

# 📋 PART 28 — FINAL ADDRESSING TABLE

Document:

| Device/Network | VLAN | Address/Network | Gateway |
|---|---:|---|---|
| Employees | 10 | | |
| Servers | 20 | | |
| IT Management | 30 | | |
| DNS-01 | 20 | | |
| APP-01 | 20 | | |
| PC-IT01 | 30 | | |
| R-EDGE Outside | — | | |
| R-ISP | — | | |
| WEB-EXT | — | | |

---

# 📋 PART 29 — SERVICES TABLE

Document:

| Service | Device | Address |
|---|---|---|
| DHCP | | |
| DNS | | |
| Internal HTTP | | |
| NAT/PAT | | |
| Inter-VLAN Routing | | |
| External HTTP | | |

---

# 🗺️ PART 30 — CREATE A NETWORK DIAGRAM

Your final documentation should show:

```text
Device Names

VLAN IDs

Subnet Addresses

Default Gateways

Trunks

Router

ISP

Servers
```

A simple Packet Tracer screenshot is fine for your own records.

Later in the course, we'll build more formal network documentation.

---

# 📝 PART 31 — TROUBLESHOOTING REPORT

Choose one challenge and document:

```text
Problem:

________________________________


Initial Symptoms:

________________________________


Scope:

One Device / One VLAN / Multiple VLANs / Entire Network


Tools Used:

________________________________


Commands Used:

________________________________


What Worked:

________________________________


What Failed:

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

# 🧠 PROJECT REVIEW

You should now be able to explain:

### Why use VLANs?

> To create separate logical Layer 2 broadcast domains and segment the network.

### Why does each VLAN need a gateway?

> To communicate with other IP networks.

### What does DHCP provide?

> Automatic IP configuration such as address, mask, gateway, and DNS.

### What does DNS provide?

> Name resolution.

### What does routing provide?

> Communication between different IP networks.

### What does PAT provide?

> Translation that allows many private clients to share outside IPv4 addressing.

---

# 🎓 Network+ Challenge 1

A client receives:

```text
IP:
192.168.100.20

Gateway:
192.168.100.1

DNS:
192.168.100.75
```

The actual DNS server is:

```text
192.168.100.70
```

What should you investigate?

> **DHCP DNS configuration**

---

# 🎓 Network+ Challenge 2

Clients in VLAN 10 cannot reach clients in VLAN 20, but devices within each VLAN communicate normally.

What area should you investigate?

> **Inter-VLAN routing**

---

# 🎓 Network+ Challenge 3

VLAN 10 clients can reach internal servers but cannot reach the simulated Internet. VLAN 20 works normally.

What should you investigate?

> **NAT/PAT matching for VLAN 10, along with any VLAN-specific routing/configuration affecting external traffic.**

---

# 🎓 Network+ Challenge 4

A client can reach:

```text
192.168.100.71
```

but not:

```text
app.northstar.local
```

What should you investigate?

> **DNS**

---

# 🎓 Network+ Challenge 5

All internal communication works, but every VLAN loses external connectivity.

The NAT configuration is unchanged.

What routing item should you check?

> **The default route toward the ISP**

---

# 🏆 PROJECT COMPLETION CHECKLIST

- [ ] I created three VLANs
- [ ] I created a VLSM addressing plan
- [ ] I configured access ports
- [ ] I configured trunks
- [ ] I configured router-on-a-stick
- [ ] I verified inter-VLAN routing
- [ ] I configured DHCP
- [ ] Employee clients receive automatic addressing
- [ ] DHCP provides the correct gateway
- [ ] DHCP provides the correct DNS server
- [ ] I configured an internal DNS server
- [ ] I created an internal DNS record
- [ ] I configured an internal web/application server
- [ ] Clients can access the internal server by name
- [ ] I configured an ISP connection
- [ ] I configured a default route
- [ ] I configured NAT/PAT
- [ ] Multiple VLANs can reach the external network
- [ ] I examined NAT translations
- [ ] I troubleshot a VLAN problem
- [ ] I troubleshot a trunk problem
- [ ] I troubleshot a DHCP problem
- [ ] I troubleshot a DNS problem
- [ ] I troubleshot a NAT problem
- [ ] I troubleshot a routing problem
- [ ] I documented the network
- [ ] I completed a troubleshooting report

---

# 💾 Save Your Project

Save locally as:

```text
project-03-routed-small-business-network.pkt
```

You do not need to upload the completed Packet Tracer file to the public repository.

---

# 🏆 Project 03 Complete

You have now built a network containing:

```text
Multiple VLANs
      ↓
Multiple IP Networks
      ↓
802.1Q Trunks
      ↓
Inter-VLAN Routing
      ↓
DHCP
      ↓
DNS
      ↓
Internal Services
      ↓
Default Routing
      ↓
NAT/PAT
      ↓
External Connectivity
```

You are no longer working with isolated networking concepts.

You're starting to see:

> **How the pieces form an actual network.**

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE
✅ Project 01

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ COMPLETE
✅ Project 02

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES
✅ COMPLETE
✅ Project 03 — Build a Routed Small-Business Network

        ↓

🟠 NEXT:
PHASE 4 — NETWORK IMPLEMENTATION

Lesson 17
Network Cabling & Physical Infrastructure
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 17 — Network Cabling and Physical Infrastructure**

So far, Packet Tracer cables have been easy:

```text
Click Cable
      ↓
Connect Device
      ↓
Link Turns Green
```

Real networks aren't that simple.

Next you'll learn about:

- Copper cabling
- Fiber
- Ethernet standards
- Cat5e
- Cat6
- Cat6a
- RJ45
- Twisted pair
- Straight-through cables
- Crossover cables
- Fiber connectors
- Multimode vs. single-mode
- SFP/SFP+ transceivers
- Patch panels
- MDFs and IDFs
- Racks
- Cable management
- PoE
- Cable testing
- Physical-layer troubleshooting

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](README.md)**

➡️ **[Return to Main README](../README.md)**