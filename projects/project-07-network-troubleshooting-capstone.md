# Project 07 — Network Troubleshooting Capstone

## Project Overview

This is the final project for **Networking Fundamentals**.

You will build a small-business network, establish a known-good baseline, document it, introduce multiple faults, troubleshoot them using the tools from the entire course, and produce a final incident report.

The goal is not simply to make the network work.

The goal is to demonstrate that you can:

```text
Build
Verify
Document
Troubleshoot
Repair
Validate
Explain
```

---

# Scenario

You are the IT technician for a small company with:

```text
Administration
Operations
IT
Servers
Corporate Wi-Fi
Guest Wi-Fi
Internet/upstream connectivity
```

Users report several unrelated network problems after recent changes.

Management wants the problems repaired and documented.

---

# Part 1 — Build the Business Network

Your Packet Tracer topology should include at least:

```text
2–3 switches
1 internal router or Layer 3 device
1 upstream router
4 VLANs or more
6 client endpoints or more
1 server
Wireless clients
DHCP/DNS where supported
```

Suggested VLANs:

```text
VLAN 10 — ADMIN
VLAN 20 — OPERATIONS
VLAN 30 — IT
VLAN 40 — SERVERS
VLAN 50 — GUEST
```

---

# Part 2 — Addressing Plan

Document:

```text
VLAN
Subnet
Gateway
DHCP/static
Purpose
```

Use private/documentation addressing only.

---

# Part 3 — Switching

Configure and verify:

```text
Access ports
VLAN membership
Trunks
MAC learning
STP behavior where redundancy exists
```

Useful commands:

```text
show interfaces status
show mac address-table
show vlan brief
show interfaces trunk
show spanning-tree
```

---

# Part 4 — Routing

Configure and verify:

```text
Inter-VLAN routing
Connected routes
Static/default routing as required
Upstream connectivity
Return paths
```

Useful commands:

```text
show ip interface brief
show ip route
```

---

# Part 5 — Network Services

Where supported, configure:

```text
DHCP
DNS
Web/application service
```

Verify:

```text
Address assignment
Gateway
DNS resolution
Service by IP
Service by name
```

---

# Part 6 — Security Baseline

Apply reasonable defensive controls from Section 6.

Examples:

```text
Guest separation
Least-privilege ACL
Unused switch ports disabled
Secure management recommendations
Corporate/guest wireless separation
```

Do not create offensive testing scenarios.

---

# Part 7 — Monitoring and Documentation

Before introducing faults, create:

```text
Logical topology
IP/VLAN plan
Device inventory
Gateway list
Trunk/uplink list
Route baseline
Service/port list
Known-good ping tests
Known-good DNS tests
Known-good application tests
```

Save a known-good Packet Tracer copy.

---

# Part 8 — Fault 1: Physical

Introduce one Layer 1 fault.

Examples:

```text
Disconnected endpoint
Disconnected uplink
Shutdown interface
```

Troubleshoot from the reported symptom.

---

# Part 9 — Fault 2: Addressing

Introduce one:

```text
Wrong IP
Wrong subnet mask
Wrong default gateway
```

Use endpoint tools and scope analysis to identify it.

---

# Part 10 — Fault 3: DHCP

Create a DHCP-related issue such as:

```text
DHCP disabled
Bad pool
Wrong option
```

Explain the client symptom.

---

# Part 11 — Fault 4: DNS

Create:

```text
Wrong DNS server
Incorrect DNS record
```

Prove the difference between IP connectivity and name resolution.

---

# Part 12 — Fault 5: VLAN

Place an endpoint in the wrong VLAN.

Use switching evidence rather than changing random IP settings.

---

# Part 13 — Fault 6: Trunk

Create a trunk-related failure.

Determine the affected scope before repairing it.

---

# Part 14 — Fault 7: Routing

Create one:

```text
Wrong/missing route
Wrong inter-VLAN gateway
Broken router subinterface/SVI
```

Use routing tables and traceroute/path testing.

---

# Part 15 — Fault 8: Application/Port

Create a situation where:

```text
Host reachable
Required service unavailable
```

Demonstrate why ping is not enough.

Use a port-specific test where appropriate.

---

# Part 16 — Fault 9: Security Policy

Create a safe ACL/policy misconfiguration that blocks required traffic.

Diagnose it without removing all security.

Apply the smallest correction.

---

# Part 17 — Fault 10: Wireless

Create a wireless configuration problem in the isolated lab.

Examples:

```text
Wrong SSID
Wrong authentication setting
Wrong network configuration
Guest/internal placement problem
```

