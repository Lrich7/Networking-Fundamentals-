# 🧪 Lab 06 — Ethernet and MAC Addressing

Welcome to **Lab 06 of Networking Fundamentals**.

In Lesson 06, you learned about:

- Ethernet
- MAC addresses
- Ethernet frames
- Switch MAC address tables
- Unicast
- Broadcast
- Multicast
- ARP
- Broadcast domains

Now you're going to see those concepts in three different environments:

```text
Windows
+
Wireshark
+
Cisco Packet Tracer
```

The goal is to connect theory with real behavior.

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Find your computer's MAC address
- Identify multiple network adapters
- View the Windows ARP cache
- Use `Get-NetNeighbor`
- Generate ARP traffic
- Capture ARP using Wireshark
- Identify Ethernet source and destination MAC addresses
- Recognize the Ethernet broadcast address
- Build a switched LAN in Packet Tracer
- View a switch MAC address table
- Explain how switches learn MAC addresses
- Observe unknown unicast flooding
- Compare local and routed communication
- Explain why remote traffic uses the default gateway's MAC address
- Troubleshoot basic Layer 2 problems

---

# 🎓 Network+ Focus

This lab reinforces important Network+ concepts including:

- Ethernet
- MAC addressing
- ARP
- Ethernet frames
- Switches
- MAC address tables
- Broadcasts
- Unicast
- Layer 2 troubleshooting
- Broadcast domains
- Local vs. remote traffic

---

# 🧰 What You'll Need

You should have:

- Windows computer
- Command Prompt
- PowerShell
- Wireshark
- Cisco Packet Tracer
- Internet or local network connection

---

# ⏱️ Estimated Time

Approximately:

**60–75 minutes**

---

# ⚠️ Safety Reminder

For the Wireshark portion:

Only inspect traffic from:

- Your own computer
- Networks you manage
- Networks where you have permission

Do not intentionally capture other users' private traffic.

---

# PART 1 — WINDOWS

# 🖥️ Step 1 — Find Your Network Adapters

Open:

> **PowerShell**

Run:

```powershell
Get-NetAdapter
```

Look for:

```text
Name
InterfaceDescription
Status
MacAddress
LinkSpeed
```

You may see adapters such as:

```text
Ethernet
Wi-Fi
Bluetooth
VPN
Virtual Ethernet
```

---

# 📝 Record Your Active Adapter

### Adapter Name

```text
____________________________________
```

### Status

```text
____________________________________
```

### MAC Address

```text
____________________________________
```

### Link Speed

```text
____________________________________
```

---

# 🧠 Question

Why might one computer have multiple MAC addresses?

```text
____________________________________________________

____________________________________________________
```

---

# 🔍 Step 2 — Use ipconfig

Open:

> **Command Prompt**

Run:

```cmd
ipconfig /all
```

Find your active adapter.

Look for:

```text
Physical Address
IPv4 Address
Subnet Mask
Default Gateway
DNS Servers
```

Record:

### IPv4 Address

```text
____________________________________
```

### Physical Address

```text
____________________________________
```

### Default Gateway

```text
____________________________________
```

---

# 🧠 Checkpoint

Which item represents Layer 2 addressing?

### A. IPv4 Address

### B. MAC Address

### C. Default Gateway IP

### D. DNS Server

Answer:

```text
____________________________________
```

Correct answer:

> **B — MAC Address**

---

# 📋 Step 3 — View the ARP Cache

Run:

```cmd
arp -a
```

You may see something like:

```text
Internet Address      Physical Address      Type
192.168.1.1           11-22-33-44-55-66     dynamic
192.168.1.20          aa-bb-cc-dd-ee-ff     dynamic
```

This table associates:

```text
IPv4 Address
      ↓
MAC Address
```

---

# 📝 Record One ARP Entry

### IPv4 Address

```text
____________________________________
```

### MAC Address

```text
____________________________________
```

