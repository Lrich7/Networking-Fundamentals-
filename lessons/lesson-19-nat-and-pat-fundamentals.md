# Lesson 19 — NAT and PAT Fundamentals

## Learning Objectives

By the end of this lesson, you will be able to:

- Explain why NAT is commonly used in IPv4 networks.
- Distinguish private and public IPv4 addressing.
- Explain static NAT, dynamic NAT, and PAT at a beginner level.
- Explain inside/local and translated address concepts.
- Describe how PAT allows many internal hosts to share a public IPv4 address.
- Recognize basic port-forwarding concepts.
- Identify common NAT troubleshooting symptoms.
- Observe NAT behavior in Packet Tracer.

---

# Why NAT?

Private IPv4 networks commonly use:

```text
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

These addresses are not normally routed across the public Internet.

A router/firewall can translate addresses between private and public address spaces using **Network Address Translation (NAT)**.

---

# Basic NAT Example

```text
PC
192.168.1.50
      ↓
Router / Firewall
      ↓
Public IPv4
203.0.113.10
      ↓
Internet
```

`203.0.113.0/24` is documentation space and is appropriate for training examples.

---

# Static NAT

Static NAT creates a consistent one-to-one translation.

Conceptually:

```text
192.168.1.10 ↔ 203.0.113.20
```

It may be used when a predictable translation is required.

---

# Dynamic NAT

Dynamic NAT selects addresses from a configured public/global pool.

The translation may vary depending on availability and configuration.

---

# PAT

**Port Address Translation (PAT)** allows multiple internal devices to share one translated IPv4 address by tracking transport-layer port information.

Example:

```text
192.168.1.10:51000 ─┐
192.168.1.20:52000 ─┼→ 203.0.113.10
192.168.1.30:53000 ─┘
```

PAT is extremely common in small networks.

You may also hear:

```text
NAT overload
```

---

# NAT and Ports

PAT demonstrates why transport-layer ports matter.

The device can track conversations using information such as:

```text
Protocol
Inside address
Inside port
Translated address
Translated port
Destination
```

---

# Port Forwarding

Inbound access to an internal service may use a configured translation/forwarding rule.

Conceptually:

```text
Public 203.0.113.10:443
          ↓
Internal 192.168.1.20:443
```

Publishing services creates security exposure and must be controlled carefully.

Do not configure real production port forwarding as part of this training.

---

# NAT Does Not Equal Firewall

NAT and firewalling are different concepts.

A security device may perform both, but:

```text
NAT        → Address/port translation
Firewall   → Traffic policy/control
```

Do not rely on NAT alone as a complete security strategy.

---

# NAT Troubleshooting

If internal clients cannot reach an external network, check:

```text
Local IP configuration
Gateway
Routing
NAT rule
Inside/outside interface roles
Translation table
Firewall policy
Upstream connectivity
DNS separately
```

---

# NAT and IPv6

IPv6 was designed with a vast address space and does not depend on IPv4-style NAT for address conservation.

IPv6 security still requires appropriate firewalling and network policy.

---

# Documentation Addresses

Use safe documentation ranges in public examples:

```text
192.0.2.0/24
198.51.100.0/24
203.0.113.0/24
```

Do not use someone else's real public address space for training diagrams.

---

# Key Terms

```text
NAT
PAT
NAT Overload
Static NAT
Dynamic NAT
Private IPv4
Public IPv4
Translation
Port Forwarding
Inside
Outside
```

---

# Knowledge Check

1. Why is NAT commonly used with private IPv4 networks?
2. What is static NAT?
3. What is PAT?
4. How can many clients share one public IPv4 address?
5. Is NAT the same thing as a firewall?
6. Why should public training examples use documentation ranges?

---

# Hands-On Lab

➡️ **[Lab 19 — NAT and PAT Fundamentals](../labs/lab-19-nat-and-pat-fundamentals.md)**
