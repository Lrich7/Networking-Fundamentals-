# 📘 Lesson 14 — DHCP

Welcome to **Lesson 14 of Networking Fundamentals**.

So far, we have manually configured devices with information such as:

```text
IP Address
Subnet Mask
Default Gateway
DNS Server
```

For a small Packet Tracer lab, that's manageable.

Imagine doing it manually for:

```text
10 devices
100 devices
1,000 devices
```

Every new laptop, phone, tablet, printer, and workstation would need network settings entered manually.

That doesn't scale.

This is where:

> **DHCP — Dynamic Host Configuration Protocol**

becomes extremely important.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain what DHCP does
- Explain why DHCP is useful
- Understand DHCP clients and servers
- Understand DHCP scopes and address pools
- Explain DHCP leases
- Understand exclusions
- Understand reservations
- Explain common DHCP options
- Understand the DORA process
- Identify DHCP UDP ports
- Explain DHCP broadcasts
- Understand DHCP relay
- Explain why routers create a problem for DHCP broadcasts
- Understand Cisco `ip helper-address`
- Explain APIPA
- Use Windows DHCP troubleshooting commands
- Recognize common DHCP failures
- Troubleshoot DHCP problems

---

# 🎓 Network+ Focus

For **CompTIA Network+ N10-009**, pay particular attention to:

- DHCP
- DHCP scopes
- DHCP leases
- Reservations
- Exclusions
- DHCP options
- DORA
- UDP 67
- UDP 68
- DHCP relay
- APIPA
- Default gateways
- DNS server assignment
- DHCP troubleshooting

A major concept to remember:

> **DHCP automatically provides IP configuration to clients.**

---

# 🌐 What Is DHCP?

DHCP stands for:

> **Dynamic Host Configuration Protocol**

DHCP allows devices to automatically obtain network configuration.

Instead of manually entering:

```text
192.168.10.25
255.255.255.0
192.168.10.1
192.168.10.5
```

the client can ask:

> "Is there a DHCP server that can configure me?"

---

# 🖥️ DHCP Client

A:

> **DHCP Client**

is a device requesting network configuration.

Examples include:

- Windows computers
- Laptops
- Phones
- Tablets
- Printers
- VoIP phones
- Cameras
- IoT devices

---

# 🗄️ DHCP Server

A:

> **DHCP Server**

provides network configuration to DHCP clients.

DHCP services can run on many types of systems, including:

- Windows Server
- Linux servers
- Routers
- Firewalls
- Dedicated network appliances
- Cloud/network platforms

---

# 🧩 What Can DHCP Provide?

DHCP can provide more than just an IP address.

Common information includes:

```text
IP Address
Subnet Mask
Default Gateway
DNS Server
Lease Information
```

Depending on the environment, DHCP can provide additional options as well.

---

# 📋 Example

Instead of manually configuring PC-01:

```text
IP:
192.168.10.25

Mask:
255.255.255.0

Gateway:
192.168.10.1

DNS:
192.168.10.5
```

PC-01 can be configured for:

> **DHCP / Automatic Addressing**

and receive those settings automatically.

---

# 📦 DHCP Scope

A:

> **DHCP Scope**

defines a range of addresses and configuration information available for a particular subnet.

Example:

```text
Network:
192.168.10.0/24
```

DHCP scope:

```text
192.168.10.100
through
192.168.10.200
```

The DHCP server can lease addresses from that range to clients.

---

# 🏊 Address Pool

You may also hear:

> **DHCP Pool**

or:

> **Address Pool**

This generally refers to the addresses available for DHCP assignment.

Example:

```text
192.168.10.100
192.168.10.101
192.168.10.102
...
192.168.10.200
```

---

# 🚫 Exclusions

Suppose your DHCP range is intended to cover:

```text
192.168.10.1
through
192.168.10.254
```

But some addresses are manually assigned.

For example:

```text
192.168.10.1
Router

192.168.10.5
DNS Server

192.168.10.10
Printer
```

We don't want DHCP assigning those addresses to clients.

Those addresses can be:

> **Excluded**

from dynamic assignment.

---

# 🧠 Why Are Exclusions Important?

Without proper planning, DHCP could assign:

```text
192.168.10.10
```

to a laptop while a printer already uses:

```text
192.168.10.10
```

That creates:

> **An IP address conflict**

---

# 📌 DHCP Reservations

Sometimes we want a device to use DHCP but receive:

> **The same IP address every time**

This is where a:

> **DHCP Reservation**

is useful.

---

# 🖨️ Example Reservation

Suppose a printer has MAC address:

```text
AA-BB-CC-DD-EE-FF
```

We create a reservation:

```text
MAC:
AA-BB-CC-DD-EE-FF

Reserved IP:
192.168.10.50
```

When that client requests DHCP configuration, the server can consistently provide:

```text
192.168.10.50
```

---

# 🧠 Static Address vs. Reservation

These are different.

## Static Address

Configured directly on the device:

```text
Device
   ↓
192.168.10.50
manually entered
```

## DHCP Reservation

Device still uses DHCP:

```text
Device
   ↓
DHCP Request
   ↓
DHCP Server
   ↓
Always receives
192.168.10.50
```

---

# 📋 Why Use Reservations?

Reservations can be useful for devices that should have predictable addresses while still being centrally managed through DHCP.

Examples might include:

- Printers
- Cameras
- Certain network appliances
- Specialized devices

Whether a device should use static addressing or a reservation depends on the network design.

---

# ⏱️ DHCP Leases

DHCP usually doesn't permanently give an address to a client.

Instead, the client receives the address for a period of time called a:

> **Lease**

Example:

```text
192.168.10.125
```

might be leased to PC-01 for:

```text
8 hours
```

or:

```text
1 day
```

or another configured duration.

---

# 🧠 Why Use Leases?

Imagine a guest Wi-Fi network.

Hundreds of devices may connect over time.

If every address were permanently assigned, the address pool could eventually be exhausted.

Leases allow addresses to:

> **Return to the pool and be reused.**

---

# 🔄 Lease Renewal

A DHCP client normally attempts to renew its lease before it expires.

Conceptually:

```text
Client Receives Lease
        ↓
Uses Address
        ↓
Attempts Renewal
        ↓
Lease Extended
```

The full renewal process has additional timing behavior, but this level is enough for now.

---

# 📡 DHCP Uses UDP

DHCP uses:

> **UDP**

The primary IPv4 DHCP ports are:

```text
UDP 67
DHCP Server
```

and:

```text
UDP 68
DHCP Client
```

---

# ⭐ Network+ Memory Tip

Remember:

```text
DHCP
67 / 68
UDP
```

A simple memory pattern:

> **Server 67 → Client 68**

---

# 🔄 The DORA Process

One of the most important DHCP concepts is:

> **DORA**

DORA stands for:

```text
Discover
Offer
Request
Acknowledge
```

---

# 1️⃣ DHCP Discover

A new client joins the network.

It doesn't yet have normal IPv4 configuration.

It sends:

> **DHCP Discover**

Conceptually:

```text
CLIENT
"I need an IP configuration!"
        ↓
DHCP DISCOVER
```

The client is trying to locate a DHCP server.

---

# 📢 Why Broadcast?

At this point, the client may not know:

- Its IP address
- The DHCP server's address
- Other network information

So early DHCP communication can rely on:

> **Broadcast traffic**

---

# 2️⃣ DHCP Offer

A DHCP server receives the Discover.

The server responds with:

> **DHCP Offer**

Conceptually:

```text
DHCP SERVER
"I can give you 192.168.10.125."
```

The offer can include network configuration such as:

- Proposed IP
- Subnet information
- Lease information
- Gateway
- DNS information

---

# 3️⃣ DHCP Request

The client responds:

> **DHCP Request**

Conceptually:

```text
CLIENT
"I would like to use that offered address."
```

---

# 4️⃣ DHCP Acknowledge

The server responds:

> **DHCP Acknowledge — DHCPACK**

Conceptually:

```text
SERVER
"Approved. Use that configuration."
```

The client can then use the leased address.

---

# 🧠 DORA

Memorize:

```text
D
Discover

O
Offer

R
Request

A
Acknowledge
```

or:

```text
CLIENT → DISCOVER

SERVER → OFFER

CLIENT → REQUEST

SERVER → ACK
```

---

# 📦 DHCP Options

DHCP can deliver configuration using:

> **DHCP Options**

Some important examples include:

| Option | Purpose |
|---|---|
| Option 1 | Subnet Mask |
| Option 3 | Default Gateway / Router |
| Option 6 | DNS Servers |
| Option 15 | DNS Domain Name |
| Option 51 | IP Address Lease Time |

For Network+, knowing the major configuration DHCP provides is more important than memorizing every possible option number.

---

# 🏢 Example DHCP Design

Employee network:

```text
VLAN 10
192.168.10.0/24
```

Router:

```text
192.168.10.1
```

Servers:

```text
192.168.10.10 - 192.168.10.49
```

DHCP clients:

```text
192.168.10.100 - 192.168.10.200
```

Conceptually:

```text
.1
Gateway

.10-.49
Infrastructure / Servers

.50-.99
Reserved / Future

.100-.200
DHCP Pool
```

This is only an example design.

---

# 🚨 What Happens If DHCP Fails?

A Windows client configured for automatic IPv4 addressing may eventually assign itself an address in:

```text
169.254.0.0/16
```

This is:

> **APIPA — Automatic Private IP Addressing**

---

# 🧠 APIPA Troubleshooting Clue

If you see:

```text
169.254.x.x
```

think:

> **The client probably failed to obtain normal IPv4 configuration from DHCP.**

Possible causes include:

- DHCP server unavailable
- DHCP service stopped
- Client can't reach DHCP server
- VLAN problem
- Switch problem
- DHCP relay missing
- Address pool exhausted
- Network connectivity problem

---

# ⚠️ Important

APIPA does not automatically mean:

> **The DHCP server itself is broken.**

The problem could be anywhere between:

```text
Client
   ↓
Switch
   ↓
VLAN
   ↓
Router / Relay
   ↓
DHCP Server
```

---

# 🚧 DHCP and Routers

Now we reach an important problem.

Suppose:

```text
CLIENT NETWORK
192.168.10.0/24

PC-01
   │
   ▼
SW-01
   │
   ▼
R-01
   │
   ▼
SERVER NETWORK
192.168.20.0/24

DHCP-01
```

PC-01 sends a DHCP Discover.

Remember:

> **Initial DHCP communication can use broadcasts.**

What do routers normally do with Layer 2 broadcasts?

> **They do not simply forward them into another broadcast domain.**

So the DHCP server may never see the client's Discover.

---

# 🌉 DHCP Relay

Instead of placing a DHCP server in every subnet, we can use:

> **DHCP Relay**

A router or Layer 3 device receives the client's local DHCP broadcast and relays the DHCP request toward a DHCP server on another network.

---

# 🗺️ DHCP Relay Example

```text
PC-01
192.168.10.0/24
   │
   ▼
SW-01
   │
   ▼
R-01
DHCP Relay
   │
   ▼
Routed Network
   │
   ▼
DHCP-01
192.168.20.10
```

---

# 🖥️ Cisco `ip helper-address`

On Cisco routers and Layer 3 switches, a common DHCP relay configuration uses:

```text
ip helper-address
```

Suppose the DHCP server is:

```text
192.168.20.10
```

On the router interface facing the DHCP clients:

```text
interface gigabitethernet 0/0
ip helper-address 192.168.20.10
```

---

# ⭐ Where Does `ip helper-address` Go?

This is important.

The command goes on:

> **The Layer 3 interface receiving the client DHCP broadcasts.**

For example:

```text
CLIENTS
192.168.10.0/24
      │
      ▼
G0/0
R-01
```

Configure:

```text
interface g0/0
ip helper-address 192.168.20.10
```

Not on the server-facing interface just because the DHCP server is there.

---

# 🧠 How Does the Server Know Which Scope to Use?

When a DHCP relay forwards the request, it provides information that allows the DHCP server to determine:

> **Which client subnet the request came from.**

The server can then choose the correct scope.

Conceptually:

```text
Request came from:
192.168.10.0/24
        ↓
Use:
192.168.10.0/24 DHCP Scope
```

---

# 🏢 Centralized DHCP

This allows a company to have:

```text
VLAN 10 — Employees
VLAN 20 — Voice
VLAN 30 — Wireless
VLAN 40 — Guest
```

while using a centralized DHCP server.

Conceptually:

```text
VLAN 10 ─┐
VLAN 20 ─┤
VLAN 30 ─┼─ Layer 3 Device ── DHCP Server
VLAN 40 ─┘      Relays
```

Each VLAN can have:

> **Its own DHCP scope**

---

# 📋 Example Scopes

| VLAN | Network | DHCP Range |
|---:|---|---|
| 10 | 192.168.10.0/24 | 192.168.10.100–200 |
| 20 | 192.168.20.0/24 | 192.168.20.100–200 |
| 30 | 192.168.30.0/24 | 192.168.30.100–200 |
| 40 | 192.168.40.0/24 | 192.168.40.100–200 |

---

# 🪫 Scope Exhaustion

Suppose a scope contains:

```text
192.168.10.100
through
192.168.10.110
```

That's a small pool.

If all available addresses are leased, a new client may fail to receive an address.

This is:

> **DHCP Scope Exhaustion**

---

# 🧠 Troubleshooting Scope Exhaustion

