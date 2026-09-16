# ✅ Networking Fundamentals — Practice Exam 2 Answer Key

**Lessons Covered:** 11–20  
**Questions:** 40

Use this answer key **after completing Practice Exam 2**.

Each answer includes an explanation so the answer key can also be used as a review guide.

---

# 📊 Scoring

Give yourself:

```text
1 point
```

for every correct answer.

Maximum score:

```text
40
```

Suggested study targets:

| Score | Percentage | Recommendation |
|---:|---:|---|
| 36–40 | 90–100% | Excellent |
| 32–35 | 80–87.5% | Strong |
| 28–31 | 70–77.5% | Review weak areas |
| 0–27 | Below 70% | Review Lessons 11–20 |

> These are course study targets and not official CompTIA passing-score equivalents.

---

# 1. A — 2.4 GHz

The 2.4 GHz band generally provides:

```text
Longer range

Better obstacle penetration

More potential interference
```

compared with higher-frequency Wi-Fi bands.

---

# 2. B — 1, 6, 11

For traditional 20 MHz channel planning in the 2.4 GHz band in the United States, remember:

```text
1
6
11
```

These are commonly used to minimize channel overlap.

---

# 3. B — Channel interference

Nearby access points using overlapping channels can interfere with each other and reduce wireless performance.

Possible symptoms include:

```text
Slow throughput

High retransmissions

Unstable connections

Poor application performance
```

---

# 4. D — WPA3

Of the listed choices:

```text
WEP
WPA
WPA2
WPA3
```

WPA3 is the newest and generally strongest security standard.

WEP should be considered obsolete and insecure.

---

# 5. B — Signal strength is only one factor affecting wireless performance

Strong signal does not guarantee good performance.

Other factors include:

```text
Interference

Channel congestion

Client capability

Access point load

Backhaul performance

Packet loss

Network congestion
```

---

# 6. A — Access point

A wireless access point connects wireless clients to a network.

Think:

```text
Wireless Client
      ↓
Access Point
      ↓
Ethernet Network
```

---

# 7. B — Securely connect two networks across another network

A site-to-site VPN commonly connects:

```text
Office A
   ↓
Internet
   ↓
Office B
```

Think:

> **Network ↔ Network**

---

# 8. B — Remote-access VPN

Remote-access VPNs are commonly used for:

```text
Remote employees

Laptops

Home workers

Traveling employees
```

Think:

> **Device/User ↔ Organization**

---

# 9. B — Some traffic uses the VPN while other traffic uses the local Internet connection

Split tunneling allows selected traffic to enter the VPN while other traffic uses the client's normal Internet connection.

Conceptually:

```text
Corporate Traffic
       ↓
      VPN

Internet Traffic
       ↓
Local Internet
```

Actual behavior depends on the organization's configuration and security policy.

---

# 10. B — Most or all client traffic is routed through the VPN according to policy

A full-tunnel configuration generally routes most or all client traffic through the organization's VPN infrastructure.

Think:

```text
Laptop
   ↓
 VPN
   ↓
Company Network
   ↓
Internet
```

---

# 11. B — Latency

Latency measures:

> **Delay**

It describes how long data takes to travel between points.

---

# 12. A — Jitter

Jitter means:

> **Variation in packet delay**

Example:

```text
Packet 1 → 20 ms

Packet 2 → 22 ms

Packet 3 → 80 ms

Packet 4 → 25 ms
```

Large variation can cause problems for real-time applications.

---

# 13. A — Jitter

Voice and video are sensitive to:

```text
Latency

Jitter

Packet loss
```

A connection can have plenty of bandwidth and still provide poor VoIP performance.

---

# 14. B — Throughput

Bandwidth describes theoretical or available capacity.

Throughput describes:

> **How much data is actually transferred.**

Think:

```text
Bandwidth
=
Capacity

Throughput
=
Actual transfer
```

---

# 15. C — QoS

QoS means:

> **Quality of Service**

It can be used to classify and prioritize traffic.

Common examples include:

```text
VoIP

Video conferencing

Business-critical applications
```

---

# 16. A — Firewall

Firewalls inspect and control traffic according to configured security rules.

They may evaluate information such as:

```text
Source

Destination

Protocol

Port

Connection state

Application
```

depending on firewall capabilities.

---

# 17. B — Access Control List

ACL stands for:

```text
Access Control List
```

ACLs are used to permit or deny traffic according to defined rules.

---

# 18. B — Block IP traffic from the first network to the second

The rule says:

```text
DENY
```

traffic from:

```text
192.168.50.0/24
```

to:

