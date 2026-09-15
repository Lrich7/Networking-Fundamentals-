# 🧪 Lab 13 — Routing Fundamentals

Welcome to **Lab 13 of Networking Fundamentals**.

In previous labs, you used routers to connect networks.

This time, the router itself is the focus.

You'll build:

```text id="l13a01"
LAN A
192.168.10.0/24
        │
        ▼
      R-01
        │
        │
   10.0.0.0/30
        │
        ▼
      R-02
        │
        ▼
LAN B
192.168.20.0/24
```

Initially:

> **The routers will not know how to reach the remote LANs.**

You'll fix that yourself.

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Build a multi-router topology
- Configure router interfaces
- Verify interface status
- Read a routing table
- Identify connected routes
- Identify local routes
- Configure static routes
- Identify next-hop addresses
- Test end-to-end routing
- Use `ping`
- Use `tracert` / `traceroute`
- Understand return routing
- Configure a default route
- Troubleshoot missing routes
- Troubleshoot wrong next hops
- Troubleshoot incorrect gateways
- Troubleshoot disabled router interfaces
- Document a routed network

---

# 🎓 Network+ Focus

This lab reinforces:

- Routing tables
- Routers
- Default gateways
- Connected routes
- Static routes
- Default routes
- Next hops
- IPv4 prefixes
- Route selection
- Layer 3 troubleshooting

---

# ⏱️ Estimated Time

**75–90 minutes**

---

# 🏗️ PART 1 — BUILD THE TOPOLOGY

Open:

> **Cisco Packet Tracer**

Add:

```text id="l13a02"
PC-01
SW-01
R-01
R-02
SW-02
SRV-01
```

Build:

```text id="l13a03"
PC-01
  │
  ▼
SW-01
  │
  ▼
R-01
  │
  │
  ▼
R-02
  │
  ▼
SW-02
  │
  ▼
SRV-01
```

---

# 🌐 PART 2 — NETWORK PLAN

We'll use three networks.

## LAN A

```text id="l13a04"
192.168.10.0/24
```

## Router Transit Network

```text id="l13a05"
10.0.0.0/30
```

## LAN B

```text id="l13a06"
192.168.20.0/24
```

---

# 📋 Addressing Table

| Device | Interface | IPv4 | Mask |
|---|---|---|---|
| PC-01 | NIC | 192.168.10.10 | 255.255.255.0 |
| R-01 | LAN | 192.168.10.1 | 255.255.255.0 |
| R-01 | Transit | 10.0.0.1 | 255.255.255.252 |
| R-02 | Transit | 10.0.0.2 | 255.255.255.252 |
| R-02 | LAN | 192.168.20.1 | 255.255.255.0 |
| SRV-01 | NIC | 192.168.20.10 | 255.255.255.0 |

---

# 🧠 Why `/30` for the Transit Link?

A `/30` network provides four addresses.

For:

```text id="l13a07"
10.0.0.0/30
```

we have:

```text id="l13a08"
10.0.0.0
Network

10.0.0.1
R-01

10.0.0.2
R-02

10.0.0.3
Broadcast
```

That's enough for this point-to-point lab.

---

# 🖥️ PART 3 — CONFIGURE PC-01

Configure:

```text id="l13a09"
IP Address:
192.168.10.10

Subnet Mask:
255.255.255.0

Default Gateway:
192.168.10.1
```

---

# 🖥️ PART 4 — CONFIGURE SRV-01

Configure:

```text id="l13a10"
IP Address:
192.168.20.10

Subnet Mask:
255.255.255.0

Default Gateway:
192.168.20.1
```

---

# 🔀 PART 5 — CONFIGURE R-01

Open R-01 CLI.

Enter:

```text id="l13a11"
enable
```

Then:

```text id="l13a12"
configure terminal
```

Rename:

```text id="l13a13"
hostname R-01
```

---

# Configure the LAN Interface

Use the actual interface connected to SW-01.

Example:

```text id="l13a14"
interface gigabitethernet 0/0
```

Then:

```text id="l13a15"
ip address 192.168.10.1 255.255.255.0
```

Enable:

```text id="l13a16"
no shutdown
```

Then:

```text id="l13a17"
exit
```

---

# Configure the Transit Interface

Example:

```text id="l13a18"
interface gigabitethernet 0/1
```

Configure:

```text id="l13a19"
ip address 10.0.0.1 255.255.255.252
```

Enable:

```text id="l13a20"
no shutdown
```

Then:

```text id="l13a21"
end
```

---

