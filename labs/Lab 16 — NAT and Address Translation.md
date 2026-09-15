# 🧪 Lab 16 — NAT and Address Translation

Welcome to **Lab 16 of Networking Fundamentals**.

In this lab, you'll build a simulated private network connected to an ISP and an external server.

The goal is to see exactly what NAT changes and why PAT allows multiple internal devices to share one outside IPv4 address.

---

# 🎯 Lab Objectives

You will:

- Build an inside/outside topology
- Configure private addressing
- Configure simulated public addressing
- Configure routing
- Configure PAT
- Identify NAT inside/outside interfaces
- Generate NAT translations
- Read a NAT translation table
- Configure static NAT
- Troubleshoot PAT
- Troubleshoot ACL mistakes
- Troubleshoot interface-role mistakes
- Distinguish NAT problems from routing problems

---

# ⏱️ Estimated Time

**75–90 minutes**

---

# 🧰 Tools

You need:

> **Cisco Packet Tracer**

---

# 🏗️ PART 1 — BUILD THE TOPOLOGY

Build:

```text
PC-01 ─┐
       │
PC-02 ─┼── SW-01 ── R-EDGE ── R-ISP ── SW-WAN ── WEB-EXT
       │
PC-03 ─┘
```

Rename the devices accordingly.

---

# 🌐 PART 2 — ADDRESSING PLAN

## Inside LAN

```text
192.168.10.0/24
```

## Edge-to-ISP

Use documentation addressing:

```text
203.0.113.0/30
```

## Simulated Internet Network

Use another documentation range:

```text
198.51.100.0/24
```

---

# 📋 Address Table

| Device | Interface | Address |
|---|---|---|
| PC-01 | NIC | 192.168.10.10/24 |
| PC-02 | NIC | 192.168.10.20/24 |
| PC-03 | NIC | 192.168.10.30/24 |
| R-EDGE | Inside | 192.168.10.1/24 |
| R-EDGE | Outside | 203.0.113.2/30 |
| R-ISP | Toward Edge | 203.0.113.1/30 |
| R-ISP | Toward Server | 198.51.100.1/24 |
| WEB-EXT | NIC | 198.51.100.10/24 |

---

# ⚠️ Router Interface Names

Depending on the Packet Tracer router, interfaces may be named:

```text
g0/0
g0/1
```

or:

```text
g0/0/0
g0/0/1
```

Use the actual interfaces connected in your topology.

---

# 🖥️ PART 3 — CONFIGURE CLIENTS

Configure:

## PC-01

```text
IP:
192.168.10.10

Mask:
255.255.255.0

Gateway:
192.168.10.1
```

## PC-02

```text
IP:
192.168.10.20

Mask:
255.255.255.0

Gateway:
192.168.10.1
```

## PC-03

```text
IP:
192.168.10.30

Mask:
255.255.255.0

Gateway:
192.168.10.1
```

---

# 🔀 PART 4 — CONFIGURE R-EDGE

Example:

```text
enable
configure terminal
```

Inside:

```text
interface g0/0
 ip address 192.168.10.1 255.255.255.0
 no shutdown
 exit
```

Outside:

```text
interface g0/1
 ip address 203.0.113.2 255.255.255.252
 no shutdown
 exit
```

---

# 🌎 PART 5 — CONFIGURE R-ISP

```text
enable
configure terminal
```

Toward R-EDGE:

```text
interface g0/0
 ip address 203.0.113.1 255.255.255.252
 no shutdown
 exit
```

Toward WEB-EXT:

```text
interface g0/1
 ip address 198.51.100.1 255.255.255.0
 no shutdown
 end
```

---

# 🌐 PART 6 — CONFIGURE WEB-EXT

Configure:

```text
IP:
198.51.100.10

Mask:
255.255.255.0

Gateway:
198.51.100.1
```

Enable:

```text
Services
   ↓
HTTP
   ↓
On
```

---

# 🧪 PART 7 — VERIFY BASIC CONNECTIVITY

From PC-01:

```text
ping 192.168.10.1
```

Expected:

> **Success**

From R-EDGE:

```text
ping 203.0.113.1
```

Expected:

> **Success**

From R-ISP:

```text
ping 198.51.100.10
```

Expected:

> **Success**

Fix basic connectivity before configuring NAT.

---

# 🛣️ PART 8 — ADD THE DEFAULT ROUTE

R-EDGE needs to know where external traffic should go.

Configure:

```text
configure terminal
ip route 0.0.0.0 0.0.0.0 203.0.113.1
end
```

Verify:

```text
show ip route
```

Look for a default route.

---

# 🧠 Important Design Choice

Do **not** add a route on R-ISP for:

```text
192.168.10.0/24
```

The ISP should not need to know the private LAN route for this PAT exercise.

That makes NAT necessary for successful return traffic.

---

# 🔐 PART 9 — IDENTIFY NAT INSIDE