Diagnose and repair.

---

# Part 18 — Windows Tool Validation

For a safe local/training system, demonstrate the purpose of:

```text
ipconfig /all
ping
tracert
nslookup
arp -a
netstat -ano
```

Document what question each command answers.

---

# Part 19 — PowerShell Tool Validation

Demonstrate:

```powershell
Get-NetAdapter
Get-NetIPConfiguration
Get-NetRoute -AddressFamily IPv4
Test-NetConnection example.com -Port 443
Resolve-DnsName example.com
Get-NetTCPConnection
```

Do not publish internal production output.

---

# Part 20 — Wireshark Analysis

Using only an authorized/safe capture, identify at least three:

```text
ARP
ICMP
DNS
TCP handshake
TCP connection
UDP traffic
```

Document:

```text
Filter used
What you observed
Layer involved
What troubleshooting question it answers
```

Do not commit production packet captures to a public repository.

---

# Part 21 — Incident Report

For all ten faults, record:

```text
Ticket number
Symptom
Scope
Layer
Evidence
Theory
Root cause
Correction
Verification
Prevention
```

---

# Part 22 — Final Troubleshooting Run

Restore the network.

Then create five faults without writing the answers into your troubleshooting notes.

Troubleshoot them using only:

```text
Symptoms
Documentation
Commands
Packet analysis
Structured reasoning
```

Time yourself if you want an additional challenge.

---

# Part 23 — Final Documentation Package

Your final project documentation should contain:

```text
Executive summary
Logical topology
Device inventory
IP addressing plan
VLAN plan
Routing plan
Services and ports
Security controls
Monitoring plan
Baseline results
Incident reports
Final validation
Lessons learned
```

---

# Part 24 — Save the Capstone

Save:

```text
project-07-network-troubleshooting-capstone.pkt
```

Recommended repository location:

```text
packet-tracer/projects/
```

You may also create a Markdown incident report in:

```text
troubleshooting/scenarios/
```

---

# Final Validation Checklist

- [ ] Business topology built
- [ ] VLANs configured
- [ ] Trunks configured
- [ ] Inter-VLAN routing works
- [ ] Upstream routing works
- [ ] DHCP/DNS tested where supported
- [ ] Required application service tested
- [ ] Security baseline applied
- [ ] Network documented before faults
- [ ] Physical fault diagnosed
- [ ] Addressing fault diagnosed
- [ ] DHCP fault diagnosed
- [ ] DNS fault diagnosed
- [ ] VLAN fault diagnosed
- [ ] Trunk fault diagnosed
- [ ] Routing fault diagnosed
- [ ] Application/port fault diagnosed
- [ ] Security-policy fault diagnosed
- [ ] Wireless fault diagnosed
- [ ] Windows tools demonstrated
- [ ] PowerShell tools demonstrated
- [ ] Wireshark analysis completed
- [ ] Incident reports completed
- [ ] Five-fault final run completed
- [ ] Final documentation package completed
- [ ] Packet Tracer capstone saved

---

# Final Reflection

1. Which troubleshooting tool gave you the most useful information?
2. Which failures produced similar symptoms?
3. How did determining scope reduce troubleshooting time?
4. Why is a baseline important?
5. Why should DNS be tested separately from raw IP connectivity?
6. Why can ping succeed while an application fails?
7. How do VLAN and routing failures differ?
8. How can security controls complicate troubleshooting?
9. What documentation would help another technician most?
10. What networking topic do you want to practice further?

---

# 🏆 Capstone Complete

You have completed **Project 07 — Network Troubleshooting Capstone**.

You have worked through:

```text
Networking foundations
Ethernet
IPv4 / IPv6
Subnetting
TCP / UDP
DNS / DHCP
NAT / PAT
Routing
Switching
VLANs / trunks
Inter-VLAN routing
Network security
Windows networking tools
PowerShell
Wireshark
Packet analysis
Troubleshooting
Documentation
Monitoring
```

# 🎓 Course Complete!

You have completed the **Networking Fundamentals** training path.

The most important skill to carry forward is the troubleshooting process:

```text
Understand the network
        ↓
Establish the baseline
        ↓
Determine scope
        ↓
Collect evidence
        ↓
Test a theory
        ↓
Repair the root cause
        ↓
Verify everything
        ↓
Document what changed
```

## Continue Learning

Use the course resources for review and continued practice:

➡️ **[Cheat Sheet](../CheatSheet/README.md)**

➡️ **[Resources](../resources/README.md)**

➡️ **[Course Home](../README.md)**