# 🔀 PART 6 — CONFIGURE R-02

Open R-02 CLI.

```text id="l13a22"
enable
```

```text id="l13a23"
configure terminal
```

```text id="l13a24"
hostname R-02
```

---

# Configure Transit Interface

Example:

```text id="l13a25"
interface gigabitethernet 0/0
```

Then:

```text id="l13a26"
ip address 10.0.0.2 255.255.255.252
```

```text id="l13a27"
no shutdown
```

```text id="l13a28"
exit
```

---

# Configure LAN B Interface

Example:

```text id="l13a29"
interface gigabitethernet 0/1
```

Then:

```text id="l13a30"
ip address 192.168.20.1 255.255.255.0
```

```text id="l13a31"
no shutdown
```

Then:

```text id="l13a32"
end
```

---

# 🔍 PART 7 — VERIFY INTERFACES

On R-01:

```text id="l13a33"
show ip interface brief
```

On R-02:

```text id="l13a34"
show ip interface brief
```

Record:

### R-01

| Interface | IP | Status | Protocol |
|---|---|---|---|
| LAN | | | |
| Transit | | | |

### R-02

| Interface | IP | Status | Protocol |
|---|---|---|---|
| Transit | | | |
| LAN | | | |

You want:

```text id="l13a35"
up
up
```

for the interfaces you're using.

---

# 🧪 PART 8 — TEST DIRECTLY CONNECTED LINKS

From PC-01:

```text id="l13a36"
ping 192.168.10.1
```

Expected:

> **Success**

From R-01:

```text id="l13a37"
ping 10.0.0.2
```

Expected:

> **Success**

From R-02:

```text id="l13a38"
ping 192.168.20.10
```

Expected:

> **Success**

If these don't work, fix them before continuing.

---

# 📖 PART 9 — VIEW R-01 ROUTING TABLE

On R-01:

```text id="l13a39"
show ip route
```

Find routes for:

```text id="l13a40"
192.168.10.0/24
```

and:

```text id="l13a41"
10.0.0.0/30
```

They should be:

> **Connected**

---

# 📝 Record R-01 Routes

```text id="l13a42"
Connected LAN:

________________________________


Connected Transit Network:

________________________________
```

---

# 📖 PART 10 — VIEW R-02 ROUTING TABLE

On R-02:

```text id="l13a43"
show ip route
```

Find:

```text id="l13a44"
10.0.0.0/30
```

and:

```text id="l13a45"
192.168.20.0/24
```

---

# ❓ What's Missing?

Does R-01 currently have a route for:

```text id="l13a46"
192.168.20.0/24
```

Does R-02 have a route for:

```text id="l13a47"
192.168.10.0/24
```

At this point:

> **No.**

---

# 🧪 PART 11 — TEST BEFORE STATIC ROUTING

From PC-01:

```text id="l13a48"
ping 192.168.20.10
```

Expected:

> **Failure**

---

# 🧠 Why?

PC-01 knows:

```text id="l13a49"
Remote network
      ↓
Send to 192.168.10.1
```

R-01 receives the packet.

But R-01 does not yet have a route for:

```text id="l13a50"
192.168.20.0/24
```

---

# 🛣️ PART 12 — CONFIGURE R-01 STATIC ROUTE

On R-01:

```text id="l13a51"
configure terminal
```

Add:

```text id="l13a52"
ip route 192.168.20.0 255.255.255.0 10.0.0.2
```

Then:

```text id="l13a53"
end
```

---

# 🔍 Verify

Run:

```text id="l13a54"
show ip route
```

Look for something similar to:

```text id="l13a55"
S    192.168.20.0/24 via 10.0.0.2
```

---

# 🧪 PART 13 — TEST AGAIN

From PC-01:

```text id="l13a56"
ping 192.168.20.10
```

Does it work?

It may still:

> **Fail**

Why?

---

# ⭐ Return Path

R-01 now knows how to send the request to LAN B.

But R-02 still doesn't know how to reach:

```text id="l13a57"
192.168.10.0/24
```

We need a:

> **Return Route**

---

# 🛣️ PART 14 — CONFIGURE R-02 STATIC ROUTE

On R-02:

```text id="l13a58"
configure terminal
```

Add:

```text id="l13a59"
ip route 192.168.10.0 255.255.255.0 10.0.0.1
```

Then:

```text id="l13a60"
end
```

---

# 🔍 Verify

Run:

```text id="l13a61"
show ip route
```

Find:

```text id="l13a62"
S    192.168.10.0/24 via 10.0.0.1
```

