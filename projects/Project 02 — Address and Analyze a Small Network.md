# 🏗️ Project 02 — Address and Analyze a Small Network

Welcome to **Project 02 of Networking Fundamentals**.

You've completed the second major phase of the course:

> **Addressing & Communication**

During Lessons 6–10, you learned how devices identify themselves, how IPv4 networks are divided, how IPv6 works, and how applications use TCP, UDP, ports, and protocols.

Now it's time to put those concepts together.

Unlike the regular labs, this project gives you:

> **Requirements instead of every command.**

Your job is to design the addressing, build the network, verify communication, analyze traffic, troubleshoot problems, and document what you discover.

---

# 🎯 Project Objectives

By the end of this project, you should be able to:

- Build a small Ethernet network
- Identify MAC addresses
- Design an IPv4 addressing plan
- Apply subnet masks
- Determine network and broadcast addresses
- Identify usable host ranges
- Configure IPv4 addresses
- Configure basic IPv6 addressing
- Verify local communication
- Observe ARP
- Understand MAC-to-IP relationships
- Identify TCP and UDP traffic
- Recognize common ports
- Capture network traffic with Wireshark
- Use Packet Tracer Simulation Mode
- Troubleshoot addressing problems
- Troubleshoot subnet mask problems
- Document a network
- Explain why communication succeeds or fails

---

# 🎓 Network+ Skills Reinforced

This project reinforces concepts relevant to **CompTIA Network+ N10-009**, including:

- Ethernet
- MAC addresses
- ARP
- IPv4
- IPv6
- CIDR notation
- Subnetting
- Network addresses
- Broadcast addresses
- Host ranges
- TCP
- UDP
- Ports
- Common protocols
- Packet analysis
- Troubleshooting

---

# 🧠 Lessons Used

This project combines:

```text
Lesson 06
Ethernet and MAC Addressing

Lesson 07
IPv4 Addressing

Lesson 08
Subnetting Fundamentals

Lesson 09
IPv6 Fundamentals

Lesson 10
TCP, UDP, Ports, and Protocols
```

If you get stuck:

> Go back to the appropriate lesson before looking for the answer elsewhere.

---

# ⏱️ Estimated Time

**90–120 minutes**

You don't need to complete the entire project in one sitting.

---

# 🧰 Tools

You will use:

- Cisco Packet Tracer
- Windows Command Prompt
- PowerShell
- Wireshark
- Calculator or subnetting notes
- Your course repository for reference

---

# ⚠️ Lab Safety

The Packet Tracer portion is completely simulated.

For the Windows and Wireshark portions:

- Do not change company network configuration without permission
- Do not capture other users' traffic without authorization
- Do not scan networks you don't own or administer
- Do not upload personal packet captures publicly

Use your own computer and authorized network traffic only.

---

# 📋 PROJECT SCENARIO

You have been asked to prepare a small training network for a company.

The network needs to support:

```text
6 Employee Workstations
2 Servers
2 Printers
```

The company has been assigned:

```text
192.168.50.0/24
```

However, management does not want the entire `/24` used as one large network.

The address space should be divided into smaller networks.

You need to create:

```text
EMPLOYEE NETWORK

SERVER / INFRASTRUCTURE NETWORK
```

Each network must support at least:

```text
20 usable IPv4 addresses
```

---

# 🧩 PROJECT REQUIREMENTS

Your finished project must include:

```text
2 Switches

4 PCs

2 Servers
```

You will represent the larger planned network without needing to place every possible workstation and printer into Packet Tracer.

---

# 🗺️ TARGET TOPOLOGY

Build:

```text
EMPLOYEE NETWORK

PC-EMP01 ─┐
          │
PC-EMP02 ─┤
          │
PC-EMP03 ─┼── SW-EMP
          │
PC-EMP04 ─┘


SERVER / INFRASTRUCTURE NETWORK

SERVER-01 ─┐
           ├── SW-SRV
SERVER-02 ─┘
```

At this point in the course:

> **Do not connect the two switches together.**

Why?

Because this project is focused on:

> **Addressing and local communication**

Routing between networks comes later.