On R-EDGE:

```text
configure terminal
interface g0/0
 ip nat inside
 exit
```

---

# 🌎 PART 10 — IDENTIFY NAT OUTSIDE

```text
interface g0/1
 ip nat outside
 exit
```

---

# 📋 PART 11 — CREATE THE NAT ACL

Identify which inside addresses may be translated:

```text
access-list 1 permit 192.168.10.0 0.0.0.255
```

---

# 🔄 PART 12 — CONFIGURE PAT

Configure:

```text
ip nat inside source list 1 interface g0/1 overload
```

Then:

```text
end
```

---

# 🔍 PART 13 — VERIFY NAT CONFIGURATION

Run:

```text
show ip nat statistics
```

Check:

```text
Inside Interface
Outside Interface
```

Then:

```text
show access-lists
```

Verify the ACL matches:

```text
192.168.10.0/24
```

---

# 🧪 PART 14 — GENERATE TRANSLATIONS

From PC-01:

```text
ping 198.51.100.10
```

Then PC-02:

```text
ping 198.51.100.10
```

Then PC-03:

```text
ping 198.51.100.10
```

Expected:

> **Success**

---

# 🔍 PART 15 — VIEW TRANSLATIONS

On R-EDGE:

```text
show ip nat translations
```

Look for the internal addresses:

```text
192.168.10.10
192.168.10.20
192.168.10.30
```

being represented externally through:

```text
203.0.113.2
```

---

# 🧠 What Are You Seeing?

Conceptually:

```text
192.168.10.10
        \
192.168.10.20
          > PAT → 203.0.113.2
192.168.10.30
        /
```

Port or protocol identifiers allow the router to distinguish translations.

---

# 🌐 PART 16 — TEST HTTP

From PC-01's browser:

```text
http://198.51.100.10
```

The external web page should load.

Try from the other PCs.

---

# 🔬 PART 17 — SIMULATION MODE

Switch Packet Tracer to:

> **Simulation Mode**

Generate traffic from PC-01 to WEB-EXT.

Inspect packets as they move through:

```text
PC-01
   ↓
SW-01
   ↓
R-EDGE
   ↓
R-ISP
   ↓
WEB-EXT
```

Pay particular attention to the packet before and after:

```text
R-EDGE
```

---

# 🧠 Observe

Inside R-EDGE:

```text
Source:
192.168.10.10
```

Outside R-EDGE:

```text
Source:
203.0.113.2
```

The NAT router changes the addressing information.

---

# 💥 PART 18 — BREAK THE NAT ACL

Change the NAT configuration so the ACL incorrectly permits:

```text
192.168.20.0/24
```

instead of:

```text
192.168.10.0/24
```

For example, remove/rebuild the lab ACL as needed.

Clear old dynamic translations:

```text
clear ip nat translation *
```

Generate new traffic.

---

# 🔍 Investigate

Run:

```text
show access-lists
```

Then:

```text
show ip nat translations
```

Ask:

```text
Does the ACL match PC-01?

Are new translations being created?
```

---

# 🧠 Root Cause

The NAT rule only translates traffic matched by its ACL.

Wrong network:

```text
192.168.20.0/24
```

Actual network:

```text
192.168.10.0/24
```

Therefore:

> **The inside traffic isn't selected for NAT.**

---

# 🔧 Repair

Restore:

```text
access-list 1 permit 192.168.10.0 0.0.0.255
```

Clear old translations if necessary and retest.

---

# 💥 PART 19 — BREAK INSIDE/OUTSIDE

Temporarily remove or incorrectly configure:

```text
ip nat inside
```

on the LAN interface.

Generate traffic.

Check:

```text
show ip nat statistics
```

and:

```text
show ip nat translations
```

---

# 🧠 Root Cause

NAT must know:

```text
Which side is inside?
Which side is outside?
```

Incorrect interface roles can prevent translation.

---

# 🔧 Repair

Restore:

```text
interface g0/0
 ip nat inside
```

and ensure:

```text
interface g0/1
 ip nat outside
```

---

# 💥 PART 20 — BREAK THE DEFAULT ROUTE

Remove the default route:

```text
no ip route 0.0.0.0 0.0.0.0 203.0.113.1
```

Try reaching:

```text
198.51.100.10
```

---

# 🔍 Investigate

Run:

```text
show ip route
```

Ask:

> Does R-EDGE know where the external network is?

---

# ⭐ Lesson

A failure that looks like NAT may actually be:

> **Routing**

NAT does not replace the routing table.

---

# 🔧 Repair

Restore:

```text
ip route 0.0.0.0 0.0.0.0 203.0.113.1
```

---

# 💥 PART 21 — BREAK THE OUTSIDE INTERFACE

On R-EDGE:

```text
configure terminal
interface g0/1
 shutdown
end
```

Test external communication.

---

# 🔍 Investigate

Use:

```text
show ip interface brief
```

If you see:

