# 🧪 Lab 11 — Switching Fundamentals

Welcome to **Lab 11 of Networking Fundamentals**.

In this lab, you'll stop treating the switch as a mysterious box.

You'll watch it:

```text
Receive Frames
      ↓
Learn MAC Addresses
      ↓
Build a MAC Table
      ↓
Forward Traffic
```

You'll also begin using:

> **Cisco IOS CLI**

for real switch administration tasks.

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Build a switched LAN
- Configure IPv4 hosts
- Test local connectivity
- Access the Cisco switch CLI
- Enter privileged EXEC mode
- Enter global configuration mode
- Rename a switch
- View interface status
- View the MAC address table
- Explain MAC learning
- Clear dynamic MAC entries
- Watch the switch relearn addresses
- Observe unknown unicast behavior
- Observe broadcast behavior
- Move a device between switch ports
- Verify MAC relearning
- Administratively disable a port
- Re-enable a port
- Identify Layer 1 vs. Layer 2 failures
- Understand why switching loops are dangerous

---

# 🎓 Network+ Focus

This lab reinforces:

- Layer 2 switching
- MAC addresses
- MAC address tables
- Frame forwarding
- Flooding
- Broadcasts
- Collision domains
- Managed switches
- Switch interfaces
- Cisco CLI concepts
- Spanning Tree concepts
- Troubleshooting

---

# ⏱️ Estimated Time

**60–75 minutes**

---

# 🌐 PART 1 — BUILD THE NETWORK

Open:

> **Cisco Packet Tracer**

Add:

```text
PC-01
PC-02
PC-03
SW-01
```

Use a Cisco 2960 or similar Layer 2 switch available in Packet Tracer.

Build:

```text
PC-01 ───── Fa0/1
               │
PC-02 ───── Fa0/2 ─── SW-01
               │
PC-03 ───── Fa0/3
```

Your exact port numbers may vary.

---

# 📍 PART 2 — CONFIGURE THE HOSTS

Use:

```text
192.168.10.0/24
```

Configure:

### PC-01

```text
IP:
192.168.10.10

Mask:
255.255.255.0
```

### PC-02

```text
IP:
192.168.10.20

Mask:
255.255.255.0
```

### PC-03

```text
IP:
192.168.10.30

Mask:
255.255.255.0
```

No default gateway is required for this portion.

Why?

> All three devices are on the same local IP subnet.

---

# 📋 Addressing Table

| Device | IPv4 | Mask |
|---|---|---|
| PC-01 | 192.168.10.10 | 255.255.255.0 |
| PC-02 | 192.168.10.20 | 255.255.255.0 |
| PC-03 | 192.168.10.30 | 255.255.255.0 |

---

# 🧪 PART 3 — TEST CONNECTIVITY

From PC-01:

```text
ping 192.168.10.20
```

Then:

```text
ping 192.168.10.30
```

Record:

```text
PC-01 → PC-02:

PASS / FAIL

PC-01 → PC-03:

PASS / FAIL
```

---

# 🖥️ PART 4 — OPEN THE SWITCH CLI

Click:

```text
SW-01
```

Open:

> **CLI**

You may initially see:

```text
Switch>
```

This is:

> **User EXEC Mode**

---

# Step 1 — Privileged EXEC

Enter:

```text
enable
```

You should see:

```text
Switch#
```

---

# Step 2 — Configuration Mode

Enter:

```text
configure terminal
```

You should see:

```text
Switch(config)#
```

---

# Step 3 — Rename the Switch

Enter:

```text
hostname SW-01
```

Prompt should become:

```text
SW-01(config)#
```

---

# Step 4 — Exit Configuration Mode

Enter:

```text
end
```

You should return to:

```text
SW-01#
```

---

# 🔍 PART 5 — VIEW INTERFACE STATUS

Run:

```text
show interfaces status
```

Find the ports connected to:

```text
PC-01
PC-02
PC-03
```

Record:

| Device | Switch Port | Status |
|---|---|---|
| PC-01 | | |
| PC-02 | | |
| PC-03 | | |

---

# 🧠 Question

What does:

```text
connected
```

tell you?

> The switch sees an active physical Ethernet link on that interface.

This doesn't necessarily prove that IP configuration is correct.