### Type

```text
____________________________________
```

---

# 🧠 What Does ARP Do?

Complete:

```text
ARP resolves:

____________________________________

to:

____________________________________
```

Correct concept:

> IPv4 address → MAC address

---

# 🔷 Step 4 — View Neighbor Information

Open PowerShell.

Run:

```powershell
Get-NetNeighbor
```

This provides neighbor information for your interfaces.

You may see columns such as:

```text
ifIndex
IPAddress
LinkLayerAddress
State
```

---

# 🧠 Compare the Tools

`arp -a` focuses primarily on IPv4 ARP mappings.

`Get-NetNeighbor` can display neighbor information associated with:

- IPv4
- IPv6

Record one entry from `Get-NetNeighbor`.

```text
IP Address:

____________________________________

Link-Layer Address:

____________________________________

State:

____________________________________
```

---

# 🌐 Step 5 — Identify Your Gateway MAC

Find your default gateway using:

```cmd
ipconfig
```

Example:

```text
192.168.1.1
```

Then run:

```cmd
arp -a
```

Look for the gateway address.

Record:

### Gateway IP

```text
____________________________________
```

### Gateway MAC

```text
____________________________________
```

---

# 🧠 Important Question

If you visit a remote Internet server, does your PC normally send the first Ethernet frame directly to the remote server's MAC address?

> **No**

It normally sends the local Ethernet frame toward:

> **The default gateway's MAC address**

---

# PART 2 — WIRESHARK

# 🦈 Step 6 — Start Wireshark

Open:

> **Wireshark**

Select your active interface.

Usually:

```text
Ethernet
```

or:

```text
Wi-Fi
```

Start a capture.

---

# 📡 Step 7 — Filter ARP

In the display filter bar, enter:

```text
arp
```

You may already see ARP traffic.

If not, we'll generate some.

---

# 🔄 Step 8 — Generate Local Traffic

Open Command Prompt.

Ping your default gateway:

```cmd
ping YOUR_GATEWAY_IP
```

Example:

```cmd
ping 192.168.1.1
```

Return to Wireshark.

Look for ARP packets.

---

# 🧠 You May Not See ARP Yet

Your computer may already know the gateway's MAC address.

If the ARP entry already exists, Windows may not need to perform a new ARP request.

That's normal.

---

# 🧹 Step 9 — Optional ARP Cache Refresh

Only on your own lab computer and where permitted, you may clear the ARP cache from an elevated Command Prompt using:

```cmd
arp -d *
```

Then immediately ping the gateway again.

If you prefer not to clear the cache, simply continue and observe existing ARP traffic when it appears.

---

# 🔍 Step 10 — Find an ARP Request

Look for something similar to:

```text
Who has 192.168.1.1?
```

Select the packet.

Expand:

> **Ethernet II**

Look at:

```text
Source
Destination
```

The destination may be:

```text
ff:ff:ff:ff:ff:ff
```

---

# 📢 Ethernet Broadcast Address

Remember:

```text
FF:FF:FF:FF:FF:FF
```

means:

> **Broadcast**

Everyone in the local broadcast domain can receive that Layer 2 frame.

---

# 📝 ARP Request Observation

### Source MAC

```text
____________________________________
```

### Destination MAC

```text
____________________________________
```

### Sender IP

```text
____________________________________
```

### Target IP

```text
____________________________________
```

---

# 📬 Step 11 — Find the ARP Reply

Look for a reply similar to:

```text
192.168.1.1 is at 11:22:33:44:55:66
```

Select the reply.

Record:

### Source MAC

```text
____________________________________
```

### Destination MAC

```text
____________________________________
```

### Source IP

```text
____________________________________
```

---

# 🧠 ARP Request vs. Reply

The request is typically:

> **Broadcast**

The reply is commonly:

> **Unicast**

Conceptually:

```text
ARP REQUEST

PC
 │
 └──────> EVERYONE
```