```text
192.168.20.0/24
```

Therefore the intended result is to block that traffic.

---

# 19. B — Give users only the access necessary to perform their responsibilities

Least privilege means:

> Give users, applications, and systems only the permissions required to perform their legitimate functions.

Avoid unnecessary administrative access.

---

# 20. A — Segmentation

Segmentation separates network resources.

Example:

```text
VLAN 10
Employees

VLAN 20
Servers

VLAN 30
Printers

VLAN 50
Guests

VLAN 99
Management
```

Security controls can then regulate communication between these segments.

---

# 21. A — Authentication, Authorization, Accounting

Memorize:

```text
AAA

Authentication
Authorization
Accounting
```

---

# 22. A — Authentication

Authentication answers:

> **Who are you?**

Examples include:

```text
Password

Certificate

Security key

Biometric
```

---

# 23. B — Authorization

Authorization answers:

> **What are you allowed to do?**

Example:

```text
User authenticated
      ↓
Authorization
      ↓
Read files
but
Cannot modify firewall
```

---

# 24. C — Accounting

Accounting answers:

> **What did you do?**

It can track:

```text
Login activity

Session information

Resource usage

Administrative actions
```

---

# 25. B — SSH

SSH provides encrypted remote command-line administration.

Think:

```text
Telnet
   ↓
Insecure plaintext-style remote access

SSH
   ↓
Encrypted remote access
```

---

# 26. C — SNMPv3

SNMPv3 provides stronger security capabilities than earlier SNMP versions, including authentication and privacy/encryption options.

For security-focused questions:

```text
SNMPv3
```

is usually the relevant version.

---

# 27. A — Network monitoring and management

SNMP is commonly used to collect and manage information about network devices.

Examples:

```text
Interface status

Bandwidth utilization

Errors

CPU utilization

Device health
```

---

# 28. B — Centralized event and log messages

Syslog allows devices to send event messages to a logging system.

Example:

```text
Switch
   ↓
Syslog
   ↓
Central Log Server
```

Useful messages might include:

```text
Interface down

Authentication failure

Configuration change

System warning
```

---

# 29. A — A performance baseline

A baseline tells you what:

> **Normal looks like.**

Example:

```text
Normal latency:
15 ms

Current latency:
80 ms
```

Without the baseline, determining whether `80 ms` is unusual is more difficult.

---

# 30. A — Detect performance, availability, and operational problems

Monitoring helps identify:

```text
Outages

High utilization

Packet loss

Interface errors

Latency

Device failures

Resource exhaustion
```

Monitoring does not eliminate the need for troubleshooting.

---

# 31. A — Redundancy

Having an additional resource available in case the primary resource fails is:

```text
Redundancy
```

Example:

```text
ISP 1
Primary

ISP 2
Backup
```

---

# 32. B — Failover

Failover is the process of moving service to a backup resource after the primary resource fails.

Think:

```text
Redundancy
=
Backup exists

Failover
=
Backup takes over
```

---

# 33. A — UPS

UPS stands for:

```text
Uninterruptible Power Supply
```

A UPS can provide temporary battery power when utility power fails.

It can help keep equipment such as:

```text
Routers

Switches

Firewalls

Servers

Wireless infrastructure
```

operating during short outages or while systems shut down safely.

---

# 34. A — Redundancy

Two power supplies provide redundancy.

If:

```text
Power Supply A
fails
```

then:

```text
Power Supply B
```

may allow the switch to continue operating, depending on the hardware design.

---

# 35. B — The scope and symptoms of the outage

Before making changes, determine:

```text
Who is affected?

What is affected?

When did it start?

What still works?

What does not work?
```

Scope is one of the most important troubleshooting clues.

---

# 36. B — Test the theory

After establishing a theory of probable cause:

> **Test it.**

Do not immediately make many unrelated changes.

Example:

```text
Theory:
Bad cable

Test:
Replace/test cable

Result:
Connectivity returns
```

Now you have evidence supporting the theory.

---

# 37. A — Verify full system functionality

A configuration change appearing to solve the problem is not enough.

Verify:

```text
Original issue resolved?

User functionality restored?

Other systems still working?

No new problems introduced?

Monitoring normal?
```

---

# 38. A — Document findings, actions, and outcomes

Documentation should capture information such as:

```text
Symptoms

Cause

Tests performed

Changes made

Solution

Verification

Lessons learned
```

This helps future troubleshooting and knowledge transfer.

---

# 39. B — Escalate the issue with the information already gathered

If the technician lacks the required:

```text
Permissions

Authority

Expertise

Access
```

the issue should be escalated appropriately.