---

# 📋 PART 6 — VIEW THE MAC ADDRESS TABLE

Run:

```text
show mac address-table
```

Look for:

```text
DYNAMIC
```

entries.

Record:

| MAC Address | Type | Port |
|---|---|---|
| | | |
| | | |
| | | |

---

# 🧠 What Happened?

When PCs generated traffic, SW-01 examined:

> **Source MAC addresses**

and learned:

```text
MAC Address
      ↓
Switch Port
```

---

# 🔎 PART 7 — MATCH A PC TO ITS MAC

Open PC-01.

Use:

```text
ipconfig /all
```

or inspect the Packet Tracer interface configuration.

Find PC-01's MAC address.

Record:

```text
PC-01 MAC:

____________________________________
```

Return to SW-01.

Run:

```text
show mac address-table
```

Find that MAC.

Record:

```text
Switch Port:

____________________________________
```

You have now proven:

```text
PC-01 MAC
      ↓
Learned on its physical switch port
```

---

# 🧹 PART 8 — CLEAR THE MAC TABLE

From SW-01:

```text
clear mac address-table dynamic
```

Then immediately run:

```text
show mac address-table
```

Some or all dynamic entries should be gone.

---

# 🧠 What Did You Remove?

You removed:

> **Dynamically learned MAC entries**

You did **not** delete the PCs' actual MAC addresses.

The switch simply forgot where they were located.

---

# 🔄 PART 9 — WATCH THE SWITCH RELEARN

From PC-01:

```text
ping 192.168.10.20
```

Return to SW-01.

Run:

```text
show mac address-table
```

What happened?

```text
____________________________________

____________________________________
```

Expected:

> The switch learned MAC addresses again from newly received frames.

---

# 🔬 PART 10 — SIMULATION MODE

Switch Packet Tracer to:

> **Simulation Mode**

Clear the dynamic MAC table again if supported:

```text
clear mac address-table dynamic
```

Now generate traffic from:

```text
PC-01
```

to:

```text
PC-02
```

Use:

> **Capture / Forward**

---

# 👀 Watch the First Communication

During initial communication you may observe:

```text
ARP
```

followed by:

```text
ICMP
```

Remember:

```text
ARP Request
=
Broadcast
```

The switch doesn't initially know every destination.

---

# 📢 PART 11 — OBSERVE A BROADCAST

Inspect the ARP request.

Look for:

```text
Destination MAC:

FFFF.FFFF.FFFF
```

or equivalent notation.

This is:

> **Ethernet Broadcast**

---

# 🧠 What Does the Switch Do?

The switch floods the broadcast to other relevant ports in the same VLAN.

Conceptually:

```text
          SW-01
         /  |  \
        /   |   \
   PC-01  PC-02 PC-03
      ↑
    Sender

Broadcast
      ↓

PC-02 receives copy
PC-03 receives copy
```

---

# ➡️ PART 12 — OBSERVE KNOWN UNICAST

After the switch has learned the MAC addresses, generate additional traffic:

```text
PC-01
   ↓
PC-02
```

Observe SW-01.

Once the destination MAC is known, the switch can forward the unicast frame toward:

> **PC-02's specific port**

instead of flooding it everywhere.

---

# ⭐ Important Comparison

```text
UNKNOWN DESTINATION
        ↓
Flood
```

versus:

```text
KNOWN DESTINATION
        ↓
Forward toward known port
```

---

# 🔌 PART 13 — MOVE A DEVICE

Disconnect PC-03 from its current switch port.

Suppose it was:

```text
Fa0/3
```

Reconnect it to:

```text
Fa0/8
```

or another unused port.

---

# 🧪 Generate Traffic

From PC-03:

```text
ping 192.168.10.10
```

Then on SW-01:

```text
show mac address-table
```

Find PC-03's MAC.

---

# 🧠 What Should Happen?

The switch should eventually associate PC-03's MAC with:

> **The new switch port**

This demonstrates that MAC table information is dynamic.

---

# 🛠️ PART 14 — ADMINISTRATIVELY DISABLE A PORT

Identify PC-02's port.

Example:

```text
Fa0/2
```

Enter:

```text
configure terminal
```

Then:

```text
interface fastethernet 0/2
```