---

# 🌐 PART 15 — TEST END-TO-END CONNECTIVITY

From PC-01:

```text id="l13a63"
ping 192.168.20.10
```

Expected:

> **Success**

From SRV-01:

```text id="l13a64"
ping 192.168.10.10
```

Expected:

> **Success**

---

# 🏆 Major Checkpoint

You have now manually built:

```text id="l13a65"
LAN A
192.168.10.0/24
       ↓
      R-01
       ↓
Static Route
       ↓
      R-02
       ↓
LAN B
192.168.20.0/24
```

and a route back.

---

# 🧭 PART 16 — TRACE THE ROUTE

From PC-01:

```text id="l13a66"
tracert 192.168.20.10
```

Observe the Layer 3 hops.

You should conceptually see:

```text id="l13a67"
192.168.10.1
      ↓
10.0.0.2
      ↓
192.168.20.10
```

Exact Packet Tracer behavior/output can vary.

---

# 🔬 PART 17 — SIMULATION MODE

Switch to:

> **Simulation Mode**

Send a Simple PDU from:

```text id="l13a68"
PC-01
```

to:

```text id="l13a69"
SRV-01
```

Use:

> **Capture / Forward**

Follow the packet:

```text id="l13a70"
PC-01
   ↓
SW-01
   ↓
R-01
   ↓
R-02
   ↓
SW-02
   ↓
SRV-01
```

---

# 🧠 At R-01

Ask:

> What destination IP does the packet have?

It should still be:

```text id="l13a71"
192.168.20.10
```

R-01 checks its routing table.

It matches:

```text id="l13a72"
192.168.20.0/24
```

and forwards toward:

```text id="l13a73"
10.0.0.2
```

---

# ⭐ Important Layer 2 vs. Layer 3 Review

Across router hops:

```text id="l13a74"
IP Source/Destination
```

generally remain the original endpoints in this no-NAT lab.

But:

```text id="l13a75"
Ethernet Source/Destination MAC
```

change as frames are rebuilt for each local link.

---

# 💥 PART 18 — BREAK THE RETURN ROUTE

On R-02, remove:

```text id="l13a76"
ip route 192.168.10.0 255.255.255.0 10.0.0.1
```

Use:

```text id="l13a77"
configure terminal
```

```text id="l13a78"
no ip route 192.168.10.0 255.255.255.0 10.0.0.1
```

Then:

```text id="l13a79"
end
```

---

# 🧪 Test

From PC-01:

```text id="l13a80"
ping 192.168.20.10
```

Investigate what happens.

---

# 📝 Troubleshooting Record

```text id="l13a81"
Source:

____________________________

Destination:

____________________________

Forward Route Exists?

YES / NO

Return Route Exists?

YES / NO

Root Cause:

____________________________
```

---

# 🔧 Repair

Restore:

```text id="l13a82"
ip route 192.168.10.0 255.255.255.0 10.0.0.1
```

Verify connectivity.

---

# 💥 PART 19 — WRONG NEXT-HOP CHALLENGE

Remove R-01's correct static route.

Then intentionally configure:

```text id="l13a83"
ip route 192.168.20.0 255.255.255.0 10.0.0.99
```

Test:

```text id="l13a84"
PC-01 → SRV-01
```

---

# 🔍 Investigate

Run:

```text id="l13a85"
show ip route
```

and:

```text id="l13a86"
show running-config
```

What is wrong?

> **The route references an incorrect/unreachable next hop.**

---

# 🔧 Repair

Remove the bad route:

```text id="l13a87"
no ip route 192.168.20.0 255.255.255.0 10.0.0.99
```

Restore:

```text id="l13a88"
ip route 192.168.20.0 255.255.255.0 10.0.0.2
```

Retest.

---

# 💥 PART 20 — WRONG DEFAULT GATEWAY

Change PC-01's gateway to:

```text id="l13a89"
192.168.10.254
```

Now test:

```text id="l13a90"
ping 192.168.10.1
```

Then:

```text id="l13a91"
ping 192.168.20.10
```

---

# 🧠 Think About the Results

PC-01 may still be able to reach:

```text id="l13a92"
192.168.10.1
```

because that address is local.

But it cannot properly send remote traffic through the incorrect gateway.

This reinforces:

```text id="l13a93"
Local Network
≠
Default Gateway Required
```

while:

```text id="l13a94"
Remote Network
=
Gateway Required
```

---

# 🔧 Repair

Restore:

```text id="l13a95"
192.168.10.1
```

---