```text
ARP REPLY

Gateway
 │
 └──────> PC
```

---

# 🔎 Step 12 — Inspect an Ethernet Frame

Clear the ARP filter.

Select any ordinary IPv4 packet that contains:

> **Ethernet II**

Expand:

```text
Ethernet II
```

Record:

### Source MAC

```text
____________________________________
```

### Destination MAC

```text
____________________________________
```

Then expand:

```text
Internet Protocol Version 4
```

Record:

### Source IP

```text
____________________________________
```

### Destination IP

```text
____________________________________
```

---

# 🧠 Layer 2 vs. Layer 3

Complete:

```text
MAC addresses are mainly associated with:

OSI Layer ______
```

```text
IP addresses are mainly associated with:

OSI Layer ______
```

Answers:

```text
MAC → Layer 2

IP → Layer 3
```

---

# 🌎 Step 13 — Examine Remote Traffic

Start a fresh capture if needed.

Run:

```cmd
ping 8.8.8.8
```

Filter:

```text
icmp
```

Select an Echo Request.

Expand:

```text
Ethernet II
```

Then:

```text
Internet Protocol Version 4
```

Record:

### Destination IP

```text
____________________________________
```

### Destination MAC

```text
____________________________________
```

---

# 🧠 What Should You Notice?

The destination IP may be:

```text
8.8.8.8
```

But the destination MAC should normally belong to:

> **Your local gateway or next Layer 2 hop**

This reinforces:

```text
REMOTE IP DESTINATION
≠
LOCAL MAC DESTINATION
```

---

# 📝 Explain It

Why does your computer use the gateway's MAC instead of the remote server's MAC?

```text
____________________________________________________

____________________________________________________

____________________________________________________
```

---

# PART 3 — PACKET TRACER

# 🌐 Step 14 — Build a Small Switched LAN

Open Cisco Packet Tracer.

Create:

```text
PC-01
PC-02
PC-03
SW-01
```

Build:

```text
PC-01 ──┐
        │
PC-02 ─ SW-01
        │
PC-03 ──┘
```

---

# 📍 Step 15 — Configure IPv4

Use:

```text
192.168.10.0/24
```

Configure:

| Device | IP Address | Subnet Mask |
|---|---|---|
| PC-01 | 192.168.10.10 | 255.255.255.0 |
| PC-02 | 192.168.10.20 | 255.255.255.0 |
| PC-03 | 192.168.10.30 | 255.255.255.0 |

A gateway is not required for these PCs to communicate with one another on the same subnet.

---

# 🧪 Step 16 — Test Local Connectivity

From PC-01:

```cmd
ping 192.168.10.20
```

Then:

```cmd
ping 192.168.10.30
```

Record:

```text
PC-01 → PC-02

PASS / FAIL
```

```text
PC-01 → PC-03

PASS / FAIL
```

---

# 🧠 Why Is No Router Required?

Answer:

```text
____________________________________________________

____________________________________________________
```

Correct concept:

> All devices are on the same local IP network.

---

# 🔀 Step 17 — Inspect the Switch MAC Table

Click:

> **SW-01**

Open:

> **CLI**

Press Enter if needed.

Run:

```text
enable
```

Then:

```text
show mac address-table
```

Depending on the Packet Tracer switch model, you may see entries similar to:

```text
Vlan    Mac Address       Type       Ports
----    -----------       --------   -----
1       xxxx.xxxx.xxxx    DYNAMIC    Fa0/1
1       xxxx.xxxx.xxxx    DYNAMIC    Fa0/2
1       xxxx.xxxx.xxxx    DYNAMIC    Fa0/3
```

---

# 📝 Record the Table

| MAC Address | Port |
|---|---|
| | |
| | |
| | |

---

# 🧠 How Did the Switch Learn These?

The switch learned them primarily by examining:

> **Source MAC addresses**

on incoming frames.

---