Then:

```text
shutdown
```

---

# 🧪 Test PC-02

From PC-01:

```text
ping 192.168.10.20
```

Record:

```text
PASS / FAIL
```

---

# 🔍 Check the Interface

On SW-01:

```text
show interfaces status
```

Look at PC-02's port.

---

# 🧠 What Did You Create?

This is not:

> **An IP addressing problem**

You intentionally disabled:

> **The switch interface**

---

# 🔧 Repair the Port

Enter:

```text
configure terminal
```

```text
interface fastethernet 0/2
```

```text
no shutdown
```

Then:

```text
end
```

Retest:

```text
ping 192.168.10.20
```

---

# 🧠 Troubleshooting Lesson

This demonstrates why:

```text
Correct IP Address
```

doesn't guarantee connectivity.

You also need:

```text
Working NIC
Working Cable
Working Switch Port
Correct Switch Configuration
```

---

# 🔍 PART 15 — INSPECT AN INTERFACE

Run:

```text
show interfaces fastethernet 0/1
```

Look for information about:

- Interface status
- Line protocol
- Duplex
- Speed
- Traffic
- Errors

Exact output depends on the Packet Tracer switch.

---

# 📝 Record

```text
Status:

____________________________________

Duplex:

____________________________________

Speed:

____________________________________
```

---

# 🌪️ PART 16 — SWITCHING LOOP DEMONSTRATION

## ⚠️ Important

We're going to examine a Layer 2 loop concept in:

> **Packet Tracer only**

Do not intentionally create switching loops on a production network.

---

# Add a Second Switch

Add:

```text
SW-02
```

Connect a PC to SW-02.

Then connect:

```text
SW-01
   │
   │
SW-02
```

with one Ethernet link.

Everything should work normally.

---

# Add Redundancy

Now add a second Ethernet link between:

```text
SW-01
```

and:

```text
SW-02
```

Conceptually:

```text
SW-01 ═════ SW-02
```

Two physical Layer 2 paths now exist.

---

# 🧠 Observe the Switches

Depending on the Packet Tracer model/configuration, you may notice one of the redundant links isn't forwarding normally.

Why?

> **Spanning Tree Protocol**

is designed to prevent the redundant topology from creating a Layer 2 forwarding loop.

---

# 🛡️ STP Concept

Instead of allowing:

```text
SW-01
 ↕ ↕
SW-02
```

to forward across both redundant paths simultaneously, STP can logically block one path.

Conceptually:

```text
SW-01
 │
 │ Active
 │
SW-02

Second Link
    X
Blocked by STP
```

---

# ⭐ Important

Do not disable STP just to watch a broadcast storm.

The purpose of this exercise is to understand:

> **Why STP is necessary.**

---

# 💥 PART 17 — TROUBLESHOOTING CHALLENGE

You're the technician.

You receive:

> "PC-03 can't connect to anything."

You are not told what's wrong.

Use:

```text
Physical inspection
show interfaces status
show mac address-table
ping
Interface configuration
```

to investigate.

---

# 📋 Document Your Troubleshooting

```text
Problem:

____________________________________


Initial Symptoms:

____________________________________


What Still Worked:

____________________________________


Switch Port:

____________________________________


Was MAC Learned?

____________________________________


Root Cause:

____________________________________


Solution:

____________________________________


Verification:

____________________________________
```

---

# 🧠 PART 18 — COMMAND PRACTICE

Without looking back, match each command.

### Enter privileged mode

```text
____________________________________
```

### Enter configuration mode

```text
____________________________________
```

### View MAC table

```text
____________________________________
```

### View interface status

```text
____________________________________
```

### Disable an interface

```text
____________________________________
```

### Enable an interface

```text
____________________________________
```

---

# ✅ Answers

```text
enable
```

```text
configure terminal
```

```text
show mac address-table
```

```text
show interfaces status
```

```text
shutdown
```

```text
no shutdown
```

---

# 🧠 Knowledge Check

### 1.

Which MAC address does a switch learn from?

### 2.

Where does the switch store learned MAC information?

### 3.

What happens to an unknown unicast?

### 4.

What happens to a broadcast?

### 5.

What is the Ethernet broadcast MAC?

### 6.

