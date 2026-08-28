# Lab 21 — Switching Fundamentals

## Lab Objective

Observe MAC learning, frame forwarding, broadcast behavior, and basic Spanning Tree operation in Cisco Packet Tracer.

---

# Part 1 — Build a Switched LAN

Create:

```text
PC0 ─┐
PC1 ─┼─ Switch
PC2 ─┤
PC3 ─┘
```

Use:

```text
192.168.210.0/24
```

Assign valid addresses.

---

# Part 2 — Inspect the MAC Table

Before generating traffic:

```text
show mac address-table
```

Then ping among the PCs.

Run the command again.

Document at least four learned entries.

---

# Part 3 — Simulation Mode

Use Simulation Mode to observe:

```text
ARP broadcast
Unknown unicast behavior
Known unicast behavior
```

Explain how the switch's behavior changes after learning MAC addresses.

---

# Part 4 — Move a Device

Move PC3 to another switch port.

Generate traffic.

Inspect:

```text
show mac address-table
```

What changed?

---

# Part 5 — Interface Status

Run:

```text
show interfaces status
```

Identify:

```text
Connected ports
Unused ports
Port identifiers
```

---

# Part 6 — Add a Second Switch

Create:

```text
PCs ─ Switch0 ─ Switch1 ─ PCs
```

Generate traffic across the inter-switch link.

Inspect the MAC table on both switches.

---

# Part 7 — Broadcast Domain

Send/observe an ARP request.

Which connected Layer 2 devices receive the broadcast?

Explain why.

---

# Part 8 — STP

Create redundant links between two or three switches in the isolated Packet Tracer lab.

Inspect:

```text
show spanning-tree
```

Identify whether STP prevents every redundant link from forwarding simultaneously.

Do not reproduce switching loops on a production network.

---

# Part 9 — Troubleshooting Ticket

> "A workstation has link but cannot communicate with another PC on the same subnet."

Create a checklist covering:

```text
Endpoint configuration
Cable
Switch port
MAC table
VLAN
STP/interface state
```

---

# Knowledge Check

1. How does a switch learn MAC addresses?
2. What is flooding?
3. What does `show mac address-table` reveal?
4. What does STP protect against?
5. Why can redundant links be both useful and dangerous?

---

# Challenge

Build three interconnected switches with redundant links and several PCs.

Observe STP and document:

```text
Root bridge
Forwarding ports
Blocked/discarding redundant path
```

Then disconnect an active link and observe reconvergence.

Save:

```text
lab-21-switching-fundamentals.pkt
```

---

# Lab Completion Checklist

- [ ] Built switched LAN
- [ ] Inspected MAC table
- [ ] Observed learning/flooding
- [ ] Moved a device
- [ ] Inspected interface status
- [ ] Added second switch
- [ ] Observed broadcasts
- [ ] Inspected STP
- [ ] Completed troubleshooting ticket
- [ ] Completed knowledge check
- [ ] Completed challenge

---

# Lab Complete

You have completed **Lab 21 — Switching Fundamentals**.

# Next Lesson

➡️ **[Lesson 22 — VLANs and Trunking](../lessons/lesson-22-vlans-and-trunking.md)**