# 🔬 Step 18 — Watch the Switch Learn

If the MAC table already contains entries, you can clear the dynamic entries for the lab.

On many Cisco switches:

```text
clear mac address-table dynamic
```

Then check again:

```text
show mac address-table
```

Now generate traffic:

```text
PC-01 → PC-02
```

Run:

```cmd
ping 192.168.10.20
```

Return to SW-01.

Run:

```text
show mac address-table
```

Observe what has been learned.

---

# 🧠 What Happened?

The switch saw traffic arriving from PC-01 and learned:

```text
PC-01 MAC
      ↓
Incoming Switch Port
```

When PC-02 replied, it could also learn:

```text
PC-02 MAC
      ↓
Its Switch Port
```

---

# 📦 Step 19 — Use Simulation Mode

Switch Packet Tracer to:

> **Simulation Mode**

Clear existing events if helpful.

Generate a Simple PDU from:

```text
PC-01
```

to:

```text
PC-02
```

Use:

> **Capture / Forward**

to advance the communication.

---

# 🔍 Step 20 — Inspect the First Communication

Watch what happens when the switch initially does not know where the destination lives.

Depending on the current MAC/ARP state, you may see:

- ARP
- ICMP
- Broadcast traffic
- Unicast traffic

Pay particular attention to the first ARP request.

---

# 📢 Step 21 — Observe the ARP Broadcast

Look for a frame sent toward:

```text
FFFF.FFFF.FFFF
```

or equivalent formatting.

That represents:

> **FF:FF:FF:FF:FF:FF**

The Ethernet broadcast MAC.

---

# 🧠 Why Did the Switch Send It to Multiple Ports?

Because the frame was:

> **Broadcast traffic**

The switch forwards broadcasts throughout the appropriate local broadcast domain.

---

# 📝 Broadcast Observation

Which devices received the broadcast?

```text
____________________________________

____________________________________
```

Which device actually answered the ARP request?

```text
____________________________________
```

---

# 👤 Step 22 — Observe Unicast Traffic

After the devices learn each other's Layer 2 information, repeat the communication.

You should see more direct:

> **Unicast**

traffic.

Conceptually:

```text
PC-01
  │
  ▼
SW-01
  │
  ▼
PC-02
```

rather than sending known unicast frames to every port.

---

# 🧠 Explain the Difference

Why is known unicast forwarding more efficient than flooding?

```text
____________________________________________________

____________________________________________________
```

---

# 🚦 PART 4 — ADD A ROUTER

# 🌐 Step 23 — Expand the Network

Add:

```text
R-01
SW-02
SRV-01
```

Create:

```text
PC-01 ─┐
PC-02 ─┼─ SW-01 ─ R-01 ─ SW-02 ─ SRV-01
PC-03 ─┘
```

---

# 📍 Step 24 — Configure the New Network

Employee LAN:

```text
192.168.10.0/24
```

Server LAN:

```text
192.168.20.0/24
```

Configure R-01:

```text
Employee side:
192.168.10.1/24
```

```text
Server side:
192.168.20.1/24
```

Configure SRV-01:

```text
IP:
192.168.20.10

Mask:
255.255.255.0

Gateway:
192.168.20.1
```

Update employee PCs to use:

```text
192.168.10.1
```

as the default gateway.

---

# 🧪 Step 25 — Test Routed Connectivity

From PC-01:

```cmd
ping 192.168.20.10
```

Record:

```text
PASS / FAIL
```

---

# 🔬 Step 26 — Inspect Routed Traffic

Use Simulation Mode.

Generate traffic:

```text
PC-01
   ↓
SRV-01
```

Inspect the packet as it crosses:

```text
PC-01
SW-01
R-01
SW-02
SRV-01
```

---

# 🧠 Critical Observation

Compare Layer 3 addressing.

### Source IP

```text
____________________________________
```

### Destination IP

```text
____________________________________
```