What command displays the MAC address table?

### 7.

What does `shutdown` do on an interface?

### 8.

What does `no shutdown` do?

### 9.

What protocol protects against Layer 2 loops?

### 10.

Why might a PoE device stay powered without a separate power adapter?

---

# ✅ Answers

1. **Source MAC**
2. **MAC address table**
3. **Flooded within the VLAN**
4. **Flooded within the broadcast domain/VLAN**
5. **FF:FF:FF:FF:FF:FF**
6. **`show mac address-table`**
7. **Administratively disables the interface**
8. **Enables the interface**
9. **Spanning Tree Protocol**
10. **The switch can provide power through the Ethernet cable**

---

# 🎓 Network+ Challenge 1

Only one user connected to SW-01 has lost connectivity.

Twenty other users on SW-01 are working normally.

Where should you start?

> **The affected endpoint, cable, and switch port**

rather than assuming the entire switch has failed.

---

# 🎓 Network+ Challenge 2

A switch doesn't know the destination MAC of an incoming unicast frame.

What happens?

> **Unknown unicast flooding within the VLAN**

---

# 🎓 Network+ Challenge 3

Two switches are accidentally connected with redundant Layer 2 paths and loop prevention isn't functioning.

What major problem can occur?

> **Layer 2 loop / broadcast storm**

---

# 🎓 Network+ Challenge 4

Which command is most useful for determining which switch port learned a particular MAC?

### A. `ipconfig`
### B. `show mac address-table`
### C. `nslookup`
### D. `tracert`

> **Answer: B**

---

# 📋 Lab Review

In this lab, you:

- Built a switched Ethernet LAN
- Configured three hosts
- Tested local communication
- Entered Cisco IOS CLI
- Entered privileged EXEC mode
- Entered configuration mode
- Renamed a switch
- Viewed interface status
- Viewed the MAC address table
- Matched endpoint MACs to switch ports
- Cleared dynamic MAC entries
- Watched MAC addresses relearn
- Observed broadcasts
- Observed known unicast forwarding
- Moved a PC between switch ports
- Verified MAC relearning
- Administratively disabled a port
- Re-enabled the port
- Inspected interface information
- Built redundant switch links
- Observed the purpose of STP
- Practiced switch troubleshooting

---

# 💾 Save Your Packet Tracer Lab

Save as:

```text
lab-11-switching-fundamentals.pkt
```

You don't need to upload the completed `.pkt` file to the repository.

Building the topology is part of the exercise.

---

# 🏆 Lab Complete

You should no longer think of a switch as:

```text
Ethernet cables
      ↓
Magic box
      ↓
Network
```

Instead:

```text
Frame Arrives
      ↓
Learn Source MAC
      ↓
Check Destination MAC
      ↓
Known?
 ┌────┴────┐
YES        NO
 ↓          ↓
Forward    Flood
      ↓
Update MAC Table
```

And when something breaks:

```text
Endpoint
   ↓
Cable
   ↓
Switch Port
   ↓
Port State
   ↓
MAC Learning
   ↓
Configuration
   ↓
Upstream Network
```

That's a much stronger troubleshooting mindset.

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

        ↓

🟡 NEXT:
Lesson 12 — VLANs & Network Segmentation

⬜ Lab 12 — VLANs & Network Segmentation

        ↓

⬜ Lesson 13 — Routing Fundamentals
⬜ Lab 13

⬜ Lesson 14 — DHCP
⬜ Lab 14

⬜ Lesson 15 — DNS
⬜ Lab 15

⬜ Lesson 16 — NAT & Address Translation
⬜ Lab 16
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 12 — VLANs and Network Segmentation**

You'll take the switching knowledge from this lab and turn:

```text
ONE PHYSICAL SWITCH
```

into multiple logical networks:

```text
VLAN 10
Employees

VLAN 20
Servers

VLAN 30
Voice

VLAN 40
Guest
```

You'll learn:

- Access ports
- Trunk ports
- 802.1Q
- VLAN tagging
- Native VLANs
- Broadcast-domain separation
- VLAN-to-subnet mapping
- Inter-VLAN routing
- Router-on-a-stick
- VLAN troubleshooting

And you'll configure the VLANs yourself using the Cisco CLI.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**