A good escalation includes:

```text
Symptoms

Scope

Timeline

Tests performed

Results

Changes attempted

Suspected cause
```

---

# 40. A — Network path/WAN performance

The clues are:

```text
LAN
✓

DNS
✓

Internet Access
✓

Packet Loss
HIGH

Latency
HIGH
```

This points toward investigating:

```text
WAN

ISP

Network path

Congestion

Routing

Upstream connectivity
```

rather than DHCP or DNS.

---

# 📊 Quick Answer Key

| # | Answer | # | Answer |
|---:|:---:|---:|:---:|
| 1 | A | 21 | A |
| 2 | B | 22 | A |
| 3 | B | 23 | B |
| 4 | D | 24 | C |
| 5 | B | 25 | B |
| 6 | A | 26 | C |
| 7 | B | 27 | A |
| 8 | B | 28 | B |
| 9 | B | 29 | A |
| 10 | B | 30 | A |
| 11 | B | 31 | A |
| 12 | A | 32 | B |
| 13 | A | 33 | A |
| 14 | B | 34 | A |
| 15 | C | 35 | B |
| 16 | A | 36 | B |
| 17 | B | 37 | A |
| 18 | B | 38 | A |
| 19 | B | 39 | B |
| 20 | A | 40 | A |

---

# 🎯 Review by Topic

## 📡 Wireless

If you missed:

```text
1–6
```

Review:

```text
2.4 GHz

5 GHz

6 GHz

Channels

Interference

WPA2/WPA3

Access Points
```

---

## 🔐 VPN / Remote Connectivity

If you missed:

```text
7–10
```

Review:

```text
Site-to-Site VPN

Remote-Access VPN

Split Tunnel

Full Tunnel
```

---

## 📊 Network Performance

If you missed:

```text
11–15
```

Review:

```text
Bandwidth

Throughput

Latency

Jitter

Packet Loss

QoS
```

Remember:

```text
Bandwidth ≠ Throughput

Bandwidth ≠ Latency
```

---

## 🛡️ Network Security

If you missed:

```text
16–26
```

Review:

```text
Firewalls

ACLs

Segmentation

Least Privilege

AAA

SSH

SNMPv3
```

---

## 📈 Monitoring

If you missed:

```text
27–30
```

Review:

```text
SNMP

Syslog

Monitoring

Baselines
```

Remember:

```text
SNMP
=
Monitoring / Management
```

```text
Syslog
=
Event Logs
```

---

## 🔄 Redundancy

If you missed:

```text
31–34
```

Review:

```text
Redundancy

Failover

UPS

Backup Connections

Redundant Hardware
```

Remember:

```text
Redundancy
=
Backup exists
```

```text
Failover
=
Backup takes over
```

---

## 🧰 Troubleshooting

If you missed:

```text
35–40
```

Review the structured troubleshooting methodology.

Think:

```text
IDENTIFY PROBLEM
       ↓
ESTABLISH THEORY
       ↓
TEST THEORY
       ↓
PLAN / IMPLEMENT SOLUTION
       ↓
VERIFY FUNCTIONALITY
       ↓
DOCUMENT
```

And always ask:

```text
WHO is affected?

WHAT is affected?

WHAT still works?

WHAT does not work?

WHAT changed?
```

---

# 🧠 Troubleshooting Pattern

For scenario questions, use:

```text
SYMPTOM
   ↓
SCOPE
   ↓
WHAT WORKS?
   ↓
WHAT FAILS?
   ↓
FOLLOW THE PATH
   ↓
FORM THEORY
   ↓
TEST THEORY
```

Avoid jumping immediately to the most complicated explanation.

---

# 🎯 What to Do With Your Score

Don't only record:

```text
34 / 40
```

Record what you missed.

Example:

```text
Wireless:
6 / 6

VPN:
4 / 4

Performance:
3 / 5

Security:
10 / 11

Monitoring:
4 / 4

Redundancy:
4 / 4

Troubleshooting:
5 / 6
```

Now you know:

> **Performance concepts should be reviewed before the final exam.**

That information is more valuable than the total score alone.

---

# 📚 Course Navigation

➡️ **[Return to Practice Exam 2](practice-exam-2.md)**

➡️ **[Exam Tips](../CheatSheet/exam-tips.md)**

➡️ **[Cheat Sheet](../CheatSheet/cheat-sheet.md)**

➡️ **[Command Reference](../CheatSheet/command-reference.md)**

➡️ **[Glossary](../CheatSheet/glossary.md)**

➡️ **[Lessons](../lessons/README.md)**

➡️ **[Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**