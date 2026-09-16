# 📘 Lesson 20 — Network Monitoring, Security & Final Troubleshooting

Welcome to **Lesson 20 of Networking Fundamentals**.

You have reached the final lesson.

Throughout this course, you have learned how networks are:

```text
Built
  ↓
Addressed
  ↓
Switched
  ↓
Routed
  ↓
Connected
  ↓
Secured
  ↓
Troubleshot
```

But a network administrator's job does not end when the network starts working.

A production network must also be:

```text
MONITORED

SECURED

DOCUMENTED

MAINTAINED

TROUBLESHOT
```

That is the focus of Lesson 20.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain why network monitoring is important
- Understand network baselines
- Explain SNMP
- Explain Syslog
- Understand logs and alerts
- Monitor availability and performance
- Understand uptime and downtime
- Recognize common network security threats
- Explain firewall concepts
- Understand ACLs
- Explain network segmentation
- Understand port security concepts
- Explain secure device management
- Understand AAA
- Recognize configuration-management importance
- Follow a structured troubleshooting methodology
- Determine troubleshooting scope
- Establish a theory of probable cause
- Test a theory
- Implement and verify solutions
- Document incidents
- Know when to escalate
- Troubleshoot multi-layer network problems

---

# 🎓 Network+ Focus

For **CompTIA Network+ N10-009**, pay particular attention to:

- SNMP
- Syslog
- Logs
- Baselines
- Performance monitoring
- Availability monitoring
- Network segmentation
- ACLs
- Firewalls
- Authentication
- AAA
- Secure protocols
- Common attacks
- Troubleshooting methodology
- Documentation
- Change management
- Configuration backups
- Escalation

---

# 👀 Why Monitor a Network?

Consider two IT departments.

## IT Department A

Waits until:

> "Someone calls and says the network is down."

## IT Department B

Receives an alert:

> "WAN interface packet loss exceeded threshold."

before most users even report the problem.

Monitoring helps IT become:

> **Proactive instead of purely reactive.**

---

# 📊 What Can Be Monitored?

Network monitoring systems may track:

```text
Device Availability

Interface Status

Bandwidth Utilization

CPU Usage

Memory Usage

Packet Loss

Latency

Errors

Temperature

Power

Wireless Clients

WAN Connections

VPN Status
```

---

# 🟢 Availability Monitoring

One of the simplest questions is:

> **Is the device reachable?**

Example:

```text
SW-01
UP

R-01
UP

AP-01
UP

FIREWALL-01
DOWN
```

A monitoring system could generate an alert when a critical device becomes unreachable.

---

# ⏱️ Uptime

Uptime describes how long a system has remained operational.

Example:

```text
Router Uptime:

45 days
12 hours
17 minutes
```

Unexpected uptime changes can provide clues.

If a router normally runs for months but suddenly reports:

```text
Uptime:
8 minutes
```

it may have rebooted recently.

---

# 📈 Performance Monitoring

A device can be:

```text
UP
```

but still perform poorly.

Monitoring may therefore track:

```text
Latency

Packet Loss

Bandwidth

Interface Utilization

Errors

CPU

Memory
```

---

# 🧠 Example

WAN link:

```text
Bandwidth:
500 Mbps

Current Utilization:
495 Mbps
```

The connection is technically:

```text
UP
```

but congestion may affect users.

---

# 📏 Network Baseline

A baseline represents:

> **What normal performance looks like**

for your environment.

Example:

```text
Normal WAN Usage:
100–200 Mbps

Normal Latency:
15–25 ms

Normal Packet Loss:
0%

Normal Firewall CPU:
20–40%
```

---

# 🚨 Why Baselines Matter

Suppose current latency is:

```text
60 ms
```

Is that bad?

Without knowing the normal value:

> **You may not know.**

If the baseline is:

```text
15 ms
```

then:

```text
60 ms
```

is a significant change.