```text
administratively down
```

fix Layer 1/interface state before spending time on NAT.

---

# 🔧 Repair

```text
configure terminal
interface g0/1
 no shutdown
end
```

---

# 1️⃣ PART 22 — STATIC NAT

Now add a server to the inside network.

Add:

```text
WEB-INT
```

with:

```text
192.168.10.50/24
Gateway: 192.168.10.1
```

Enable HTTP.

---

# 🔄 Configure Static NAT

On R-EDGE:

```text
configure terminal
ip nat inside source static 192.168.10.50 203.0.113.6
end
```

This maps:

```text
192.168.10.50
        ↕
203.0.113.6
```

---

# ⚠️ Simulation Note

Packet Tracer NAT behavior and topology requirements can vary by device/version. If inbound static-NAT testing does not behave exactly as expected, focus on:

```text
show ip nat translations
```

and the static mapping itself.

The key concept is the fixed:

> **1:1 translation**

---

# 🔍 PART 23 — VIEW STATIC TRANSLATION

Run:

```text
show ip nat translations
```

Identify:

```text
Inside Local:
192.168.10.50
```

and:

```text
Inside Global:
203.0.113.6
```

---

# 📋 PART 24 — COMPARE TRANSLATIONS

Complete:

| Translation | Type |
|---|---|
| 192.168.10.50 ↔ 203.0.113.6 | |
| Many PCs → 203.0.113.2 using ports | |

Answers:

```text
Static NAT

PAT
```

---

# 🛠️ PART 25 — TROUBLESHOOTING CHALLENGE

A user reports:

> "I can reach other computers inside the office, but nothing outside works."

You discover:

```text
Client IP:
192.168.10.20

Gateway:
192.168.10.1

LAN Ping:
Works

R-EDGE → ISP:
Works

R-EDGE → WEB-EXT:
Works

Client → WEB-EXT:
Fails

NAT Table:
No translation appears
```

What should you investigate first?

Possible areas:

```text
NAT ACL
NAT inside/outside roles
PAT configuration
```

---

# 🧭 PART 26 — TROUBLESHOOTING WORKFLOW

Use:

```text
Client IP Correct?
        ↓
Gateway Correct?
        ↓
Reach Gateway?
        ↓
Router Outside Up?
        ↓
Router Can Reach ISP?
        ↓
Default Route Present?
        ↓
Inside Interface Marked?
        ↓
Outside Interface Marked?
        ↓
ACL Matches LAN?
        ↓
PAT Rule Correct?
        ↓
Translation Created?
```

---

# 📝 PART 27 — TROUBLESHOOTING REPORT

Document one failure:

```text
Problem:

________________________________


Initial Symptoms:

________________________________


Client IP:

________________________________


Gateway:

________________________________


Inside Interface:

________________________________


Outside Interface:

________________________________


NAT ACL:

________________________________


NAT Rule:

________________________________


Translation Created?

YES / NO


Root Cause:

________________________________


Solution:

________________________________


Verification:

________________________________
```

---

# 🧠 Knowledge Check

### 1.
What does NAT stand for?

### 2.
What does PAT stand for?

### 3.
What is another name for PAT?

### 4.
Which NAT type creates a permanent 1:1 mapping?

### 5.
Which command shows translations?

### 6.
Which command shows NAT statistics?

### 7.
Which command marks an internal interface?

### 8.
Which command marks an external interface?

### 9.
Does NAT replace routing?

### 10.
Why is PAT useful?

---

# ✅ Answers

1. **Network Address Translation**
2. **Port Address Translation**
3. **NAT overload**
4. **Static NAT**
5. **`show ip nat translations`**
6. **`show ip nat statistics`**
7. **`ip nat inside`**
8. **`ip nat outside`**
9. **No**
10. **It allows many internal hosts to share one or a small number of external IPv4 addresses.**

---

# 🏆 Lab Complete

You have now configured:

```text
Private LAN
        ↓
Routing
        ↓
NAT/PAT
        ↓
ISP
        ↓
External Server
```

You also learned to distinguish:

```text
NAT Failure
vs.
Routing Failure
vs.
Interface Failure
vs.
Client Configuration Failure
```

---

# 💾 Save Your Work

Save locally as:

```text
lab-16-nat-address-translation.pkt
```

You do not need to upload the completed `.pkt` file.

---

# 📍 Course Progress

```text
🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES

✅ Lesson 11 — Switching Fundamentals
✅ Lab 11
✅ Lesson 12 — VLANs & Network Segmentation
✅ Lab 12
✅ Lesson 13 — Routing Fundamentals
✅ Lab 13
✅ Lesson 14 — DHCP
✅ Lab 14
✅ Lesson 15 — DNS
✅ Lab 15
✅ Lesson 16 — NAT & Address Translation
✅ Lab 16

        ↓

🏗️ NEXT:
Project 03 — Build a Routed Small-Business Network
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**