# Lesson 21 — Switching Fundamentals

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain the role of an Ethernet switch.
- Explain MAC address learning and forwarding.
- Describe flooding, forwarding, and filtering.
- Explain collision and broadcast domains.
- Recognize basic switch interface states.
- Explain why switching loops are dangerous.
- Describe Spanning Tree Protocol at a beginner level.
- Use Cisco commands to inspect switch operation.

---

# What Does a Switch Do?

A Layer 2 switch forwards Ethernet frames based primarily on destination MAC addresses.

```text
PC1 ─┐
PC2 ─┼─ Switch
PC3 ─┘
```

The switch learns where devices are connected.

---

# MAC Address Learning

When a frame enters a switch, the switch examines the source MAC address.

Conceptually:

```text
Source MAC
    ↓
Arrived on Port 3
    ↓
MAC table learns
MAC → Port 3
```

---

# Forwarding

If the destination MAC is known:

```text
Frame
  ↓
MAC table lookup
  ↓
Correct switch port
```

The switch does not need to send that known unicast frame everywhere.

---

# Flooding

If a destination MAC is unknown, the switch may flood the frame out appropriate ports in the same VLAN except the port where it arrived.

Broadcast traffic is also flooded within the broadcast domain/VLAN.

---

# Collision Domains

Each normal switch port creates its own collision domain.

This is different from old Ethernet hubs, where devices shared a collision domain.

---

# Broadcast Domains

By default, a basic Layer 2 switch does not separate broadcast domains.

VLANs can create separate Layer 2 broadcast domains.

You will configure VLANs in Lesson 22.

---

# Switching Loops

Redundant physical links can accidentally create Layer 2 loops.

Potential effects include:

```text
Broadcast storms
Duplicate frames
MAC table instability
Severe network outage
```

---

# Spanning Tree Protocol

**STP** helps prevent Layer 2 loops while allowing physical redundancy.

At a high level:

```text
Redundant links
      ↓
STP calculates topology
      ↓
Some paths forward
Some redundant paths block/discard
```

If the active path fails, STP can reconverge.

---

# Useful Cisco Commands

```text
show mac address-table
show interfaces status
show interfaces
show spanning-tree
```

Exact output varies by switch and Packet Tracer version.

---

# Troubleshooting Switching

Check:

```text
Cable/link
Switch port state
Correct port
MAC learned?
Correct VLAN?
Errors?
STP state?
Duplicate/loop condition?
```

---

# Key Terms

```text
Switch
MAC Table
Learning
Forwarding
Flooding
Filtering
Collision Domain
Broadcast Domain
Loop
STP
```

---

# Knowledge Check

1. What information does a switch learn from the source MAC?
2. What happens to an unknown unicast frame?
3. Does a basic switch automatically separate broadcast domains?
4. What problem does STP help prevent?
5. Why are switching loops dangerous?

---

# Hands-On Lab

➡️ **[Lab 21 — Switching Fundamentals](../labs/lab-21-switching-fundamentals.md)**
