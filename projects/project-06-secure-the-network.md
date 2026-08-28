# Project 06 — Secure the Network

## Project Overview

You have completed **Section 6 — Network Security**.

Your task is to take a fictional small-business network and create a practical security-hardening plan, implement safe controls in Packet Tracer where supported, test the result, and troubleshoot security-related failures.

This is a **defensive administration project**.

---

# Scenario

The company has:

```text
VLAN 10 — ADMIN
VLAN 20 — OPERATIONS
VLAN 30 — IT
VLAN 40 — SERVERS
VLAN 50 — GUEST
```

Management wants to reduce unnecessary access without breaking required business services.

---

# Requirements

Your design must address:

```text
Network segmentation
Firewall policy
ACL concepts
Secure remote access / VPN
Wireless security
Threat awareness
Device hardening
Logging and monitoring
Documentation
```

Use only fictional lab information.

---

# Part 1 — Identify Assets

Document what needs protection:

```text
User endpoints
Network devices
Servers
Administrative interfaces
Wireless network
Credentials
Configuration backups
Business data
```

Classify which assets require the strongest restrictions.

---

# Part 2 — Trust Boundaries

Draw the network and mark:

```text
Internal users
IT administrators
Servers
Guest wireless
Internet/untrusted network
Remote users
```

Explain why each boundary exists.

---

# Part 3 — Traffic Requirements

Create a least-privilege matrix.

For each source and destination, document:

```text
Required?
Protocol/port
Reason
Permit or deny
```

Examples may include:

```text
Users → DNS
Users → Web server
IT → Network management
Guest → Internet only
Guest → Internal servers denied
```

---

# Part 4 — ACL Implementation

In Packet Tracer, implement at least one ACL that enforces a meaningful business requirement.

Example goal:

```text
Guest network
    ↓
Cannot access internal server VLAN
```

Verify the rule using supported show commands and connectivity tests.

Do not use ACLs to experiment on a real company network.

---

# Part 5 — Firewall Design

Create a firewall policy diagram covering:

```text
Inbound Internet traffic
Outbound user traffic
Server traffic
Administrative traffic
Guest traffic
```

For every allowed inbound service, document the business reason.

---

# Part 6 — VPN Design

Design:

```text
Remote IT administrator
        ↓
Encrypted VPN
        ↓
Corporate network
        ↓
Authorized management resources
```

Document:

```text
Authentication
MFA recommendation
Authorized users
Permitted destinations
Logging
Full vs. split tunnel decision
```

Configuration is optional if your simulator does not support the desired VPN features.

---

# Part 7 — Wireless Security

Design separate:

```text
Corporate Wi-Fi
Guest Wi-Fi
```

Document:

```text
WPA2/WPA3 choice
Authentication method
Guest isolation
Credential handling
Management access
Firmware/update requirements
```

---

# Part 8 — Switch Hardening

In the Packet Tracer lab:

- Identify unused switch ports.
- Administratively disable unused ports where appropriate.
- Document why unused interfaces should not remain casually available.
- Keep required trunk/access ports operational.

Verify the business network still works.

---

# Part 9 — Management-Plane Hardening

Create recommendations for:

```text
SSH instead of Telnet
HTTPS instead of HTTP where supported
Strong unique administrative credentials
MFA where available
Restricted management source networks
Least-privilege administrator access
Configuration backups
Logging
Time synchronization
Patching/firmware
```

---

# Part 10 — Threat Review

For each threat, document one or more defenses:

```text
Phishing
Malware/ransomware
Rogue wireless
Password attack
DoS/DDoS
Spoofing
Unauthorized device
Misconfiguration
```

Focus on prevention, detection, containment, and recovery.

---

# Part 11 — Monitoring Plan

Document what should be monitored:

```text
Authentication failures
Firewall denies
VPN logins
Configuration changes
Device availability
Interface errors
Unusual traffic
Wireless events
Critical system logs
```

Explain who should review alerts.

---

# Part 12 — Failure Ticket 1

Create a safe lab fault where an ACL blocks legitimate business traffic.

Troubleshoot without simply deleting all security controls.

Record:

```text
Scope
Evidence
Root cause
Minimal correction
Verification
```

---

# Part 13 — Failure Ticket 2

Create a segmentation/VLAN-related fault that appears to be a security problem.

Prove whether the root cause is:

```text
Layer 2
Layer 3
or
Security policy
```

---

# Part 14 — Failure Ticket 3

Scenario:

> A remote employee reports that the VPN connects, but an authorized internal resource is unreachable.

Create a troubleshooting plan covering:

```text
Authentication
VPN status
Assigned addressing
Routes
DNS
Authorization
Firewall/ACL
Target service
```

---

# Part 15 — Incident Response Exercise

Use this fictional event:

> Multiple failed administrator logins are followed by a successful login from an unexpected source.

Document defensive actions:

```text
Validate alert
Preserve evidence/logs
Confirm account activity
Contain if necessary
Reset/revoke credentials according to policy
Review MFA
Determine scope
Escalate
Document
Monitor
```

Do not attempt retaliation or unauthorized access.

---

# Part 16 — Final Security Baseline

Produce a checklist for future technicians covering:

```text
VLANs
ACLs
Firewall rules
VPN
Wireless
Unused ports
Management protocols
Updates
Backups
Logging
Monitoring
Documentation
```

---

# Part 17 — Final Validation

- [ ] Assets identified
- [ ] Trust boundaries documented
- [ ] Traffic requirements documented
- [ ] Least-privilege matrix created
- [ ] ACL implemented in lab
- [ ] Allowed traffic verified
- [ ] Denied traffic verified
- [ ] Firewall policy designed
- [ ] VPN design completed
- [ ] Wireless security plan completed
- [ ] Switch hardening completed
- [ ] Management-plane recommendations completed
- [ ] Threat review completed
- [ ] Monitoring plan completed
- [ ] Three troubleshooting scenarios completed
- [ ] Incident response exercise completed
- [ ] Security baseline documented

---

# Project Reflection

1. Why is segmentation useful even when a firewall exists?
2. Why should a security rule have a documented business reason?
3. What is the danger of an overly broad allow rule?
4. Why should guest wireless be separated from internal resources?
5. Why is MFA valuable for remote administrative access?
6. Why should troubleshooting verify Layers 1–3 before blaming a firewall?
7. How does logging improve both security and troubleshooting?

---

# 🏆 Project Complete

You have completed **Project 06 — Secure the Network**.

You have now applied:

```text
Defense in depth
Least privilege
Segmentation
Firewall concepts
ACLs
VPN concepts
Wireless security
Threat recognition
Network hardening
Monitoring
Incident response
Security troubleshooting
```

---

# ➡️ Continue Training

Next:

➡️ **[Lesson 32 — Network Troubleshooting Methodology](../lessons/lesson-32-network-troubleshooting-methodology.md)**