# 💥 PART 21 — DISABLE THE TRANSIT LINK

On R-01, identify the interface connected to R-02.

Enter interface configuration and use:

```text id="l13a96"
shutdown
```

---

# 🧪 Test

Try:

```text id="l13a97"
PC-01 → SRV-01
```

Expected:

> **Failure**

---

# 🔍 Diagnose

On R-01:

```text id="l13a98"
show ip interface brief
```

Then:

```text id="l13a99"
show ip route
```

Observe how interface state affects routing.

---

# 🔧 Repair

Use:

```text id="l13a100"
no shutdown
```

Wait for the link to recover.

Retest.

---

# 🌎 PART 22 — DEFAULT ROUTE EXERCISE

Now let's practice a default route.

On R-01, remove the specific route:

```text id="l13a101"
no ip route 192.168.20.0 255.255.255.0 10.0.0.2
```

Instead configure:

```text id="l13a102"
ip route 0.0.0.0 0.0.0.0 10.0.0.2
```

---

# 🔍 Verify

Run:

```text id="l13a103"
show ip route
```

Look for:

```text id="l13a104"
S*   0.0.0.0/0
```

or similar output.

The `*` identifies a:

> **Candidate Default Route**

---

# 🧪 Test

From PC-01:

```text id="l13a105"
ping 192.168.20.10
```

It should still work if the rest of the routing is correct.

---

# 🧠 Why?

R-01 doesn't have a more specific route for LAN B.

Therefore it uses:

```text id="l13a106"
0.0.0.0/0
      ↓
10.0.0.2
```

---

# ⭐ Important

A default route is not automatically:

> **An Internet route**

It simply means:

> **Use this route when no more specific route matches.**

In many real networks, the default route happens to point toward an Internet/firewall/upstream connection.

---

# 🎯 PART 23 — LONGEST-PREFIX MATCH EXERCISE

Suppose a router has:

```text id="l13a107"
0.0.0.0/0
192.168.0.0/16
192.168.20.0/24
```

Destination:

```text id="l13a108"
192.168.20.50
```

Which route wins?

```text id="l13a109"
________________________________
```

Answer:

> **192.168.20.0/24**

because `/24` is the most specific matching route.

---

# 🖥️ PART 24 — WINDOWS ROUTING TABLE

On your Windows computer, open Command Prompt.

Run:

```text id="l13a110"
route print
```

Look for:

```text id="l13a111"
0.0.0.0
```

in the IPv4 routing table.

---

# ⚡ PowerShell

Run:

```text id="l13a112"
Get-NetRoute -AddressFamily IPv4
```

Find:

```text id="l13a113"
0.0.0.0/0
```

Record:

```text id="l13a114"
Default Next Hop:

____________________________


Interface:

____________________________
```

---

# 🧭 PART 25 — TRACE A REAL PATH

If you're on a network where testing is permitted:

```text id="l13a115"
tracert 8.8.8.8
```

Observe the first hop.

It will commonly be:

> **Your local default gateway or another nearby routed device.**

Some later routers may not respond to traceroute probes, which does not automatically mean the path is broken.

---

# 📝 PART 26 — ROUTING DOCUMENTATION

Complete:

| Network | Connected To | Route Type |
|---|---|---|
| 192.168.10.0/24 | R-01 | Connected |
| 10.0.0.0/30 | R-01 / R-02 | Connected |
| 192.168.20.0/24 | R-02 | Connected |

Then document remote routing.

### R-01

```text id="l13a116"
Remote Destination:

____________________________

Next Hop:

____________________________

Route Type:

____________________________
```

### R-02

```text id="l13a117"
Remote Destination:

____________________________

Next Hop:

____________________________

Route Type:

____________________________
```

---

# 🛠️ PART 27 — TROUBLESHOOTING CHALLENGE

A user reports:

> "PC-01 can reach its gateway, but it can't reach SRV-01."

You aren't told what's wrong.

Check:

```text id="l13a118"
PC Addressing
      ↓
Default Gateway
      ↓
R-01 Interfaces
      ↓
R-01 Routing Table
      ↓
Transit Connectivity
      ↓
R-02 Routing Table
      ↓
Server Gateway
      ↓
Return Route
```

Document:

```text id="l13a119"
Problem:

________________________________


What Worked:

________________________________


What Failed:

________________________________


First Router Reached:

________________________________


Destination Route Present?

YES / NO


Return Route Present?

YES / NO


Root Cause:

________________________________


Solution:

________________________________


Verification:

________________________________
```

---

# 🧠 Knowledge Check