---

# 🧠 PROJECT RULE

You are not given the complete addressing plan.

You must calculate it.

Starting network:

```text
192.168.50.0/24
```

Requirements:

```text
Subnet 1
At least 20 usable hosts

Subnet 2
At least 20 usable hosts
```

---

# ✏️ PART 1 — DETERMINE THE PREFIX

Determine the smallest practical subnet that supports at least:

```text
20 usable IPv4 hosts
```

Complete:

```text
Required Hosts:

20


Host Bits Needed:

________________


CIDR Prefix:

/______


Subnet Mask:

____________________________


Total Addresses:

________________


Usable Host Addresses:

________________
```

---

# 💡 Hint

Remember:

```text
2^HostBits - 2
```

for traditional IPv4 usable host calculations.

Try:

```text
2^4 - 2
```

Then:

```text
2^5 - 2
```

Which one supports at least 20 hosts?

---

# 🛑 CHECKPOINT 1

Try calculating it before continuing.

---

# ✅ CHECKPOINT 1 ANSWER

You need:

```text
5 Host Bits
```

because:

```text
2^5
=
32 total addresses
```

Traditional usable hosts:

```text
32 - 2
=
30 usable hosts
```

Therefore:

```text
Prefix:
/27
```

Subnet mask:

```text
255.255.255.224
```

---

# 🧮 PART 2 — FIND THE BLOCK SIZE

Calculate:

```text
256 - 224
```

Result:

```text
32
```

Therefore `/27` networks increment by:

```text
32
```

---

# ✏️ PART 3 — IDENTIFY THE FIRST TWO SUBNETS

Complete:

## Subnet 1

```text
Network Address:

____________________________


First Usable:

____________________________


Last Usable:

____________________________


Broadcast:

____________________________
```

## Subnet 2

```text
Network Address:

____________________________


First Usable:

____________________________


Last Usable:

____________________________


Broadcast:

____________________________
```

---

# 🛑 CHECKPOINT 2

Calculate both networks before continuing.

---

# ✅ CHECKPOINT 2 ANSWER

## Subnet 1

```text
Network:
192.168.50.0/27

First Usable:
192.168.50.1

Last Usable:
192.168.50.30

Broadcast:
192.168.50.31
```

## Subnet 2

```text
Network:
192.168.50.32/27

First Usable:
192.168.50.33

Last Usable:
192.168.50.62

Broadcast:
192.168.50.63
```

---

# 🏢 PART 4 — ASSIGN THE NETWORKS

Use:

```text
EMPLOYEE NETWORK

192.168.50.0/27
```

and:

```text
SERVER / INFRASTRUCTURE NETWORK

192.168.50.32/27
```

---

# 📋 PART 5 — CREATE AN ADDRESSING PLAN

You decide which valid host addresses to assign.

Complete the table before configuring Packet Tracer.

| Device | Network | IPv4 Address | Prefix | Subnet Mask |
|---|---|---|---:|---|
| PC-EMP01 | Employee | | /27 | |
| PC-EMP02 | Employee | | /27 | |
| PC-EMP03 | Employee | | /27 | |
| PC-EMP04 | Employee | | /27 | |
| SERVER-01 | Server | | /27 | |
| SERVER-02 | Server | | /27 | |

---

# ⭐ Rules

You may not use:

- Network addresses
- Broadcast addresses
- Duplicate addresses
- Addresses outside the assigned subnet

For this project:

> **Do not configure a default gateway yet.**

There is no router.

---

# 🏗️ PART 6 — BUILD THE NETWORK

Open:

> **Cisco Packet Tracer**

Add:

```text
4 PCs

2 Servers

2 Switches
```

Rename them:

```text
PC-EMP01
PC-EMP02
PC-EMP03
PC-EMP04

SERVER-01
SERVER-02

SW-EMP
SW-SRV
```

Connect the employee devices to:

```text
SW-EMP
```

Connect the servers to:

```text
SW-SRV
```

---

# 🔌 PART 7 — VERIFY PHYSICAL CONNECTIVITY

Before configuring IP addresses, verify:

```text
Links are green
```

If not, investigate:

- Cable type
- Correct interface
- Device state
- Switch port

Do not immediately blame IP addressing for a Layer 1 problem.

---

# 🌐 PART 8 — CONFIGURE IPv4

Configure each device according to your addressing table.

Example path:

```text
Device
   ↓
Desktop
   ↓
IP Configuration
```

Enter:

```text
IPv4 Address

Subnet Mask
```

Leave the default gateway blank.

---

# 🧪 PART 9 — VERIFY EMPLOYEE COMMUNICATION

From:

```text
PC-EMP01
```

ping:

```text
PC-EMP02
PC-EMP03
PC-EMP04
```

Record:

| Test | Result |
|---|---|
| EMP01 → EMP02 | |
| EMP01 → EMP03 | |
| EMP01 → EMP04 | |

Expected:

> **Success**

assuming your addressing is correct.

---

# 🧪 PART 10 — VERIFY SERVER COMMUNICATION

From:

```text
SERVER-01
```

ping:

```text
SERVER-02
```

Record:

```text
SERVER-01 → SERVER-02

PASS / FAIL
```

Expected:

> **Success**

---

# 🚧 PART 11 — CROSS-NETWORK QUESTION

Can:

```text
PC-EMP01
```

communicate with:

```text
SERVER-01
```

right now?

> **No**

The networks aren't physically connected, and there is no Layer 3 device routing between them.

This reinforces an important concept:

```text
Same IP Network
→ Local Communication

Different IP Networks
→ Layer 3 Routing Required
```

You'll solve that in later lessons.

---

# 🔍 PART 12 — FIND MAC ADDRESSES

On a Packet Tracer PC:

```text
Command Prompt
```

Run:

```text
ipconfig /all
```

Find the physical/MAC address.

Record:

| Device | IPv4 | MAC Address |
|---|---|---|
| PC-EMP01 | | |
| PC-EMP02 | | |
| PC-EMP03 | | |
| PC-EMP04 | | |

---

# 🧠 IPv4 vs. MAC

Remember:

```text
IPv4 Address
=
Layer 3 logical address
```

while:

```text
MAC Address
=
Layer 2 interface address
```

Both are involved in local Ethernet communication.

---

# 🔎 PART 13 — EXAMINE THE ARP TABLE

From PC-EMP01:

```text
arp -a
```

Record one entry:

```text
IPv4 Address:

____________________________


MAC Address:

____________________________
```

---

# 🧠 What Does ARP Do?

ARP helps an IPv4 device determine:

> **Which MAC address corresponds to a local IPv4 address?**

Conceptually:

```text
192.168.50.x
       ↓
ARP
       ↓
MAC Address
```

---

# 🔬 PART 14 — OBSERVE ARP IN PACKET TRACER

Switch Packet Tracer to:

> **Simulation Mode**

Clear previous events if necessary.

Generate traffic:

```text
PC-EMP01
   ↓
ping
   ↓
PC-EMP02
```

Watch for:

```text
ARP
```

before the ICMP communication.

---

# 📢 ARP REQUEST

Observe the ARP Request.

Conceptually:

```text
PC-EMP01

"Who has 192.168.50.x?"
```

The request is:

> **Broadcast**

because PC-EMP01 doesn't yet know the destination MAC address.

---

# 📩 ARP REPLY

PC-EMP02 responds with its MAC address.

Conceptually:

```text
PC-EMP02

"192.168.50.x is at
AA:BB:CC:DD:EE:FF"
```

The sender can then construct the Ethernet frame.

---

# 🧠 Communication Process

You should now be able to explain:

```text
Application wants to communicate
        ↓
Destination IPv4 known
        ↓
Destination is local
        ↓
ARP determines MAC address
        ↓
Ethernet frame created
        ↓
Switch forwards frame
        ↓
Destination receives traffic
```

---

# 🔀 PART 15 — INSPECT THE SWITCH MAC TABLE

Open:

```text
SW-EMP
```

CLI:

```text
enable
```

Then:

```text
show mac address-table
```

Record:

```text
How many dynamic MAC entries exist?

____________________________
```

