# Lesson 24 — Routing and Switching Troubleshooting

## Learning Objectives

By the end of this lesson, you will be able to:

- Troubleshoot Layer 2 and Layer 3 problems systematically.
- Distinguish switching, VLAN, trunk, gateway, and routing failures.
- Use Cisco show commands to gather evidence.
- Use ping and traceroute without relying on them alone.
- Identify the scope of a network outage.
- Work from lower layers toward higher layers.
- Document root cause and verification.

---

# Start with Scope

Ask:

```text
One host?
One VLAN?
One switch?
One subnet?
Multiple networks?
Entire site?
```

Scope often points toward the affected component.

---

# Layered Troubleshooting

A useful flow:

```text
Layer 1
Cable / link / interface
        ↓
Layer 2
MAC / VLAN / trunk / STP
        ↓
Layer 3
IP / mask / gateway / route
        ↓
Layer 4+
Ports / services / applications
```

---

# Layer 2 Evidence

Useful commands:

```text
show interfaces status
show mac address-table
show vlan brief
show interfaces trunk
show spanning-tree
```

Questions:

```text
Is the port up?
Is the MAC learned?
Is the port in the correct VLAN?
Is the trunk carrying the VLAN?
Is STP affecting the path?
```

---

# Layer 3 Evidence

Useful commands:

```text
show ip interface brief
show ip route
```

Endpoint tools:

```text
ipconfig /all
ping
tracert
arp -a
```

Questions:

```text
Correct IP?
Correct prefix?
Correct gateway?
Router interface up?
Route exists?
Return route exists?
```

---

# Common Failure Patterns

## Local Host Only

Investigate:

```text
Endpoint
Cable
Access port
IP configuration
```

## Entire VLAN

Investigate:

```text
VLAN configuration
Trunk
Gateway/SVI/subinterface
Routing
```

## One Switch

Investigate:

```text
Switch uplink
Trunk
STP
Power/device state
```

## Local Works, Remote Fails

Investigate:

```text
Gateway
Routing
Layer 3 interface
Return path
```

---

# Change One Thing at a Time

Avoid making five changes at once.

Use:

```text
Observe
   ↓
Form hypothesis
   ↓
Test
   ↓
Change one item
   ↓
Verify
```

---

# Establish a Baseline

Know what normal looks like.

Document:

```text
VLANs
Trunks
Gateways
Subnets
Routes
Expected interface states
```

Troubleshooting becomes much easier when you can compare current state with a known-good design.

---

# Key Terms

```text
Scope
Baseline
Root Cause
Layer 2
Layer 3
Trunk
VLAN
Gateway
Route
Return Path
Verification
```

---

# Knowledge Check

1. What should you determine before changing configuration?
2. Which command helps show VLAN membership?
3. Which command shows the routing table?
4. If same-VLAN traffic works but remote VLANs fail, which layer should receive attention?
5. Why should you change one thing at a time?
6. What is a baseline?

---

# Hands-On Lab

➡️ **[Lab 24 — Routing and Switching Troubleshooting](../labs/lab-24-routing-and-switching-troubleshooting.md)**
