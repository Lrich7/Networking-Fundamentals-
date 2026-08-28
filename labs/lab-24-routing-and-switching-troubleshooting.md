# Lab 24 — Routing and Switching Troubleshooting

## Lab Objective

Troubleshoot a multi-VLAN routed Packet Tracer network using evidence, Cisco show commands, and a reusable ticket workflow.

---

# Part 1 — Build a Known-Good Baseline

Build:

```text
VLAN 10 ─┐
VLAN 20 ─┼─ Switch0 ═ Switch1
VLAN 30 ─┘       ║
                 Router
```

Use:

```text
VLAN 10 → 192.168.10.0/24
VLAN 20 → 192.168.20.0/24
VLAN 30 → 192.168.30.0/24
```

Configure working inter-VLAN routing.

Save:

```text
lab-24-working-baseline.pkt
```

---

# Part 2 — Baseline Documentation

Record:

```text
VLANs
Access ports
Trunks
Gateways
Router subinterfaces
Expected routes
```

---

# Part 3 — Ticket 1: Wrong Access VLAN

Move one endpoint port into the wrong VLAN.

Do not fix it immediately.

Use evidence to identify the cause.

---

# Part 4 — Ticket 2: Broken Trunk

Create a trunk problem.

Determine:

```text
Which VLANs fail?
Which switch is affected?
Does local same-switch traffic still work?
```

Repair and verify.

---

# Part 5 — Ticket 3: Wrong Gateway

Give one host the wrong gateway.

Compare:

```text
Same VLAN
Different VLAN
```

Document the pattern.

---

# Part 6 — Ticket 4: Router Subinterface

Break one router subinterface.

Use:

```text
show ip interface brief
show ip route
show interfaces trunk
```

to isolate the fault.

---

# Part 7 — Ticket 5: Physical Failure

Disconnect an uplink or endpoint cable.

Start troubleshooting at Layer 1.

Document why higher-layer configuration changes would not fix the problem.

---

# Part 8 — Ticket 6: STP/Redundancy

If your topology contains redundant links, inspect:

```text
show spanning-tree
```

Identify expected blocked/discarding and forwarding paths.

Do not disable STP simply to make every link forward.

---

# Part 9 — Timed Troubleshooting

Restore the baseline.

Create three faults.

Give yourself 15–20 minutes to:

```text
Identify scope
Collect evidence
State hypothesis
Find root cause
Repair
Verify
Document
```

---

# Part 10 — Ticket Template

Use:

```text
Ticket:
Affected users/devices:
Scope:
Layer suspected:
Evidence:
Commands used:
Root cause:
Change made:
Verification:
Prevention/documentation:
```

---

# Knowledge Check

1. What does `show vlan brief` tell you?
2. What does `show interfaces trunk` tell you?
3. What does `show ip route` tell you?
4. Why can a wrong gateway allow local but not remote traffic?
5. Why is a known-good baseline valuable?

---

# Challenge

Have another person—or your future self—create five hidden faults in the lab.

Possible faults:

```text
Wrong access VLAN
Broken trunk
Wrong IP
Wrong gateway
Wrong router subinterface VLAN
Shutdown interface
Missing route
Disconnected cable
```

Diagnose each without random configuration changes.

Save the repaired version:

```text
lab-24-routing-switching-challenge.pkt
```

---

# Lab Completion Checklist

- [ ] Built known-good baseline
- [ ] Documented baseline
- [ ] Diagnosed wrong access VLAN
- [ ] Diagnosed trunk fault
- [ ] Diagnosed gateway fault
- [ ] Diagnosed router subinterface fault
- [ ] Diagnosed physical failure
- [ ] Inspected STP
- [ ] Completed timed troubleshooting
- [ ] Used ticket template
- [ ] Completed knowledge check
- [ ] Completed challenge

---

# Lab Complete

You have completed **Lab 24 — Routing and Switching Troubleshooting** and **Section 5 — Routing & Switching**.

You now have hands-on experience with:

```text
Routing tables
Static routes
Default routes
Switch MAC learning
STP
VLANs
802.1Q trunks
Inter-VLAN routing
Router-on-a-stick
Layer 2 troubleshooting
Layer 3 troubleshooting
```

Now apply those skills in Project 05.

---

# 🛠️ Project 05 — Build a Segmented Business Network

➡️ **[Project 05 — Build a Segmented Business Network](../projects/project-05-build-a-segmented-business-network.md)**

In this project, you will design and troubleshoot a multi-department network using VLANs, trunks, routing, redundancy concepts, and structured documentation.

➡️ **[Begin Project 05 — Build a Segmented Business Network](../projects/project-05-build-a-segmented-business-network.md)**