---

# 🧠 What Did the Switch Learn?

The switch learns:

```text
Source MAC Address
        +
Incoming Switch Port
```

Conceptually:

```text
MAC Address             Port
AA:AA:AA:AA:AA:01       Fa0/1
AA:AA:AA:AA:AA:02       Fa0/2
```

This allows the switch to intelligently forward Ethernet frames.

---

# 🌐 PART 16 — ADD IPv6

Now add basic IPv6 addressing to the employee network.

Use documentation prefix:

```text
2001:db8:50:1::/64
```

Assign:

```text
PC-EMP01
2001:db8:50:1::10/64

PC-EMP02
2001:db8:50:1::20/64

PC-EMP03
2001:db8:50:1::30/64

PC-EMP04
2001:db8:50:1::40/64
```

---

# 🧪 PART 17 — TEST IPv6

From PC-EMP01:

```text
ping 2001:db8:50:1::20
```

Then test:

```text
2001:db8:50:1::30
```

and:

```text
2001:db8:50:1::40
```

Record:

```text
IPv6 Local Communication:

PASS / FAIL
```

---

# 🧠 IPv6 Reminder

IPv6 does not use ARP.

Instead, IPv6 uses:

> **Neighbor Discovery**

through ICMPv6.

This is an important IPv4 vs. IPv6 distinction.

---

# 🔬 PART 18 — OBSERVE IPv6 COMMUNICATION

Use Packet Tracer Simulation Mode.

Generate an IPv6 ping.

Look for:

```text
ICMPv6
```

and Neighbor Discovery-related traffic.

Compare this with the ARP behavior you observed for IPv4.

---

# 📋 PART 19 — IPv4 vs. IPv6

Complete:

| Feature | IPv4 | IPv6 |
|---|---|---|
| Address Size | | |
| Example | | |
| Local Neighbor Resolution | | |
| Broadcast | | |

Answers:

| Feature | IPv4 | IPv6 |
|---|---|---|
| Address Size | 32-bit | 128-bit |
| Example | 192.168.50.10 | 2001:db8:50:1::10 |
| Local Neighbor Resolution | ARP | Neighbor Discovery |
| Broadcast | Supported | No traditional broadcast |

---

# 💻 PART 20 — MOVE TO YOUR WINDOWS COMPUTER

Now use your real Windows computer for traffic analysis.

Open:

> **Command Prompt**

Run:

```text
ipconfig /all
```

Record your active adapter's:

```text
IPv4 Address:

____________________________


Subnet Mask:

____________________________


Default Gateway:

____________________________


MAC Address:

____________________________
```

---

# ⚡ PART 21 — POWERSHELL INSPECTION

Open PowerShell.

Run:

```text
Get-NetIPConfiguration
```

Then:

```text
Get-NetIPAddress
```

Then:

```text
Get-NetAdapter
```

Compare this information with:

```text
ipconfig /all
```

---

# 🧠 Question

Which tool do you find easier for quickly viewing network information?

```text
Command Prompt

or

PowerShell
```

Record:

```text
________________________________
```

There is no wrong answer.

A good technician should be comfortable with both.

---

# 🦈 PART 22 — WIRESHARK

Open:

> **Wireshark**

Select your active network adapter.

Start a capture.

Only capture traffic you're authorized to inspect.

---

# 🔎 PART 23 — OBSERVE DNS

Use display filter:

```text
dns
```

Generate a DNS query:

```text
nslookup example.com
```

Find:

```text
DNS Query
```

and:

```text
DNS Response
```

Record:

```text
DNS Server:

____________________________


Queried Name:

____________________________


Returned Address:

____________________________
```

---

# 🧠 Protocol Question

What transport port is associated with traditional DNS?

```text
____________________________
```

Answer:

```text
53
```

---

# 🔎 PART 24 — OBSERVE TCP

Use a display filter such as:

```text
tcp
```

Generate normal authorized web traffic.

Select a TCP packet.

Record:

```text
Source IP:

____________________________


Destination IP:

____________________________


Source Port:

____________________________


Destination Port:

____________________________
```

