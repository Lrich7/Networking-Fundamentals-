# Project 05 — Build a Segmented Business Network

## Project Overview

You have completed Section 5 — **Routing & Switching**.

Your task is to design, build, test, and troubleshoot a segmented business network.

This project combines:

```text
Switching
VLANs
Trunks
Inter-VLAN routing
Static/default routing
STP concepts
Troubleshooting
Documentation
```

The project is intentionally less guided than the labs.

---

# Scenario

A company has four departments:

```text
Administration
Operations
IT
Servers
```

Management wants each department separated into its own VLAN and IP subnet.

The company also has an upstream router representing another site or service-provider connection.

---

# Requirements

Create:

```text
VLAN 10 — ADMIN
VLAN 20 — OPERATIONS
VLAN 30 — IT
VLAN 40 — SERVERS
```

Use:

```text
192.168.10.0/24
192.168.20.0/24
192.168.30.0/24
192.168.40.0/24
```

Use at least:

```text
2 switches
1 internal router or Layer 3 routing device
1 upstream router
2 endpoints per user VLAN
1–2 servers
```

---

# Part 1 — Draw the Design

Before configuring devices, create a topology showing:

```text
Endpoints
Switches
Access ports
Trunks
VLANs
Router
Upstream router
Server network
```

---

# Part 2 — Create the VLAN Plan

Document:

```text
VLAN ID
VLAN name
IPv4 subnet
Default gateway
Purpose
```

---

# Part 3 — Configure Access Ports

Assign endpoint ports to the correct VLAN.

Verify:

```text
show vlan brief
```

---

# Part 4 — Configure Trunks

Configure required switch-to-switch and switch-to-router trunks.

Verify:

```text
show interfaces trunk
```

---

# Part 5 — Configure Inter-VLAN Routing

Use router-on-a-stick or a suitable Layer 3 switching method.

Gateways:

```text
VLAN 10 → 192.168.10.1
VLAN 20 → 192.168.20.1
VLAN 30 → 192.168.30.1
VLAN 40 → 192.168.40.1
```

---

# Part 6 — Configure Endpoints

Assign valid addresses and gateways.

Verify same-VLAN communication before testing between VLANs.

---

# Part 7 — Test Inter-VLAN Communication

Verify:

```text
ADMIN → OPERATIONS
ADMIN → SERVERS
OPERATIONS → SERVERS
IT → all internal VLANs
```

At this stage, the project is testing connectivity, not advanced security policy.

---

# Part 8 — Add the Upstream Router

Create a transit network between the internal and upstream router.

Use documentation/private lab addressing.

Configure routing so internal VLANs can reach a test network behind the upstream router.

---

# Part 9 — Routing Table Review

Inspect:

```text
show ip route
```

Document:

```text
Connected routes
Static routes
Default route if used
Next hops
```

---

# Part 10 — Switching Review

Inspect:

```text
show mac address-table
show vlan brief
show interfaces trunk
show spanning-tree
```

Explain what each command tells you about the network.

---

# Part 11 — Redundancy Concept

If appropriate, create a redundant switch path.

Observe STP.

Document:

```text
Root bridge
Forwarding path
Blocked/discarding path
```

Do not disable STP to force all paths active.

---

# Part 12 — Failure 1: Access VLAN

Place one ADMIN endpoint in VLAN 20.

Diagnose it using evidence.

Record:

```text
Symptom
Scope
Command
Root cause
Fix
Verification
```

---

# Part 13 — Failure 2: Trunk

Break a trunk configuration.

Determine whether:

```text
One VLAN
Several VLANs
One switch
All switches
```

are affected.

Repair it.

---

# Part 14 — Failure 3: Gateway

Give an Operations PC the wrong gateway.

Compare local and remote communication.

Repair and document.

---

# Part 15 — Failure 4: Inter-VLAN Routing

Break one router subinterface or SVI.

Use show commands to locate the failure.

Repair it.

---

# Part 16 — Failure 5: Static/Default Route

Remove or misconfigure the route toward the upstream test network.

Verify internal VLAN communication still works while upstream communication fails.

Explain why the scope points toward routing.

---

# Part 17 — Failure 6: Physical Link

Disconnect one uplink.

Determine whether redundancy keeps the network operational.

If no redundant path exists, identify the affected scope.

---

# Part 18 — Troubleshooting Matrix

Create a table or structured section for:

```text
One PC fails
One VLAN fails
One switch fails
Same VLAN works / remote VLAN fails
Internal works / upstream fails
Multiple VLANs across trunk fail
```

For each include:

```text
Likely area
First command/check
Second command/check
```

---

# Part 19 — Final Documentation

Produce:

```text
Topology
VLAN table
Subnet table
Gateway table
Trunk links
Routing design
Upstream route
STP notes
Testing results
Troubleshooting matrix
```

Another technician should be able to understand the design from your documentation.

---

# Part 20 — Save

Save:

```text
project-05-build-a-segmented-business-network.pkt
```

Recommended location:

```text
packet-tracer/projects/
```

---

# Final Validation

- [ ] Topology designed
- [ ] Four VLANs created
- [ ] Access ports assigned
- [ ] Trunks configured
- [ ] Inter-VLAN routing configured
- [ ] Endpoints addressed
- [ ] Same-VLAN traffic tested
- [ ] Inter-VLAN traffic tested
- [ ] Upstream router added
- [ ] Upstream routing tested
- [ ] Routing table documented
- [ ] MAC/VLAN/trunk state inspected
- [ ] STP reviewed
- [ ] Access VLAN fault repaired
- [ ] Trunk fault repaired
- [ ] Gateway fault repaired
- [ ] Inter-VLAN routing fault repaired
- [ ] Route fault repaired
- [ ] Physical-link scenario tested
- [ ] Troubleshooting matrix completed
- [ ] Final documentation completed
- [ ] Packet Tracer project saved

---

# Project Reflection

1. Why are VLANs useful in a business network?
2. Why does each VLAN normally use a different IP subnet?
3. What is the purpose of a trunk?
4. Why is Layer 3 routing required between VLANs?
5. What does STP protect the network from?
6. How can outage scope help distinguish a VLAN fault from a routing fault?
7. Which show commands were most useful?

---

# 🏆 Project Complete

You have completed **Project 05 — Build a Segmented Business Network**.

You have now applied:

```text
Ethernet switching
MAC learning
VLANs
802.1Q trunks
Inter-VLAN routing
Static/default routing
STP concepts
Layered troubleshooting
Network documentation
```

---

# ➡️ Continue Training

Next:

➡️ **[Lesson 25 — Network Security Fundamentals](../lessons/lesson-25-network-security-fundamentals.md)**