Now compare Layer 2 addresses on:

```text
PC-01 → R-01
```

and:

```text
R-01 → SRV-01
```

You should notice:

> **The MAC addresses change at the router.**

---

# 📦 Why?

The router removes the incoming Ethernet frame, processes the IP packet, and creates new Layer 2 framing for the next local network.

Conceptually:

```text
PC-01

Ethernet Frame A
        ↓
IP Packet
        ↓

R-01

Processes IP Packet

        ↓
Ethernet Frame B
        ↓

SRV-01
```

---

# 🧠 End-to-End IP

Even though the MAC addresses change, the original IP communication remains between:

```text
192.168.10.10
```

and:

```text
192.168.20.10
```

This is a key distinction:

```text
MAC
=
Local-link delivery
```

```text
IP
=
Logical end-to-end routing
```

---

# PART 5 — TROUBLESHOOTING

# 💥 Challenge 1 — Disconnect a PC

Disconnect PC-03 from SW-01.

Test:

```text
PC-01 → PC-02
```

and:

```text
PC-01 → PC-03
```

Record:

| Test | Result |
|---|---|
| PC-01 → PC-02 | PASS / FAIL |
| PC-01 → PC-03 | PASS / FAIL |

---

# 🧠 What Does This Suggest?

The problem likely affects:

> **PC-03's local connection**

rather than the whole LAN.

Possible areas:

- Cable
- NIC
- Switch port
- Physical connectivity

---

# 💥 Challenge 2 — Move a Device

Reconnect PC-03 using a different switch port.

Generate traffic.

Then run:

```text
show mac address-table
```

on SW-01.

Look for PC-03's MAC.

Question:

> Did the switch learn the MAC address on the new port?

```text
YES / NO
```

This demonstrates that MAC table information can change dynamically.

---

# 💥 Challenge 3 — Wrong Gateway

Change PC-01's default gateway from:

```text
192.168.10.1
```

to:

```text
192.168.10.254
```

Test:

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
| Local PC | PASS / FAIL |
| Remote Server | PASS / FAIL |

---

# 🧠 Explain the Result

Why might local Ethernet communication still work?

```text
____________________________________________________

____________________________________________________
```

Why does remote communication fail?

```text
____________________________________________________

____________________________________________________
```

Restore the correct gateway:

```text
192.168.10.1
```

---

# 💥 Challenge 4 — Broadcast Question

An ARP request is sent using:

```text
FF:FF:FF:FF:FF:FF
```

Will R-01 forward that Ethernet broadcast directly into the Server LAN?

### A. Yes

### B. No

Answer:

> **B — No**

Routers separate normal Layer 2 broadcast domains.

---

# 🧠 Knowledge Check

### 1.

What does MAC stand for?

### 2.

Which OSI layer is Ethernet primarily associated with?

### 3.

What is the Layer 2 PDU called?

### 4.

What command shows the ARP cache in Windows?

### 5.

What PowerShell command can display neighbor information?

### 6.

What is the Ethernet broadcast MAC address?

### 7.

What protocol resolves local IPv4 addresses to MAC addresses?

### 8.

Does a switch primarily learn from source or destination MAC addresses?

### 9.

What does a switch do when it does not know a destination MAC address?

### 10.

Does a router preserve the same Ethernet frame across different LANs?

---

# ✅ Knowledge Check Answers

### 1.

**Media Access Control**

### 2.

**OSI Layer 2 — Data Link**

### 3.

**Frame**

### 4.

```cmd
arp -a
```

### 5.

```powershell
Get-NetNeighbor
```

### 6.

```text
FF:FF:FF:FF:FF:FF
```

### 7.

**ARP**

### 8.

**Source MAC addresses**

### 9.

It may flood the unknown unicast frame within the appropriate Layer 2 domain.

### 10.

**No**

The router creates new Layer 2 framing for the next local link.

---

# 🎓 Network+ Challenge 1