---

# 🧠 Client Port vs. Server Port

You may see something conceptually like:

```text
Client:
192.168.1.50:52144

Server:
203.0.113.10:443
```

The high-numbered client port is typically:

> **An ephemeral port**

while:

```text
443
```

is associated with:

> **HTTPS**

---

# 🔎 PART 25 — OBSERVE UDP

Use:

```text
udp
```

as a filter.

Look for authorized UDP traffic generated by your system.

Depending on your environment, you may see protocols such as:

```text
DNS
DHCP
QUIC
mDNS
```

Do not worry if your exact traffic differs.

---

# 📋 PART 26 — PROTOCOL ANALYSIS

Complete:

| Traffic | TCP/UDP | Common Port |
|---|---|---:|
| HTTP | | |
| HTTPS | | |
| DNS | | |
| DHCP Server | | |
| DHCP Client | | |
| SSH | | |

Answers:

| Traffic | TCP/UDP | Common Port |
|---|---|---:|
| HTTP | TCP | 80 |
| HTTPS | TCP | 443 |
| DNS | UDP/TCP | 53 |
| DHCP Server | UDP | 67 |
| DHCP Client | UDP | 68 |
| SSH | TCP | 22 |

---

# ⭐ PROJECT CHECKPOINT

At this point, you have worked with:

```text
Ethernet
        ↓
MAC Addresses
        ↓
ARP
        ↓
IPv4
        ↓
Subnetting
        ↓
IPv6
        ↓
TCP / UDP
        ↓
Ports
        ↓
Real Packet Capture
```

Now we're going to break things.

---

# 💥 PART 27 — TROUBLESHOOTING CHALLENGE 1

On:

```text
PC-EMP04
```

change its subnet mask from:

```text
255.255.255.224
```

to:

```text
255.255.255.0
```

Do not change the other devices.

---

# 🧪 Investigate

Test communication.

Then answer:

```text
What changed?

________________________________


Does the IP still look valid?

YES / NO


Does the subnet mask match the network design?

YES / NO


Root Cause:

________________________________
```

---

# ⭐ Lesson

An IP address can look perfectly reasonable while:

> **The subnet mask is wrong.**

Always inspect both.

---

# 🔧 Repair

Restore:

```text
255.255.255.224
```

Verify communication.

---

# 💥 PART 28 — TROUBLESHOOTING CHALLENGE 2

Give:

```text
PC-EMP03
```

the same IPv4 address as:

```text
PC-EMP02
```

You have created:

> **A duplicate IP address**

Test communication.

---

# 🧠 Investigate

Ask:

```text
Are two devices using the same address?

Does ARP behave strangely?

Is communication reliable?

Does Packet Tracer report a conflict?
```

---

# 🔧 Repair

Give each device a unique address.

Verify:

```text
PC-EMP01
→
PC-EMP02

PC-EMP01
→
PC-EMP03
```

both work again.

---

# 💥 PART 29 — TROUBLESHOOTING CHALLENGE 3

Configure PC-EMP04 with:

```text
192.168.50.35
255.255.255.224
```

Remember:

```text
PC-EMP04
```

is supposed to belong to:

```text
192.168.50.0/27
```

---

# 🧠 Question

Which subnet contains:

```text
192.168.50.35/27
```

?

Answer:

```text
192.168.50.32/27
```

PC-EMP04 now has an address belonging to:

> **The wrong IP network**

even though it is physically connected to the Employee switch.

---

# ⭐ Important Concept

Physical connection does not determine:

> **Which IP subnet an address belongs to.**

The combination of:

```text
IP Address
+
Subnet Mask
```

does.

---

# 🔧 Repair

Return PC-EMP04 to a valid address in:

```text
192.168.50.0/27
```

---

# 💥 PART 30 — TROUBLESHOOTING CHALLENGE 4

Disconnect:

```text
PC-EMP02
```

from the switch.

Test:

```text
PC-EMP01
→
PC-EMP02
```

Expected:

> **Failure**

---

# 🧠 Troubleshooting Lesson

This failure has nothing to do with:

```text
TCP
UDP
Subnetting
DNS
```

The problem is:

> **Physical connectivity**

Always start with the simplest possibilities.

---

# 🔧 Repair

Reconnect PC-EMP02.

Wait for the link.

Retest.

---

# 🔍 PART 31 — TROUBLESHOOTING METHODOLOGY

For an endpoint that cannot communicate locally, use:

```text
Physical Link
      ↓
Interface Up?
      ↓
Correct IPv4 Address?
      ↓
Correct Subnet Mask?
      ↓
Duplicate Address?
      ↓
Same Subnet?
      ↓
ARP Working?
      ↓
Switch Learning MAC?
      ↓
Test Again
```

Later in the course we'll add:

```text
Default Gateway
Routing
VLANs
DHCP
DNS
NAT
Firewall
```

to this troubleshooting process.

---

# 📋 PART 32 — DOCUMENT THE FINAL NETWORK

Create a final table:

| Device | IPv4 | Prefix | MAC | IPv6 |
|---|---|---:|---|---|
| PC-EMP01 | | /27 | | |
| PC-EMP02 | | /27 | | |
| PC-EMP03 | | /27 | | |
| PC-EMP04 | | /27 | | |
| SERVER-01 | | /27 | | |
| SERVER-02 | | /27 | | |

---

# 🗺️ PART 33 — DOCUMENT THE SUBNETS

## Employee Network

```text
Network:

____________________________


Prefix:

____________________________


Subnet Mask:

____________________________


First Usable:

____________________________


Last Usable:

____________________________


Broadcast:

____________________________
```

## Server / Infrastructure Network

```text
Network:

____________________________


Prefix:

____________________________


Subnet Mask:

____________________________


First Usable:

____________________________


Last Usable:

____________________________


Broadcast:

____________________________
```

---

# 📝 PART 34 — PROJECT TROUBLESHOOTING REPORT

Choose one failure you created.

Document it like an IT technician.

```text
Problem:

________________________________


Initial Symptoms:

________________________________


Tools Used:

________________________________


Commands Used:

________________________________


What I Found:

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

# 🧠 PART 35 — EXPLAIN THE NETWORK

Without looking at the previous lessons, try to explain:

### Why does a PC need a MAC address?

```text
________________________________

________________________________
```

### Why does it need an IP address?

```text
________________________________

________________________________
```

### What does the subnet mask tell the device?

```text
________________________________

________________________________
```

### What does ARP do?

```text
________________________________

________________________________
```

### Why can't these two networks communicate yet?

```text
________________________________

________________________________
```

### What is the difference between TCP and UDP?

```text
________________________________

________________________________
```

### What does a port number identify?

```text
________________________________