Symptoms may include:

- Existing clients work
- New clients fail
- Some clients receive APIPA
- DHCP server shows no available addresses

Possible solutions include:

- Remove stale leases when appropriate
- Increase the DHCP pool
- Correct overly long lease times where appropriate
- Redesign the subnet if capacity is genuinely insufficient

---

# ⚔️ Rogue DHCP Server

A:

> **Rogue DHCP Server**

is an unauthorized DHCP server providing network configuration.

This can cause clients to receive:

- Wrong gateway
- Wrong DNS server
- Wrong subnet information
- Malicious network settings

Managed switching environments can use features such as:

> **DHCP Snooping**

to help protect against unauthorized DHCP servers.

We'll explore network hardening later in the course.

---

# 🖥️ Windows — Check DHCP Configuration

Run:

```text
ipconfig /all
```

Look for information such as:

```text
DHCP Enabled
IPv4 Address
Subnet Mask
Default Gateway
DHCP Server
DNS Servers
Lease Obtained
Lease Expires
```

---

# 🔄 Release an Address

Windows:

```text
ipconfig /release
```

This releases DHCP configuration for applicable adapters.

---

# 🔄 Request New DHCP Configuration

Use:

```text
ipconfig /renew
```

This asks DHCP to obtain or renew configuration.

---

# ⚠️ Production Warning

Running:

```text
ipconfig /release
```

on your active work connection can temporarily disconnect you.

Only perform DHCP release/renew testing where:

> **You have permission and understand the impact.**

Packet Tracer is a safer place to intentionally break DHCP.

---

# ⚡ PowerShell

Useful PowerShell commands include:

```text
Get-NetIPConfiguration
```

and:

```text
Get-NetIPAddress -AddressFamily IPv4
```

These can help verify the configuration received by the client.

---

# 🛠️ Troubleshooting Scenario 1

Client receives:

```text
169.254.25.14
```

What should you suspect?

> **DHCP communication failed.**

Begin investigating:

```text
Physical Connectivity
        ↓
Switch Port
        ↓
Correct VLAN
        ↓
DHCP Server Available?
        ↓
Scope Available?
        ↓
Relay Required?
```

---

# 🛠️ Scenario 2 — Wrong Gateway

Client successfully receives:

```text
IP:
192.168.10.125

Mask:
255.255.255.0

Gateway:
192.168.10.254
```

Actual gateway:

```text
192.168.10.1
```

The DHCP server is working.

But:

> **The DHCP scope option is incorrectly configured.**

Likely symptom:

```text
Local Network
✅

Remote Networks
❌
```

---

# 🛠️ Scenario 3 — Wrong DNS

Client receives:

```text
IP
✅

Mask
✅

Gateway
✅

DNS
❌
```

Possible symptom:

```text
ping 8.8.8.8
works
```

but:

```text
nslookup example.com
fails
```

This points toward:

> **DNS configuration**

rather than basic IP routing.

---

# 🛠️ Scenario 4 — DHCP Works in One VLAN Only

VLAN 10 receives addresses.

VLAN 20 receives APIPA.

Possible causes include:

- Missing VLAN 20 scope
- Wrong VLAN 20 scope
- Missing DHCP relay on VLAN 20
- Wrong helper address
- Routing problem
- VLAN/trunk problem
- Scope exhaustion

Troubleshoot by:

> **Scope**

Don't assume the entire DHCP server is down if another VLAN is working.

---

# 🛠️ Scenario 5 — Existing Clients Work, New Clients Don't

This is an important clue.

Possible cause:

> **DHCP pool exhaustion**

Existing clients may still have valid leases while new clients cannot obtain addresses.

---

# 🛠️ DHCP Troubleshooting Workflow

Use:

```text
Does Client Have Link?
        ↓
Correct VLAN?
        ↓
DHCP Enabled?
        ↓
What IP Did Client Receive?
        ↓
169.254.x.x?
        ↓
Can DHCP Server Be Reached?
        ↓
Is Relay Required?
        ↓
Is Helper Configured?
        ↓
Does Correct Scope Exist?
        ↓
Are Addresses Available?
        ↓
Are Gateway/DNS Options Correct?
```

---

# 📋 DHCP Quick Reference