A switch receives a frame with:

```text
Source MAC:
AA-AA-AA-AA-AA-AA
```

on port:

```text
Fa0/7
```

What does the switch learn?

### A.

The destination IP is on Fa0/7

### B.

AA-AA-AA-AA-AA-AA is reachable through Fa0/7

### C.

Fa0/7 is the default gateway

### D.

The switch learns nothing

Answer:

> **B**

---

# 🎓 Network+ Challenge 2

Which address represents an Ethernet broadcast?

### A.

```text
255.255.255.0
```

### B.

```text
127.0.0.1
```

### C.

```text
FF:FF:FF:FF:FF:FF
```

### D.

```text
0.0.0.0
```

Answer:

> **C**

---

# 🎓 Network+ Challenge 3

A workstation wants to reach a remote network.

Which MAC address is normally used as the local destination?

### A.

Remote server MAC

### B.

Default gateway MAC

### C.

DNS server MAC

### D.

Its own MAC

Answer:

> **B**

---

# 🎓 Network+ Challenge 4

A computer can reach local devices but not remote networks.

Which configuration should be checked early?

### A.

Default gateway

### B.

Monitor resolution

### C.

Computer wallpaper

### D.

Keyboard layout

Answer:

> **A**

---

# 📋 Lab Review

In this lab, you:

- Found your real MAC address
- Viewed multiple Windows network adapters
- Used `ipconfig /all`
- Used `arp -a`
- Used `Get-NetNeighbor`
- Identified your gateway's MAC address
- Captured ARP traffic
- Identified ARP broadcasts
- Examined Ethernet headers
- Compared MAC and IP addresses
- Examined remote traffic
- Built a switched LAN
- Inspected a switch MAC address table
- Watched switch MAC learning
- Observed broadcast behavior
- Observed unicast behavior
- Expanded the topology with a router
- Compared local and routed traffic
- Observed MAC addresses changing across a router
- Troubleshot Layer 2 and Layer 3 problems

---

# 🧠 What You Should Understand Now

Before moving on, you should be comfortable explaining:

```text
What is a MAC address?
```

```text
What is an Ethernet frame?
```

```text
How does a switch learn device locations?
```

```text
What is ARP?
```

```text
Why are ARP requests broadcasts?
```

```text
Why does remote traffic use the gateway's MAC?
```

```text
Why do MAC addresses change across routers?
```

If those questions make sense, you're ready for the next lesson.

---

# 💾 Packet Tracer Save File

Save your lab as:

```text
lab-06-ethernet-mac-addressing.pkt
```

Keep the completed `.pkt` file locally.

You do not need to upload your personal completed lab to the public repository.

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS

✅ Lessons 01–05
✅ Labs 01–05
✅ Project 01

        ↓

🔵 PHASE 2 — ADDRESSING & COMMUNICATION

✅ Lesson 06 — Ethernet & MAC Addressing
✅ Lab 06 — Ethernet & MAC Addressing

        ↓

🟡 NEXT:
Lesson 07 — IPv4 Addressing

        ↓

⬜ Lab 07 — IPv4 Addressing

⬜ Lesson 08 — Subnetting Fundamentals

⬜ Lab 08 — Subnetting Fundamentals

⬜ Lesson 09 — IPv6 Fundamentals

⬜ Lesson 10 — TCP, UDP, Ports & Protocols
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 07 — IPv4 Addressing**

In Lesson 07, you'll go deeper into:

- IPv4 address structure
- Network and host portions
- Private IPv4 ranges
- Public IPv4 addresses
- APIPA
- Loopback
- Default gateways
- Subnet masks
- CIDR notation
- Network addresses
- Broadcast addresses
- Usable host addresses

This will prepare you for:

> **Lesson 08 — Subnetting Fundamentals**

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Cisco Networking Companion](../resources/cisco-companion.md)**

➡️ **[Return to Main README](../README.md)**