________________________________
```

If you can explain these in your own words:

> **You're learning networking rather than simply memorizing commands.**

---

# 🎓 NETWORK+ CHALLENGE 1

A network must support:

```text
25 hosts
```

Which prefix is appropriate?

### A. /28
### B. /27
### C. /30
### D. /29

> **Answer: B — /27**

A `/27` provides:

```text
30 traditional usable host addresses
```

---

# 🎓 NETWORK+ CHALLENGE 2

Given:

```text
192.168.50.45/27
```

what is the network address?

### A. 192.168.50.0
### B. 192.168.50.16
### C. 192.168.50.32
### D. 192.168.50.64

> **Answer: C — 192.168.50.32**

---

# 🎓 NETWORK+ CHALLENGE 3

Which protocol maps a local IPv4 address to a MAC address?

### A. DNS
### B. DHCP
### C. ARP
### D. HTTP

> **Answer: C — ARP**

---

# 🎓 NETWORK+ CHALLENGE 4

Which transport protocol provides connection-oriented communication?

### A. ARP
### B. TCP
### C. UDP
### D. ICMP

> **Answer: B — TCP**

---

# 🎓 NETWORK+ CHALLENGE 5

Which port is associated with HTTPS?

### A. 22
### B. 53
### C. 80
### D. 443

> **Answer: D — 443**

---

# 🎓 NETWORK+ CHALLENGE 6

A device has:

```text
192.168.50.20
255.255.255.224
```

Which network does it belong to?

> **192.168.50.0/27**

---

# 🎓 NETWORK+ CHALLENGE 7

A device has:

```text
192.168.50.35
255.255.255.224
```

Which network does it belong to?

> **192.168.50.32/27**

---

# 🎓 NETWORK+ CHALLENGE 8

What technology does IPv6 use instead of ARP?

> **Neighbor Discovery**

---

# 🎓 NETWORK+ CHALLENGE 9

Two PCs have different IPv4 addresses but the same MAC address is not normally expected.

Which address does an Ethernet switch primarily use when forwarding Ethernet frames?

> **MAC address**

---

# 🎓 NETWORK+ CHALLENGE 10

A computer can communicate with other devices on its local network but cannot communicate with a different IP network.

What component will eventually be needed?

> **A router or another Layer 3 routing device**

---

# 🏆 PROJECT COMPLETION CHECKLIST

Before marking Project 02 complete, verify:

- [ ] I calculated the `/27` networks
- [ ] I identified network addresses
- [ ] I identified broadcast addresses
- [ ] I identified usable host ranges
- [ ] I created an addressing plan
- [ ] I built the Packet Tracer topology
- [ ] I configured IPv4
- [ ] I verified local communication
- [ ] I identified MAC addresses
- [ ] I examined ARP
- [ ] I examined a switch MAC address table
- [ ] I configured IPv6
- [ ] I tested IPv6 communication
- [ ] I reviewed Neighbor Discovery
- [ ] I inspected my Windows network configuration
- [ ] I used PowerShell networking commands
- [ ] I captured authorized traffic with Wireshark
- [ ] I identified DNS traffic
- [ ] I examined TCP
- [ ] I examined UDP
- [ ] I identified common ports
- [ ] I troubleshot a bad subnet mask
- [ ] I troubleshot a duplicate IPv4 address
- [ ] I troubleshot a wrong-subnet address
- [ ] I troubleshot physical connectivity
- [ ] I documented the network
- [ ] I completed a troubleshooting report
- [ ] I can explain why the network works

---

# 💾 Save Your Work

Save your Packet Tracer project locally as:

```text
project-02-address-and-analyze-small-network.pkt
```

You do not need to upload the completed `.pkt` file to the public repository.

If you save a Wireshark capture, keep it local as well.

---

# 🏆 Project 02 Complete

You have now completed:

> **Phase 2 — Addressing & Communication**

You started this phase learning how Ethernet identifies devices.

You can now follow communication through:

```text
Application
     ↓
TCP / UDP
     ↓
Ports
     ↓
IPv4 / IPv6
     ↓
Subnet
     ↓
ARP / Neighbor Discovery
     ↓
MAC Address
     ↓
Ethernet Frame
     ↓
Switch
```

You also know that when two devices belong to different IP networks:

```text
Network A
     ↓
?????
     ↓
Network B
```

something else is required.

That's exactly where the next phase begins.

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ Lessons 01–05
✅ Labs 01–05
✅ Project 01 — Build Your First Network

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ Lesson 06 — Ethernet & MAC Addressing
✅ Lab 06
✅ Lesson 07 — IPv4 Addressing
✅ Lab 07
✅ Lesson 08 — Subnetting Fundamentals
✅ Lab 08
✅ Lesson 09 — IPv6 Fundamentals
✅ Lab 09
✅ Lesson 10 — TCP, UDP, Ports & Protocols
✅ Lab 10
✅ Project 02 — Address and Analyze a Small Network

        ↓

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES

🟡 NEXT:
Lesson 11 — Switching Fundamentals
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 11 — Switching Fundamentals**

You've already seen that a switch can learn MAC addresses.

Next you'll go deeper into:

- Switch operation
- MAC address tables
- Frame forwarding
- Flooding
- Broadcasts
- Unknown unicasts
- Collision domains
- Broadcast domains
- Switch ports
- Cisco switch CLI
- Switch troubleshooting

This begins:

> **Phase 3 — Switching, Routing & Services**

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](README.md)**

➡️ **[Return to Main README](../README.md)**