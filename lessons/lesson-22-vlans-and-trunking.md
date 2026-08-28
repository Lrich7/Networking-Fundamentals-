# Lesson 22 — VLANs and Trunking

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain the purpose of VLANs.
- Explain how VLANs create separate broadcast domains.
- Distinguish access and trunk ports.
- Explain IEEE 802.1Q tagging at a beginner level.
- Recognize native VLAN concepts.
- Configure basic VLANs in Packet Tracer.
- Configure a trunk between switches.
- Troubleshoot common VLAN and trunk problems.

---

# What Is a VLAN?

A **Virtual LAN (VLAN)** logically separates a switched network.

Without VLANs:

```text
One switch
    ↓
One large Layer 2 broadcast domain
```

With VLANs:

```text
VLAN 10 → Administration
VLAN 20 → Operations
VLAN 30 → IT
```

Each VLAN represents a separate Layer 2 broadcast domain.

---

# VLAN IDs

Common normal-range VLAN IDs include:

```text
1–1005
```

VLAN IDs extend beyond that on modern 802.1Q networks, but platform support and reserved values vary.

For labs, use simple IDs such as:

```text
10
20
30
40
```

---

# Access Ports

An access port normally carries traffic for one assigned VLAN to an endpoint.

Example:

```text
PC
 ↓
Switch Port
 ↓
VLAN 10
```

---

# Trunk Ports

A trunk carries traffic for multiple VLANs between compatible network devices.

Example:

```text
Switch 1
   ║
802.1Q trunk
   ║
Switch 2
```

---

# 802.1Q

IEEE **802.1Q** provides VLAN tagging on Ethernet trunks.

The VLAN tag allows the receiving switch to determine which VLAN a frame belongs to.

---

# Native VLAN

On an 802.1Q trunk, the native VLAN is associated with untagged traffic.

Native VLAN mismatches can create connectivity and security problems.

For beginner labs, keep trunk configurations consistent.

---

# VLANs and IP Subnets

A common design uses a different IP subnet per VLAN.

Example:

```text
VLAN 10 → 192.168.10.0/24
VLAN 20 → 192.168.20.0/24
VLAN 30 → 192.168.30.0/24
```

Devices in different VLANs need Layer 3 routing to communicate.

---

# Basic Cisco Configuration Pattern

Create VLAN:

```text
vlan 10
 name ADMIN
```

Assign access port:

```text
interface fastethernet0/1
 switchport mode access
 switchport access vlan 10
```

Trunk:

```text
interface gigabitethernet0/1
 switchport mode trunk
```

Exact interface names vary.

---

# Useful Commands

```text
show vlan brief
show interfaces trunk
show interfaces switchport
show mac address-table
```

---

# VLAN Troubleshooting

Check:

```text
VLAN exists?
Correct access VLAN?
Correct trunk?
VLAN allowed across trunk?
Native VLAN consistent?
Correct IP subnet?
Routing available between VLANs?
```

---

# Key Terms

```text
VLAN
VLAN ID
Broadcast Domain
Access Port
Trunk Port
802.1Q
Tag
Native VLAN
Inter-VLAN Routing
```

---

# Knowledge Check

1. What does a VLAN separate?
2. What is an access port?
3. What is a trunk port?
4. What standard is commonly used for VLAN tagging?
5. Can devices in different VLANs communicate through Layer 2 switching alone?
6. Why should VLAN and IP subnet design align?

---

# Hands-On Lab

➡️ **[Lab 22 — VLANs and Trunking](../labs/lab-22-vlans-and-trunking.md)**
