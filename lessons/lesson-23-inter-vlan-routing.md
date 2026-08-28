# Lesson 23 — Inter-VLAN Routing

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain why VLANs require Layer 3 routing to communicate.
- Explain router-on-a-stick.
- Recognize router subinterfaces and 802.1Q encapsulation.
- Explain switched virtual interfaces at a beginner level.
- Assign default gateways to VLANs.
- Configure basic inter-VLAN routing in Packet Tracer.
- Troubleshoot common inter-VLAN routing failures.

---

# Why Inter-VLAN Routing?

VLANs create separate Layer 2 broadcast domains.

Example:

```text
VLAN 10 → 192.168.10.0/24
VLAN 20 → 192.168.20.0/24
```

A Layer 3 device is needed for communication between them.

---

# Router-on-a-Stick

One physical router interface can use multiple logical subinterfaces.

```text
VLAN 10 ─┐
VLAN 20 ─┼─ Switch ═ trunk ═ Router
VLAN 30 ─┘
```

The router link is an 802.1Q trunk.

---

# Router Subinterfaces

Conceptual Cisco configuration:

```text
interface g0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
```

Then:

```text
interface g0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
```

The physical interface must also be enabled.

---

# VLAN Gateways

Endpoints use the Layer 3 address for their VLAN as the default gateway.

Example:

```text
VLAN 10 host
192.168.10.25/24
Gateway 192.168.10.1
```

---

# Layer 3 Switches

A multilayer/Layer 3 switch can perform routing using **Switch Virtual Interfaces (SVIs)**.

Conceptually:

```text
interface vlan 10
 ip address 192.168.10.1 255.255.255.0
```

Layer 3 switching is common in enterprise networks.

---

# Router-on-a-Stick vs. Layer 3 Switching

```text
Router-on-a-stick
- Router performs routing
- Trunk connects switch to router
- Useful for learning/smaller designs

Layer 3 switch
- Switch performs routing
- Uses SVIs
- Common in larger enterprise LANs
```

---

# Troubleshooting

Check:

```text
Correct endpoint VLAN?
Correct endpoint IP?
Correct gateway?
VLAN exists?
Trunk working?
Correct VLAN tags?
Router subinterface up?
Correct encapsulation?
Routing enabled where required?
```

---

# Useful Commands

Switch:

```text
show vlan brief
show interfaces trunk
```

Router:

```text
show ip interface brief
show ip route
```

---

# Knowledge Check

1. Why is routing required between VLANs?
2. What is router-on-a-stick?
3. What is a router subinterface?
4. What should a VLAN host use as its gateway?
5. What is an SVI?
6. What role does the trunk play?

---

# Hands-On Lab

➡️ **[Lab 23 — Inter-VLAN Routing](../labs/lab-23-inter-vlan-routing.md)**
