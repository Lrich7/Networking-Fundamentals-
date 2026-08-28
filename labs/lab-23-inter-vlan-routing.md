# Lab 23 — Inter-VLAN Routing

## Lab Objective

Extend the VLAN lab by configuring router-on-a-stick, testing inter-VLAN communication, and troubleshooting common failures.

---

# Part 1 — Build the Network

Use:

```text
VLAN 10 PCs ─┐
VLAN 20 PCs ─┼─ Switch ═ trunk ═ Router
VLAN 30 PCs ─┘
```

Networks:

```text
VLAN 10 → 192.168.10.0/24
VLAN 20 → 192.168.20.0/24
VLAN 30 → 192.168.30.0/24
```

---

# Part 2 — Create VLANs

Create:

```text
10 ADMIN
20 OPERATIONS
30 IT
```

Assign endpoint access ports.

---

# Part 3 — Configure the Router Trunk

Configure the switch port toward the router as a trunk.

Verify:

```text
show interfaces trunk
```

---

# Part 4 — Configure Subinterfaces

Configure router subinterfaces using:

```text
VLAN 10 → 192.168.10.1
VLAN 20 → 192.168.20.1
VLAN 30 → 192.168.30.1
```

Use the appropriate `encapsulation dot1Q` commands.

---

# Part 5 — Configure Gateways

Set endpoints to use the gateway for their VLAN.

Verify local communication first.

---

# Part 6 — Test Inter-VLAN Routing

Test:

```text
VLAN 10 → VLAN 20
VLAN 10 → VLAN 30
VLAN 20 → VLAN 30
```

Record pass/fail.

---

# Part 7 — Inspect Routes

On the router:

```text
show ip route
```

Identify the three connected VLAN networks.

---

# Part 8 — Break a Gateway

Give one VLAN 20 PC the VLAN 10 gateway.

Test:

```text
Same-VLAN communication
Different-VLAN communication
```

Repair it.

---

# Part 9 — Break a Subinterface

Misconfigure the VLAN ID on one router subinterface.

Use:

```text
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
```

to isolate the problem.

---

# Part 10 — Troubleshooting Ticket

> "All ADMIN users can reach each other, but none can reach the server in another VLAN."

Create a logical troubleshooting sequence.

---

# Knowledge Check

1. What does `encapsulation dot1Q 20` identify?
2. Why does same-VLAN traffic not need the router?
3. Why does different-VLAN traffic need a gateway?
4. Which commands help verify the trunk and router interfaces?
5. What happens if the router subinterface uses the wrong VLAN ID?

---

# Challenge

Build four VLANs:

```text
10 ADMIN
20 OPERATIONS
30 IT
40 SERVERS
```

Configure router-on-a-stick and verify full inter-VLAN routing.

Then create three faults and troubleshoot them.

Save:

```text
lab-23-inter-vlan-routing.pkt
```

---

# Lab Completion Checklist

- [ ] Created three VLANs
- [ ] Assigned access ports
- [ ] Configured router trunk
- [ ] Configured subinterfaces
- [ ] Configured gateways
- [ ] Tested inter-VLAN routing
- [ ] Inspected routes
- [ ] Diagnosed wrong gateway
- [ ] Diagnosed subinterface fault
- [ ] Completed troubleshooting ticket
- [ ] Completed knowledge check
- [ ] Completed challenge

---

# Lab Complete

You have completed **Lab 23 — Inter-VLAN Routing**.

# Next Lesson

➡️ **[Lesson 24 — Routing and Switching Troubleshooting](../lessons/lesson-24-routing-and-switching-troubleshooting.md)**
