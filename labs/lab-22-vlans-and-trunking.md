# Lab 22 — VLANs and Trunking

## Lab Objective

Create VLANs, assign access ports, configure an 802.1Q trunk, and troubleshoot VLAN connectivity in Cisco Packet Tracer.

---

# Part 1 — Build the Topology

Create:

```text
PC0 ─ Switch0 ═ Switch1 ─ PC2
PC1 ─┘                 └── PC3
```

The switch-to-switch link will become a trunk.

---

# Part 2 — Create VLANs

On both switches create:

```text
VLAN 10 — ADMIN
VLAN 20 — OPERATIONS
```

Verify:

```text
show vlan brief
```

---

# Part 3 — Assign Access Ports

Place:

```text
PC0 and PC2 → VLAN 10
PC1 and PC3 → VLAN 20
```

Use appropriate access-port commands.

---

# Part 4 — Address the PCs

Use:

```text
VLAN 10 → 192.168.10.0/24
VLAN 20 → 192.168.20.0/24
```

Assign valid host addresses.

No inter-VLAN routing is required yet.

---

# Part 5 — Configure the Trunk

Configure the switch-to-switch link as a trunk.

Verify:

```text
show interfaces trunk
```

---

# Part 6 — Test Same-VLAN Connectivity

Test:

```text
PC0 → PC2
PC1 → PC3
```

These should work when the VLANs and trunk are configured correctly.

---

# Part 7 — Test Different VLANs

Test:

```text
PC0 → PC1
```

Without inter-VLAN routing, explain the expected result.

---

# Part 8 — Break an Access Port

Move PC2's switch port into VLAN 20.

Test PC0 → PC2.

Use:

```text
show vlan brief
```

to identify the fault.

Repair it.

---

# Part 9 — Break the Trunk

Misconfigure or disable the trunk in the isolated lab.

Determine which communications fail.

Repair it and verify.

---

# Part 10 — Simulation Mode

Observe a broadcast generated in VLAN 10.

Does a VLAN 20 endpoint receive the same Layer 2 broadcast?

Explain what this demonstrates.

---

# Knowledge Check

1. What command displays VLAN membership?
2. What is carried over a trunk?
3. Why can two PCs in VLAN 10 communicate across two switches?
4. Why does VLAN 10 not automatically communicate with VLAN 20?
5. What happens if one end of a required trunk is misconfigured?

---

# Challenge

Create:

```text
VLAN 10 — ADMIN
VLAN 20 — OPERATIONS
VLAN 30 — IT
```

across two switches.

Place at least two endpoints in each VLAN.

Verify same-VLAN communication across the trunk and VLAN isolation.

Save:

```text
lab-22-vlans-and-trunking.pkt
```

---

# Lab Completion Checklist

- [ ] Created VLANs
- [ ] Assigned access ports
- [ ] Configured IP subnets
- [ ] Configured trunk
- [ ] Verified same-VLAN traffic
- [ ] Verified VLAN isolation
- [ ] Diagnosed access VLAN fault
- [ ] Diagnosed trunk fault
- [ ] Observed broadcast isolation
- [ ] Completed knowledge check
- [ ] Completed challenge

---

# Lab Complete

You have completed **Lab 22 — VLANs and Trunking**.

# Next Lesson

➡️ **[Lesson 23 — Inter-VLAN Routing](../lessons/lesson-23-inter-vlan-routing.md)**