| Concept | Meaning |
|---|---|
| DHCP | Dynamic Host Configuration Protocol |
| Client | Requests configuration |
| Server | Supplies configuration |
| Scope | Configuration/address range for a subnet |
| Pool | Addresses available for leasing |
| Lease | Temporary address assignment |
| Exclusion | Address not dynamically assigned |
| Reservation | Specific client receives predictable address |
| DORA | Discover, Offer, Request, Acknowledge |
| UDP 67 | DHCP server |
| UDP 68 | DHCP client |
| APIPA | Automatic 169.254.0.0/16 addressing |
| DHCP Relay | Forwards DHCP communication across routed boundaries |
| `ip helper-address` | Common Cisco DHCP relay configuration |

---

# 🧠 Knowledge Check

### 1.

What does DHCP stand for?

### 2.

What four steps make up DORA?

### 3.

What transport protocol does DHCP use?

### 4.

Which port is associated with the DHCP server?

### 5.

Which port is associated with the DHCP client?

### 6.

What is a DHCP lease?

### 7.

What is a DHCP reservation?

### 8.

What IPv4 range is associated with APIPA?

### 9.

Why might DHCP relay be necessary?

### 10.

What Cisco command is commonly used to configure DHCP relay?

---

# ✅ Answers

1. **Dynamic Host Configuration Protocol**
2. **Discover, Offer, Request, Acknowledge**
3. **UDP**
4. **UDP 67**
5. **UDP 68**
6. **A temporary assignment of network configuration**
7. **A mapping that allows a particular DHCP client to receive a predictable IP address**
8. **169.254.0.0/16**
9. **Routers normally do not forward the client's local DHCP broadcasts between broadcast domains**
10. **`ip helper-address`**

---

# 🎓 Network+ Challenge 1

A Windows workstation shows:

```text
169.254.44.12
```

What should you investigate first?

### A. DNS only
### B. DHCP/network connectivity
### C. HTTPS
### D. NTP

> **Answer: B**

---

# 🎓 Network+ Challenge 2

Which sequence is correct?

### A. Offer → Discover → ACK → Request
### B. Discover → Offer → Request → ACK
### C. Discover → Request → Offer → ACK
### D. Request → Discover → ACK → Offer

> **Answer: B**

---

# 🎓 Network+ Challenge 3

A company wants printers to use DHCP while receiving predictable addresses.

What DHCP feature can accomplish this?

> **Reservation**

---

# 🎓 Network+ Challenge 4

Clients in the same subnet as the DHCP server work.

Clients behind a router do not.

What should you investigate?

> **DHCP relay configuration**

---

# 🎓 Network+ Challenge 5

Existing DHCP clients work, but new clients cannot obtain an address.

What is one likely cause?

> **DHCP scope/pool exhaustion**

---

# 🎓 Network+ Challenge 6

A client receives the correct IP and subnet mask but the wrong default gateway.

Where should you investigate?

> **The DHCP scope's gateway/router option.**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- DHCP automatically provides network configuration.
- DHCP uses UDP ports 67 and 68.
- DORA means Discover, Offer, Request, Acknowledge.
- DHCP scopes correspond to IP networks.
- Pools contain addresses available for leasing.
- Leases allow addresses to be reused.
- Exclusions prevent DHCP from assigning selected addresses.
- Reservations provide predictable DHCP assignments.
- DHCP can provide gateway and DNS information.
- APIPA uses 169.254.0.0/16.
- APIPA is an important DHCP troubleshooting clue.
- Routers separate broadcast domains.
- DHCP relay allows centralized DHCP across routed networks.
- Cisco `ip helper-address` is commonly used for DHCP relay.
- Each client subnet needs appropriate DHCP configuration.
- Existing clients working while new clients fail can indicate scope exhaustion.

---

# 🧪 Next Step — Lab 14

In Lab 14 you'll build:

```text
DHCP Client
     ↓
Switch
     ↓
DHCP Server
```

and then expand it to:

```text
REMOTE DHCP CLIENT
        ↓
      Switch
        ↓
      Router
   DHCP Relay
        ↓
      Switch
        ↓
   DHCP Server
```

You'll observe DORA, create DHCP pools, test automatic addressing, configure relay, and troubleshoot broken DHCP.

➡️ **[Lab 14 — DHCP](../labs/lab-14-dhcp.md)**

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ COMPLETE

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES

✅ Lesson 11 — Switching Fundamentals
✅ Lab 11

✅ Lesson 12 — VLANs & Network Segmentation
✅ Lab 12

✅ Lesson 13 — Routing Fundamentals
✅ Lab 13

✅ Lesson 14 — DHCP
        ↓
🟡 NEXT: Lab 14

⬜ Lesson 15 — DNS
⬜ Lab 15

⬜ Lesson 16 — NAT & Address Translation
⬜ Lab 16

        ↓

🏗️ Project 03
Build a Routed Small-Business Network
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**