### 1.

What command displays the Cisco routing table?

### 2.

What does `C` represent?

### 3.

What does `S` represent?

### 4.

What is R-01's next hop toward LAN B?

### 5.

What is R-02's next hop toward LAN A?

### 6.

Why are routes needed in both directions?

### 7.

What is the IPv4 default route?

### 8.

What route wins when several prefixes match?

### 9.

What command quickly displays Cisco interface status?

### 10.

What Windows command displays the routing table?

---

# ✅ Answers

1. **`show ip route`**
2. **Connected**
3. **Static**
4. **10.0.0.2**
5. **10.0.0.1**
6. **Reply traffic needs a return path**
7. **`0.0.0.0/0`**
8. **The most specific route / longest-prefix match**
9. **`show ip interface brief`**
10. **`route print`**

---

# 🎓 Network+ Challenge 1

R-01 has:

```text id="l13a120"
0.0.0.0/0
192.168.0.0/16
192.168.20.0/24
```

Destination:

```text id="l13a121"
192.168.20.10
```

Which route wins?

> **192.168.20.0/24**

---

# 🎓 Network+ Challenge 2

PC-01 can reach its gateway.

R-01 can reach R-02.

R-02 can reach SRV-01.

But PC-01 can't receive replies from SRV-01.

What should you check?

> **The return path toward 192.168.10.0/24.**

---

# 🎓 Network+ Challenge 3

Which route matches every IPv4 destination?

> **0.0.0.0/0**

---

# 🎓 Network+ Challenge 4

A router has no matching route and no default route.

What should it generally do with the packet?

> **Drop it.**

---

# 🎓 Network+ Challenge 5

A static route points to a nonexistent next-hop IP.

What type of problem is this?

> **Routing configuration / incorrect next hop**

---

# 📋 Lab Review

In this lab, you:

- Built two LANs
- Built a router transit network
- Configured two routers
- Used a `/30` transit subnet
- Configured endpoint gateways
- Verified router interfaces
- Viewed routing tables
- Identified connected routes
- Identified local routes
- Observed missing remote routes
- Configured static routes
- Configured return routing
- Tested end-to-end connectivity
- Traced the routed path
- Used Simulation Mode
- Observed Layer 3 forwarding
- Broke the return route
- Troubleshot an incorrect next hop
- Troubleshot a wrong host gateway
- Troubleshot a disabled router interface
- Configured a default route
- Practiced longest-prefix match
- Viewed the Windows routing table
- Documented a routed network

---

# 💾 Save Your Packet Tracer Lab

Save as:

```text id="l13a122"
lab-13-routing-fundamentals.pkt
```

You don't need to upload the completed `.pkt` file to the public repository.

Building the topology yourself is part of the lab.

---

# 🏆 Lab Complete

You can now look at:

```text id="l13a123"
PC-01
   ↓
R-01
   ↓
R-02
   ↓
SRV-01
```

and understand that every Layer 3 device must answer:

```text id="l13a124"
What is the destination IP?
        ↓
Which routes match?
        ↓
Which route is most specific?
        ↓
What is the next hop?
        ↓
Which interface should I use?
        ↓
Forward the packet
```

And troubleshooting now becomes:

```text id="l13a125"
Can I reach the gateway?
        ↓
Does the router know the destination?
        ↓
Can it reach the next hop?
        ↓
Does the next router know the destination?
        ↓
Is there a route back?
```

---

# 📍 Course Progress

```text id="l13a126"
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

        ↓

🟡 NEXT:
Lesson 14 — DHCP

⬜ Lab 14 — DHCP

        ↓

⬜ Lesson 15 — DNS
⬜ Lab 15

⬜ Lesson 16 — NAT & Address Translation
⬜ Lab 16

        ↓

🏗️ Project 03
Build a Routed Small-Business Network
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 14 — DHCP**

So far, we've manually configured addresses such as:

```text id="l13a127"
IP Address
Subnet Mask
Default Gateway
DNS Server
```

That works in a small lab.

It doesn't scale well when you have:

```text id="l13a128"
10 Devices
100 Devices
1,000 Devices
```

Next we'll learn how:

> **DHCP automatically provides network configuration to clients.**

We'll cover:

- DHCP clients and servers
- DHCP scopes
- Address pools
- Exclusions
- Reservations
- Lease times
- Default gateway options
- DNS options
- DORA
- DHCP relay
- `ipconfig /release`
- `ipconfig /renew`
- APIPA troubleshooting
- Packet Tracer DHCP configuration

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**