---

# ⭐ Key Concept

You cannot easily identify:

> **Abnormal**

without understanding:

> **Normal**

---

# 📡 SNMP

SNMP stands for:

> **Simple Network Management Protocol**

SNMP allows monitoring systems to collect information from network devices.

---

# 🗺️ Basic SNMP Architecture

```text
Monitoring Server
      │
      │ SNMP
      ▼
   Router

Monitoring Server
      │
      │ SNMP
      ▼
   Switch

Monitoring Server
      │
      │ SNMP
      ▼
 Firewall
```

---

# 🧠 SNMP Manager and Agent

Conceptually:

```text
SNMP MANAGER
Monitoring System
      │
      ▼
SNMP AGENT
Network Device
```

The manager requests or receives information associated with managed devices.

---

# 📚 MIB

MIB stands for:

> **Management Information Base**

A MIB organizes information that can be monitored through SNMP.

Examples might include information about:

```text
Interfaces

Traffic Counters

Errors

Device Status
```

---

# 🔢 OID

OID stands for:

> **Object Identifier**

An OID identifies a specific managed object within the SNMP information structure.

For fundamentals, remember:

```text
SNMP
 ↓
MIB
 ↓
OID
```

---

# 🔐 SNMP Versions

You may encounter:

```text
SNMPv1

SNMPv2c

SNMPv3
```

SNMPv3 provides stronger security capabilities such as authentication and encryption options.

For secure modern deployments:

> **SNMPv3 is generally preferred when supported and properly configured.**

---

# 🚨 SNMP Trap

Normally a monitoring server may poll a device.

A device can also send an unsolicited notification:

> **SNMP Trap**

Example:

```text
Switch Port
   │
   X
Goes Down
   │
   ▼
SNMP Trap
   │
   ▼
Monitoring Server
```

---

# 📝 Syslog

Syslog is used to send event and log messages.

Conceptually:

```text
Router ─────┐
            │
Switch ─────┼──► Syslog Server
            │
Firewall ───┤
            │
AP ─────────┘
```

Instead of checking logs individually on every device, organizations can centralize them.

---

# 📜 Logs

Logs provide records of events.

Examples:

```text
Interface went down

Administrator logged in

VPN failed

Authentication failed

Device rebooted

Configuration changed

Firewall blocked traffic
```

---

# 🕵️ Logs Tell a Story

Imagine:

```text
09:02
WAN interface down

09:03
VPN tunnels disconnected

09:03
Cloud applications unreachable

09:04
Users begin calling IT
```

Those events help establish:

> **A timeline**

---

# 🚨 Alerts

Monitoring systems can generate alerts when conditions cross thresholds.

Example:

```text
Packet Loss > 5%

WAN Utilization > 90%

Device Down

Temperature High

VPN Tunnel Down
```

---

# ⚠️ Alert Fatigue

Too many meaningless alerts can cause administrators to ignore them.

Good monitoring requires useful thresholds.

The goal is not:

> **Alert about everything.**

The goal is:

> **Alert about things that require attention.**

---

# 📊 Monitoring Dashboard

A simple dashboard might show:

| Device | Status | Latency | Notes |
|---|---|---:|---|
| FIREWALL-01 | UP | 2 ms | Normal |
| SW-CORE-01 | UP | 1 ms | Normal |
| AP-01 | UP | 3 ms | Normal |
| ISP-01 | UP | 18 ms | Normal |
| ISP-02 | UP | 45 ms | Backup |

---

# 🔐 NETWORK SECURITY

Networks connect devices.

That connectivity also creates opportunities for unauthorized access.

Network security attempts to protect:

```text
Confidentiality

Integrity

Availability
```

---

# 🛡️ CIA Triad

The three concepts are commonly called the:

> **CIA Triad**

---

# 🔒 Confidentiality

Confidentiality means:

> Information should only be accessible to authorized users.

Examples:

```text
Encryption

Authentication

Permissions
```

---

# 🧾 Integrity

Integrity means:

> Information should not be changed improperly.

Examples include:

```text
Hashing

Digital Signatures

Access Controls
```

---

# 🟢 Availability

Availability means:

> Authorized users should be able to access systems when needed.

Examples:

```text
Redundancy

Backups

Failover

Monitoring
```

---

# 🚨 Common Network Threats

Network administrators should recognize threats such as:

```text
Malware

Phishing

Unauthorized Access

Password Attacks

Denial of Service

Rogue Devices

Rogue Wireless APs

Man-in-the-Middle Attacks

Spoofing

Misconfiguration
```

---

# 🦠 Malware

Malware is malicious software.

Examples include:

```text
Virus

Worm

Trojan

Ransomware
```

Network segmentation and security controls can help limit the impact of compromised devices.

---

# 🎣 Phishing

Phishing attempts to trick users into providing information or performing dangerous actions.

Examples:

```text
Fake Login Page

Malicious Attachment

Fake Password Reset

Fraudulent MFA Request
```

Technical controls help, but:

> **User awareness is also important.**

---

# 🌊 Denial of Service

A denial-of-service attack attempts to make a service unavailable.

A distributed denial-of-service attack:

> **DDoS**

uses multiple sources.

---

# 👤 Rogue Device

A rogue device is an unauthorized device connected to the environment.

Example:

```text
Unknown Laptop
      │
      ▼
Wall Jack
      │
      ▼
Corporate Switch
```

Organizations should control which devices are allowed to connect.

---

# 📡 Rogue Access Point

Someone could connect an unauthorized wireless AP:

```text
Corporate LAN
     │
     ▼
Unauthorized AP
     )))
     )))
Unknown Wireless Clients
```

This could create an unintended path into the network.

---

# 🧱 FIREWALLS

A firewall controls traffic between networks based on configured policies.

Conceptually:

```text
LAN
 │
 ▼
FIREWALL
 │
 ▼
INTERNET
```

---

# 🛡️ Firewall Rules

A firewall rule might say:

```text
ALLOW
Internal Users
        ↓
HTTPS
        ↓
Internet
```

Another might say:

```text
DENY
Guest Network
      ↓
Corporate Servers
```

---

# 📋 ACL

ACL stands for:

> **Access Control List**

ACLs define which traffic should be:

```text
PERMITTED

or

DENIED
```

based on configured criteria.

---

# 🧠 Example ACL Logic

```text
Permit:
192.168.10.0/24
      ↓
Server VLAN
      ↓
HTTPS

Deny:
Guest VLAN
      ↓
Server VLAN
```

---

# 🧱 Network Segmentation

Segmentation separates devices into different network areas.

Remember VLANs?

```text
VLAN 10
Employees

VLAN 20
Servers

VLAN 30
Printers

VLAN 50
Guests

VLAN 60
IoT
```

---

# 🔐 Segmentation + Security

Without controls:

```text
Guest
 ↓
Server
```

might be possible.

With appropriate routing/firewall policy:

```text
Guest VLAN
     │
     X
     │
Server VLAN
```

while:

```text
Guest VLAN
     │
     ▼
Internet
```

is permitted.

---

# ⭐ Important

A VLAN alone does not automatically provide complete security.

Security depends on:

```text
Segmentation
+
Routing
+
ACLs
+
Firewall Policy
+
Authentication
+
Device Configuration
```

---

# 🔌 Port Security Concepts

Switch ports should not necessarily allow any unknown device unrestricted network access.

Controls may include:

```text
Port Security

802.1X

Network Access Control

MAC Address Restrictions

Unused Port Shutdown
```

Implementation depends on the environment.

---

# 🚫 Unused Switch Ports

A simple security practice is:

> **Disable unused switch ports when appropriate.**

Instead of:

```text
Unused Wall Jack
      │
      ▼
Active Switch Port
```

you may configure unused ports as administratively disabled according to organizational policy.

---

# 🔐 Secure Device Management

Network devices must also be administered securely.

Avoid insecure management protocols when secure alternatives exist.

---

# 📋 Secure Alternatives

| Avoid | Prefer |
|---|---|
| Telnet | SSH |
| HTTP management | HTTPS |
| FTP | SFTP/SCP where appropriate |
| SNMPv1/v2c for sensitive management | SNMPv3 where supported |

---

# 🔐 SSH

SSH provides encrypted remote command-line management.

Example:

```text
Administrator
      │
      │ SSH
      ▼
   Switch
```

---

# 🔑 AAA

AAA stands for:

```text
Authentication

Authorization

Accounting
```

---

# 👤 Authentication

Authentication asks:

> **Who are you?**

Example:

```text
Username
+
Password
+
MFA
```

---

# 🚪 Authorization

Authorization asks:

> **What are you allowed to do?**

Example:

```text
Help Desk:
View status

Network Admin:
Change configuration
```

---

# 📝 Accounting

Accounting records:

> **What did the user do?**

Example:

```text
Administrator:
Logged in 09:15

Changed VLAN 20

Logged out 09:32
```

---

# 💾 Configuration Backups

Imagine a switch fails.

Replacement hardware arrives.

But:

```text
No configuration backup exists.
```

Now someone must rebuild:

```text
VLANs

Trunks

Management Settings

ACLs

Port Configurations
```

from memory.

That is not a good recovery plan.

---

# 📁 Configuration Management

Organizations should maintain:

```text
Configuration Backups

Device Inventory

Network Diagrams

IP Address Plans

Change Records

Firmware Information
```

---

# 🔄 Change Management

A configuration change can fix one problem and create another.

Before making significant changes, consider:

```text
What are we changing?

Why?

Who approved it?

When?

What systems could be affected?

How do we test it?

How do we roll back?
```

---

# 🔙 Rollback Plan

Before changing:

```text
Firewall Rules
```

know how to restore the previous configuration if something goes wrong.

That is a:

> **Rollback plan**

---

# 🧰 TROUBLESHOOTING METHODOLOGY

Throughout this course, we have repeatedly followed a structured process.

Now we'll formalize it.

---

# 1️⃣ Identify the Problem

Gather information.

Ask:

```text
What is happening?

Who is affected?

When did it start?

What changed?

What still works?

What fails?

Is it intermittent?

Can it be reproduced?
```

---

# ⭐ Scope First

One of the most valuable questions is:

> **Who is affected?**

Compare:

```text
One User
```

vs.

```text
One Department
```

vs.

```text
One VLAN
```

vs.

```text
One Building
```

vs.

```text
Entire Company
```

The scope gives clues about where the problem exists.

---

# 2️⃣ Establish a Theory

Based on the evidence, develop likely causes.

Example:

```text
User:
Cannot open websites

Can ping gateway:
YES

Can ping 8.8.8.8:
YES

Can resolve example.com:
NO
```

Theory:

> **DNS problem**

---

# 🚫 Do Not Randomly Change Things

Poor troubleshooting:

```text
Reboot Switch

Change DNS

Replace Cable

Reset Router

Reinstall Driver
```

all at once.

Now even if the problem disappears:

> **You do not know what fixed it.**

---

# 3️⃣ Test the Theory

Use the smallest useful test.

For suspected DNS:

```text
nslookup example.com
```

Compare:

```text
ping 8.8.8.8
```

with:

```text
ping example.com
```

---

# 4️⃣ Establish a Plan of Action

Once the cause is identified:

```text
Determine Fix

Consider Impact

Obtain Approval if Needed

Create Rollback Plan

Implement Change
```

---

# 5️⃣ Implement the Solution

Make the appropriate change.

Examples:

```text
Correct DNS

Enable Interface

Replace Cable

Correct VLAN

Add Route

Fix DHCP Scope

Restore Firewall Rule
```

---

# 6️⃣ Verify Full Functionality

Do not stop at:

> **"The error disappeared."**

Verify:

```text
Can user connect?

Can user reach gateway?

Can user resolve DNS?

Can user access application?

Are other users still working?

Did monitoring return to normal?
```

---

# 7️⃣ Document

Record:

```text
Problem

Symptoms

Scope

Cause

Actions

Solution

Verification

Time

Devices Affected
```

This creates institutional knowledge.

---

# 🧠 Troubleshooting Flow

```text
IDENTIFY PROBLEM
       ↓
ESTABLISH THEORY
       ↓
TEST THEORY
       ↓
ESTABLISH PLAN
       ↓
IMPLEMENT
       ↓
VERIFY
       ↓
DOCUMENT
```

---

# 🧗 Escalation

Not every problem should be solved entirely by one technician.

Escalate when:

```text
You lack required access

Change exceeds your authority

Vendor involvement is required

Security incident is suspected

Major outage exists

Risk is too high

Expertise is required
```

---

# ⭐ Good Escalation

Do not send:

> "Network broken. Please help."

Send:

```text
Affected:
Entire Springfield office

Started:
09:14

Gateway:
Reachable

ISP Gateway:
Unreachable

Firewall WAN:
Up

Packet Loss:
100% beyond ISP handoff

Changes:
None known

Troubleshooting:
LAN verified operational

Suspected:
Provider outage
```

That gives the next technician useful evidence.

---

# 🧅 Troubleshoot by Layers

Remember the OSI model.

A problem can exist at:

```text
Layer 1
Cable / Signal

Layer 2
VLAN / Switching

Layer 3
IP / Routing

Layer 4
Ports / Transport

Layers 5–7
Session / Application / DNS / Services
```

---

# 🔍 Example

User says:

> "The Internet is down."

Start with:

```text
Link?
 ↓
IP?
 ↓
Gateway?
 ↓
Routing?
 ↓
DNS?
 ↓
Application?
```

---

# 🧠 Final Troubleshooting Scenario

User reports:

> "The server isn't working."

You discover:

```text
PC IP:
192.168.10.25

Gateway:
192.168.10.1

Gateway Ping:
SUCCESS

Server IP:
192.168.20.10

Server IP Ping:
SUCCESS

Server Name:
FAILS
```

What is most likely?

> **DNS / name resolution**

Notice how much of the network has already been proven operational.

---

# 📋 Final Command Toolkit

Windows:

```text
ipconfig /all

ping

tracert

pathping

nslookup

arp -a

route print

netstat

Get-NetAdapter

Get-NetIPConfiguration

Get-NetRoute

netsh wlan show interfaces
```

Cisco:

```text
show ip interface brief

show interfaces

show vlan brief

show interfaces trunk

show mac address-table

show ip route

show running-config
```

---

# 📋 Quick Reference

| Concept | Purpose |
|---|---|
| SNMP | Monitor/manage network information |
| Syslog | Centralized event logging |
| Baseline | Establish normal behavior |
| Alert | Notify IT about conditions |
| Firewall | Control traffic between networks |
| ACL | Permit/deny traffic |
| VLAN | Logical segmentation |
| SSH | Secure remote CLI management |
| AAA | Authentication, Authorization, Accounting |
| Backup | Preserve configurations/data |
| Change Management | Control infrastructure changes |
| Rollback | Restore previous working state |
| Escalation | Transfer issue when appropriate |

---

# 🧠 Final Knowledge Check

### 1.
What is a network baseline?

### 2.
What does SNMP stand for?

### 3.
What does Syslog provide?

### 4.
What is an SNMP trap?

### 5.
What does AAA stand for?

### 6.
Why segment a network?

### 7.
What secure protocol should generally replace Telnet?

### 8.
Why maintain configuration backups?

### 9.
What should happen after implementing a fix?

### 10.
What is the final troubleshooting step?

---

# ✅ Answers

1. **A measurement/record of normal network behavior**
2. **Simple Network Management Protocol**
3. **Event/log message collection**
4. **An unsolicited SNMP notification from a device**
5. **Authentication, Authorization, Accounting**
6. **To separate systems and control traffic/access between network areas**
7. **SSH**
8. **To restore device configurations and aid recovery**
9. **Verify full functionality**
10. **Document the problem, cause, solution, and results**

---

# 🎓 Network+ Challenge 1

A network normally has:

```text
20 ms latency
```

but now reports:

```text
180 ms
```

What helps you know this is abnormal?

> **The network baseline**

---

# 🎓 Network+ Challenge 2

What protocol can network devices use to send centralized log messages?

> **Syslog**

---

# 🎓 Network+ Challenge 3

A guest VLAN can access an internal database server.

What should you investigate?

> **Segmentation policy, routing, ACLs, and firewall rules**

---

# 🎓 Network+ Challenge 4

A technician changes five settings simultaneously and the problem disappears.

What troubleshooting mistake occurred?

> **Multiple variables were changed without isolating and testing the cause.**

---

# 🎓 Network+ Challenge 5

A problem requires a firewall change you are not authorized to perform.

What should you do?

> **Document your findings and escalate through the appropriate process.**

---

# 🎓 Network+ Challenge 6

A switch fails and no configuration backup exists.

What operational practice would have reduced recovery difficulty?

> **Configuration backup and configuration management**

---

# 📝 Key Takeaways

You should now understand:

- Monitoring allows IT to detect problems proactively.
- Availability and performance are different.
- Baselines define normal network behavior.
- SNMP can provide network monitoring information.
- Syslog centralizes event messages.
- Useful alerts help IT respond quickly.
- Security requires multiple layers.
- Firewalls and ACLs control traffic.
- VLANs help segment networks.
- Segmentation must be combined with access-control policy.
- Secure protocols should replace insecure management protocols.
- AAA controls and records administrative access.
- Configuration backups improve recoverability.
- Changes should include testing and rollback planning.
- Troubleshooting should follow a structured process.
- Scope is one of the strongest troubleshooting clues.
- Evidence should drive your theory.
- Fixes must be verified.
- Problems and solutions should be documented.
- Good escalation includes evidence.

---

# 🧪 Next Step — Complete Lab 20

Lab 20 is your final guided troubleshooting lab.

You'll:

- Build a multi-VLAN network
- Configure routing
- Configure DHCP
- Configure DNS
- Add a server
- Test network services
- Establish a baseline
- Examine logs and monitoring concepts
- Apply basic segmentation
- Secure unused ports
- Troubleshoot Layer 1 failures
- Troubleshoot VLAN failures
- Troubleshoot DHCP
- Troubleshoot routing
- Troubleshoot DNS
- Troubleshoot WAN connectivity
- Document each incident
- Practice escalation

➡️ **[Lab 20 — Network Monitoring, Security & Final Troubleshooting](../labs/lab-20-monitoring-security-troubleshooting.md)**

---

# 🏁 After Lab 20

There is one final challenge:

> **🏆 Project 04 — Small Business Network Capstone**

Unlike the guided labs, Project 04 gives you requirements instead of every command.

You will design and build the network yourself.

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ COMPLETE

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES
✅ COMPLETE

🟠 PHASE 4 — NETWORK IMPLEMENTATION

✅ Lesson 17
✅ Lab 17

✅ Lesson 18
✅ Lab 18

✅ Lesson 19
✅ Lab 19

✅ Lesson 20 — Network Monitoring, Security & Final Troubleshooting

        ↓

🟡 NEXT:
Lab 20

        ↓

🏆 Project 04 — Small Business Network Capstone
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**