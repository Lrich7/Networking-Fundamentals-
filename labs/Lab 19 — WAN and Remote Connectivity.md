# 🧪 Lab 19 — WAN and Remote Connectivity

Welcome to **Lab 19 of Networking Fundamentals**.

This lab connects many of the skills you've already learned:

```text
IP Addressing
+
Routing
+
DNS
+
DHCP
+
Wireless
+
Internet Connectivity
+
Troubleshooting
```

You'll first inspect the WAN path from your own Windows computer.

Then you'll build two fictional business locations in Packet Tracer and connect them across a simulated WAN.

Finally, you'll work through remote-access VPN troubleshooting scenarios.

---

# 🎯 Lab Objectives

You will:

- Identify your local default gateway
- Test Internet connectivity
- Measure latency
- Observe packet loss
- Use continuous ping
- Use `tracert`
- Use `pathping`
- Understand the local-to-WAN path
- Build two office LANs in Packet Tracer
- Connect offices through a simulated WAN
- Configure routing
- Verify site-to-site connectivity
- Simulate a WAN outage
- Troubleshoot routing failures
- Analyze remote-access VPN failures
- Troubleshoot DNS over VPN
- Recognize overlapping subnet problems
- Compare WAN performance metrics
- Document a WAN incident

---

# ⏱️ Estimated Time

**75–100 minutes**

---

# 🧰 Tools

Use:

- Windows computer
- PowerShell or Command Prompt
- Cisco Packet Tracer
- Calculator

For real-world testing:

> Only test systems and networks you are authorized to use.

---

# 💻 PART 1 — IDENTIFY YOUR IP CONFIGURATION

Open PowerShell or Command Prompt.

Run:

```text
ipconfig /all
```

Find your active adapter.

Record:

```text
IPv4 Address:

____________________________


Subnet Mask:

____________________________


Default Gateway:

____________________________


DNS Server:

____________________________
```

---

# 🧠 PART 2 — IDENTIFY YOUR FIRST ROUTER

Your default gateway is generally the first Layer 3 device your computer uses to reach destinations outside its local subnet.

Conceptually:

```text
Your PC
   │
   ▼
Default Gateway
   │
   ▼
External Networks
```

Record your default gateway:

```text
____________________________
```

---

# 🧪 PART 3 — TEST YOUR GATEWAY

Run:

```text
ping <your-default-gateway>
```

Example:

```text
ping 192.168.1.1
```

Record:

```text
Successful?

YES / NO


Average Latency:

____________________________
```

---

# 🧠 What Does This Test?

This primarily tests:

```text
Your Computer
      ↓
Local Network
      ↓
Default Gateway
```

It does not prove the Internet is working.

---

# 🌎 PART 4 — TEST INTERNET REACHABILITY

Run:

```text
ping 8.8.8.8
```

Record:

```text
Successful?

YES / NO


Average Latency:

____________________________


Packet Loss:

____________________________
```

---

# 🧠 Why Use an IP Address?

Testing an IP address helps separate:

```text
Basic IP Connectivity
```

from:

```text
DNS Name Resolution
```

---

# 📛 PART 5 — TEST DNS

Run:

```text
nslookup example.com
```

Then:

```text
ping example.com
```

Record:

```text
DNS Working?

YES / NO


Resolved Address:

____________________________
```

---

# 🧠 Troubleshooting Logic

If:

```text
ping 8.8.8.8
works
```

but:

```text
nslookup example.com
fails
```

investigate:

> **DNS**

---

# ⏱️ PART 6 — CONTINUOUS PING

Run:

```text
ping 8.8.8.8 -t
```

Let it run for approximately:

```text
30–60 seconds
```

Then press:

```text
Ctrl + C
```

---

# 📝 Record

```text
Minimum:

____________________________


Maximum:

____________________________


Average:

____________________________


Packets Lost:

____________________________
```

---

# 🧠 Question

Were the response times:

```text
Stable

or

Highly Variable
```

Record:

```text
____________________________
```

Large variations can be one clue when investigating network performance.

---

# 🗺️ PART 7 — TRACEROUTE

Run:

```text
tracert 8.8.8.8
```

Observe the path.

---

# 📝 Record

```text
Total Visible Hops:

____________________________


First Hop:

____________________________


Second Hop:

____________________________


Final Destination Reached?

YES / NO
```

---

# ⚠️ Important

You may see:

```text
*
*
*
```

on some hops.

That does not automatically mean the device or path is broken.

Some routers do not respond to these probes.

---

# 🧭 PART 8 — PATHPING

Run:

```text
pathping 8.8.8.8
```

This may take several minutes.

Observe the results.

Look for:

```text
Latency

Packet Loss

Network Hops
```

---

# 📝 Record

```text
Any Packet Loss Observed?

YES / NO


Where?

____________________________


Anything Interesting?

____________________________
```

---

# ⭐ Important Interpretation Rule

Do not declare a router faulty merely because one intermediate hop does not answer probes.

If later hops and the destination respond normally, the intermediate device may simply be filtering or deprioritizing diagnostic traffic.

---

# 🗺️ PART 9 — DRAW YOUR PATH

Create a simplified path based on what you observed:

```text
MY COMPUTER
      │
      ▼
________________
Default Gateway
      │
      ▼
________________
ISP / Provider
      │
      ▼
________________
Internet
      │
      ▼
________________
Destination
```

You do not need to identify every provider router.

The goal is understanding:

> **Your LAN is only the beginning of the path.**

---

# 🏗️ PART 10 — OPEN PACKET TRACER

Now build a fictional two-office network.

Northstar Services has:

```text
SPRINGFIELD HQ

and

KANSAS CITY BRANCH
```

---

# 🗺️ PART 11 — BUILD THE TOPOLOGY

Create:

```text
SPRINGFIELD HQ

PC-HQ
  │
  ▼
SW-HQ
  │
  ▼
R-HQ
  │
  │
  │ WAN
  │
  ▼
R-BRANCH
  │
  ▼
SW-BRANCH
  │
  ▼
PC-BRANCH
```

You can use a direct router-to-router link to represent the WAN for this lab.

---

# 📋 PART 12 — ADDRESSING PLAN

Use:

## Springfield HQ LAN

```text
192.168.10.0/24
```

Router:

```text
192.168.10.1
```

PC-HQ:

```text
192.168.10.10
```

---

## Kansas City Branch LAN

```text
192.168.20.0/24
```

Router:

```text
192.168.20.1
```

PC-BRANCH:

```text
192.168.20.10
```

---

## WAN Network

Use:

```text
10.0.0.0/30
```

R-HQ:

```text
10.0.0.1
```

R-BRANCH:

```text
10.0.0.2
```

---

# 🧠 Why /30?

A traditional point-to-point IPv4 connection only needs two usable addresses.

A `/30` provides:

```text
4 total addresses

2 usable host addresses
```

which works well for this lab.

---

# 🛣️ PART 13 — CONFIGURE R-HQ

Configure the LAN interface.

Example:

```text
enable
configure terminal

interface g0/0
 ip address 192.168.10.1 255.255.255.0
 no shutdown

exit
```

Configure the WAN interface.

Example:

```text
interface g0/1
 ip address 10.0.0.1 255.255.255.252
 no shutdown

end
```

Use the actual interfaces on your Packet Tracer router.

---

# 🛣️ PART 14 — CONFIGURE R-BRANCH

LAN:

```text
enable
configure terminal

interface g0/0
 ip address 192.168.20.1 255.255.255.0
 no shutdown

exit
```

WAN:

```text
interface g0/1
 ip address 10.0.0.2 255.255.255.252
 no shutdown

end
```

---

# 💻 PART 15 — CONFIGURE PC-HQ

Set:

```text
IP:
192.168.10.10

Mask:
255.255.255.0

Gateway:
192.168.10.1
```

---

# 💻 PART 16 — CONFIGURE PC-BRANCH

Set:

```text
IP:
192.168.20.10

Mask:
255.255.255.0

Gateway:
192.168.20.1
```

---

# 🧪 PART 17 — VERIFY LOCAL CONNECTIVITY

From PC-HQ:

```text
ping 192.168.10.1
```

Expected:

> **Success**

From PC-BRANCH:

```text
ping 192.168.20.1
```

Expected:

> **Success**

---

# 🧪 PART 18 — TEST THE WAN LINK

From R-HQ:

```text
ping 10.0.0.2
```

From R-BRANCH:

```text
ping 10.0.0.1
```

Expected:

> **Success**

---

# 🧠 What Works Now?

You have:

```text
HQ LAN
 ✓

WAN Link
 ✓

Branch LAN
 ✓
```

But the routers still need to know how to reach the remote LAN.

---

# 🛣️ PART 19 — ADD STATIC ROUTES

On R-HQ:

```text
configure terminal

ip route 192.168.20.0 255.255.255.0 10.0.0.2

end
```

On R-BRANCH:

```text
configure terminal

ip route 192.168.10.0 255.255.255.0 10.0.0.1

end
```

---

# 🔍 PART 20 — VERIFY ROUTES

Run on both routers:

```text
show ip route
```

Look for the static routes.

---

# 🧪 PART 21 — TEST SITE-TO-SITE CONNECTIVITY

From PC-HQ:

```text
ping 192.168.20.10
```

Expected:

> **Success**

From PC-BRANCH:

```text
ping 192.168.10.10
```

Expected:

> **Success**

---

# 🗺️ Follow the Packet

```text
PC-HQ
192.168.10.10
      │
      ▼
R-HQ
192.168.10.1
      │
      ▼
10.0.0.1
      │
      │ WAN
      ▼
10.0.0.2
      │
      ▼
R-BRANCH
192.168.20.1
      │
      ▼
PC-BRANCH
192.168.20.10
```

---

# ⭐ What Did We Build?

This is a simplified:

> **Routed WAN between two business locations**

It is not yet an encrypted VPN.

The WAN link simply represents provider connectivity.

---

# 💥 PART 22 — FAILURE 1: WAN LINK DOWN

On R-HQ, shut down the WAN interface:

```text
configure terminal

interface g0/1
 shutdown

end
```

Use your actual WAN interface.

---

# 🧪 Test

From PC-HQ:

```text
ping 192.168.20.10
```

Expected:

> **Failure**

---

# 🔍 Investigate

On R-HQ:

```text
show ip interface brief
```

Look for the WAN interface.

---

# 🧠 Root Cause

```text
WAN Interface
Administratively Down
```

---

# 🔧 Repair

```text
configure terminal

interface g0/1
 no shutdown

end
```

Verify:

```text
show ip interface brief
```

Retest.

---

# 💥 PART 23 — FAILURE 2: MISSING ROUTE

Remove the HQ route to the branch.

Example:

```text
configure terminal

no ip route 192.168.20.0 255.255.255.0 10.0.0.2

end
```

---

# 🧪 Test

From PC-HQ:

```text
ping 192.168.20.10
```

Expected:

> **Failure**

---

# 🔍 Investigate

Run:

```text
show ip route
```

Ask:

> Does R-HQ know how to reach 192.168.20.0/24?

---

# 🔧 Repair

Restore:

```text
configure terminal

ip route 192.168.20.0 255.255.255.0 10.0.0.2

end
```

Retest.

---

# ⭐ Important Lesson

A WAN link can be:

```text
UP
```

while communication still fails because:

```text
Routing
```

is incorrect.

---

# 💥 PART 24 — FAILURE 3: WRONG DEFAULT GATEWAY

On PC-BRANCH, temporarily change the gateway from:

```text
192.168.20.1
```

to:

```text
192.168.20.254
```

---

# 🧪 Test

Try:

```text
ping 192.168.10.10
```

Expected:

> **Failure**

---

# 🧠 Why?

PC-BRANCH does not know where to send traffic destined for remote networks.

---

# 🔧 Repair

Restore:

```text
192.168.20.1
```

Retest.

---

# 🧭 PART 25 — USE TRACERT IN PACKET TRACER

From PC-HQ, if supported by the Packet Tracer endpoint:

```text
tracert 192.168.20.10
```

Observe the route.

You should conceptually see:

```text
PC-HQ
 ↓
R-HQ
 ↓
R-BRANCH
 ↓
PC-BRANCH
```

---

# 🔐 PART 26 — SITE-TO-SITE VPN CONCEPT

Now imagine that the WAN between the routers is actually:

```text
The Public Internet
```

You do not want sensitive corporate traffic traveling unprotected.

A site-to-site VPN can create:

```text
HQ LAN
  │
  ▼
R-HQ / Firewall
      ║
      ║ Encrypted VPN Tunnel
      ║
R-BRANCH / Firewall
  │
  ▼
Branch LAN
```

---

# 🧠 Important

The Packet Tracer routed WAN you built demonstrates:

```text
Site-to-Site Connectivity
```

The VPN concept adds:

```text
Encryption
+
Authentication
+
Tunnel Configuration
```

The exact VPN configuration depends on the technology and equipment.

For this fundamentals lab, focus on understanding the architecture and troubleshooting path.

---

# 💻 PART 27 — REMOTE EMPLOYEE SCENARIO

A remote employee has:

```text
Laptop:
192.168.50.25

Home Router:
192.168.50.1
```

The user needs access to:

```text
Corporate Server:
10.20.30.10
```

The path is:

```text
Laptop
  │
  ▼
Home Wi-Fi
  │
  ▼
Home Router
  │
  ▼
ISP
  │
  ▼
Internet
  │
  ▼
Company VPN Gateway
  │
  ▼
Corporate Network
  │
  ▼
Server
```

---

# 🔍 PART 28 — TROUBLESHOOT THE REMOTE PATH

The user says:

> "VPN doesn't work."

Before touching the VPN client, ask:

```text
Does the laptop have a valid IP?

Can it reach the home gateway?

Can it reach the Internet?

Does DNS work?
```

---

# 🧪 Scenario A

The user cannot open any websites.

They cannot ping a public IP.

Should you start by reinstalling the VPN?

> **No**

Investigate local/Internet connectivity first.

---

# 🧪 Scenario B

The user can:

```text
Browse Internet
```

but VPN authentication says:

```text
Invalid credentials
```

Where should you focus?

> **VPN authentication / credentials**

---

# 🧪 Scenario C

User can:

```text
Browse Internet
Connect VPN
Ping 10.20.30.10
```

but cannot reach:

```text
fileserver.company.local
```

Where should you focus?

> **Corporate/VPN DNS**

---

# 🧪 Scenario D

VPN connects.

User cannot reach any corporate subnet.

Where should you investigate?

```text
VPN Routes

Client Routing Table

Firewall Policy

Corporate Routing

Addressing
```

---

# 🧰 PART 29 — WINDOWS ROUTING TABLE

On your own Windows computer, run:

```text
route print
```

or:

```text
Get-NetRoute
```

Look for:

```text
0.0.0.0
```

The default IPv4 route generally points toward your default gateway.

---

# 📝 Record

```text
Default Route Found?

YES / NO


Gateway:

____________________________


Interface:

____________________________
```

---

# 🧠 VPN Connection Effect

When a VPN connects, it may add routes for:

```text
Corporate Networks
```

or alter the:

```text
Default Route
```

depending on whether the VPN uses split or full tunneling.

---

# 🔀 PART 30 — SPLIT-TUNNEL SCENARIO

Suppose:

```text
Corporate Network:
10.20.0.0/16
```

The VPN installs a route for:

```text
10.20.0.0/16
     ↓
VPN
```

Normal Internet traffic continues through:

```text
Home Router
```

This represents:

> **Split tunneling**

---

# 🚇 PART 31 — FULL-TUNNEL SCENARIO

Suppose the VPN causes most traffic to use:

```text
VPN Gateway
```

including Internet traffic.

Conceptually:

```text
Laptop
   │
   ▼
VPN
   │
   ▼
Company
   │
   ▼
Internet
```

This represents:

> **Full tunneling**

---

# ⚠️ PART 32 — OVERLAPPING SUBNETS

Home network:

```text
192.168.10.0/24
```

Corporate network:

```text
192.168.10.0/24
```

Question:

> Why could this cause trouble?

---

# ✅ Answer

The client may have difficulty determining whether:

```text
192.168.10.x
```

is:

```text
Local Home Network
```

or:

```text
Remote Corporate Network
```

depending on the routing/VPN design.

This is an:

> **Overlapping subnet problem**

---

# 📊 PART 33 — WAN PERFORMANCE SCENARIO

Connection A:

```text
Bandwidth:
500 Mbps

Latency:
150 ms

Packet Loss:
0%

Jitter:
5 ms
```

Connection B:

```text
Bandwidth:
100 Mbps

Latency:
20 ms

Packet Loss:
0%

Jitter:
3 ms
```

---

# 🧠 Question

Which connection has:

### More bandwidth?

> **Connection A**

### Lower latency?

> **Connection B**

### Lower jitter?

> **Connection B**

---

# ⭐ Lesson

Do not describe a connection using only:

> **"Fast" or "slow."**

Different performance metrics describe different characteristics.

---

# 📦 PART 34 — PACKET LOSS SCENARIO

You send:

```text
100 packets
```

and receive:

```text
95 packets
```

Calculate packet loss.

```text
100 - 95
=
5 packets lost
```

Percentage:

```text
5 / 100
=
5%
```

Answer:

> **5% packet loss**

---

# ☎️ PART 35 — VOICE TROUBLESHOOTING

Users report:

```text
Internet browsing works

Voice calls are choppy

Video freezes occasionally
```

What should you investigate?

```text
Latency

Jitter

Packet Loss

Upload Capacity

Congestion

Wi-Fi Quality
```

---

# 🔄 PART 36 — REDUNDANT WAN DESIGN

Northstar wants:

```text
Primary:
Fiber

Backup:
5G
```

Draw:

```text
               LAN
                │
                ▼
             Firewall
             /      \
            /        \
         Fiber        5G
         ISP-01      ISP-02
```

---

# 💥 PART 37 — PRIMARY FAILURE

Imagine:

```text
Fiber
  X
```

but:

```text
5G
 ✓
```

Traffic automatically moves to the backup.

What is this called?

> **Failover**

---

# 🧠 PART 38 — FAILURE DOES NOT MEAN ZERO IMPACT

A backup 5G connection might have:

```text
Lower Bandwidth

Higher Latency

Different Public IP

Different Provider Path
```

So:

```text
Internet Still Works
```

does not necessarily mean:

```text
Users Notice No Difference
```

---

# 📝 PART 39 — WAN DOCUMENTATION

Document the fictional Northstar WAN:

| Site | LAN | WAN IP | Primary WAN | Backup |
|---|---|---|---|---|
| Springfield HQ | 192.168.10.0/24 | 10.0.0.1 | Fiber | 5G |
| Kansas City Branch | 192.168.20.0/24 | 10.0.0.2 | Provider WAN | Cellular |

---

# 📝 PART 40 — REMOTE-ACCESS DOCUMENTATION

Create:

```text
Remote User Network:

____________________________


VPN Type:

Remote Access


Corporate Network:

____________________________


VPN Authentication:

____________________________


Split or Full Tunnel:

____________________________


Corporate DNS:

____________________________


Resources Needed:

____________________________
```

---

# 🚨 PART 41 — WAN INCIDENT REPORT

Choose one failure from the lab.

Document:

```text
Problem:

________________________________


Users Affected:

________________________________


Sites Affected:

________________________________


LAN Working?

YES / NO


WAN Interface Up?

YES / NO


Internet Working?

YES / NO


VPN Working?

YES / NO / N/A


DNS Working?

YES / NO


Packet Loss:

________________________________


Latency:

________________________________


Tools Used:

________________________________


Root Cause:

________________________________


Resolution:

________________________________


Verification:

________________________________


What I Learned:

________________________________
```

---

# 🧭 PART 42 — FINAL TROUBLESHOOTING CHALLENGE

A remote employee reports:

> "I can't access the company file server."

You discover:

```text
Wi-Fi:
Connected

Local IP:
192.168.50.25

Home Gateway:
Reachable

Internet:
Working

DNS:
Working for Internet sites

VPN:
Connected

Corporate Server IP:
Reachable

Corporate Server Name:
Fails
```

What is the most likely area to investigate?

> **Corporate DNS / DNS configuration supplied through the VPN**

---

# 🧠 Explain Why

The evidence shows:

```text
Local Network
✓

Internet
✓

VPN
✓

Corporate IP Routing
✓

Corporate Name Resolution
X
```

That dramatically narrows the troubleshooting scope.

This is the method we've been building throughout the course:

> **Follow the evidence.**

---

# 🎓 Network+ Challenge 1

Which metric represents variation in packet delay?

### A. Bandwidth
### B. Jitter
### C. Throughput
### D. VLAN

> **Answer: B — Jitter**

---

# 🎓 Network+ Challenge 2

Which metric represents delay?

> **Latency**

---

# 🎓 Network+ Challenge 3

A business wants a secondary Internet path if fiber fails.

What concept is being implemented?

> **Redundancy**

---

# 🎓 Network+ Challenge 4

The secondary path automatically takes over after the primary fails.

What occurred?

> **Failover**

---

# 🎓 Network+ Challenge 5

What type of VPN commonly connects two business locations?

> **Site-to-site VPN**

---

# 🎓 Network+ Challenge 6

What type of VPN commonly connects an employee's laptop to the company?

> **Remote-access VPN**

---

# 🎓 Network+ Challenge 7

A remote user's Internet works, VPN connects, and internal IP addresses work, but internal hostnames fail.

What should you investigate?

> **DNS**

---

# 🎓 Network+ Challenge 8

A VPN user cannot reach the corporate `192.168.1.0/24` network. Their home network is also `192.168.1.0/24`.

What should you suspect?

> **Overlapping subnets / routing conflict**

---

# 🎓 Network+ Challenge 9

A company has 1 Gbps Internet but voice calls are still choppy.

Which metrics should you examine in addition to bandwidth?

> **Latency, jitter, and packet loss**

---

# 🎓 Network+ Challenge 10

What command displays the Windows routing table?

> **`route print`**

PowerShell can also use:

```text
Get-NetRoute
```

---

# 🏆 LAB COMPLETION CHECKLIST

- [ ] I identified my IPv4 configuration
- [ ] I identified my default gateway
- [ ] I tested my local gateway
- [ ] I tested Internet IP connectivity
- [ ] I tested DNS
- [ ] I ran a continuous ping
- [ ] I observed latency
- [ ] I checked packet loss
- [ ] I used `tracert`
- [ ] I used `pathping`
- [ ] I mapped my local-to-Internet path
- [ ] I built two business sites in Packet Tracer
- [ ] I created separate LAN subnets
- [ ] I created a WAN subnet
- [ ] I configured router interfaces
- [ ] I configured static routes
- [ ] I verified site-to-site connectivity
- [ ] I troubleshot a WAN interface failure
- [ ] I troubleshot a missing route
- [ ] I troubleshot an incorrect default gateway
- [ ] I reviewed site-to-site VPN architecture
- [ ] I reviewed remote-access VPN architecture
- [ ] I reviewed split tunneling
- [ ] I reviewed full tunneling
- [ ] I identified an overlapping-subnet problem
- [ ] I compared bandwidth and latency
- [ ] I reviewed jitter
- [ ] I calculated packet loss
- [ ] I designed WAN redundancy
- [ ] I reviewed failover
- [ ] I documented the WAN
- [ ] I completed a WAN incident report

---

# 🏆 Lab 19 Complete

You can now follow a connection far beyond the local network:

```text
Remote Laptop
      │
      ▼
Home Wi-Fi
      │
      ▼
Home Router
      │
      ▼
ISP
      │
      ▼
Internet
      │
      ▼
VPN Gateway
      │
      ▼
Corporate Firewall
      │
      ▼
Corporate Router
      │
      ▼
Corporate Network
      │
      ▼
Server
```

You also know that:

```text
Connected to Wi-Fi
```

does not prove:

```text
Internet works
```

and:

```text
Internet works
```

does not prove:

```text
VPN works
```

and:

```text
VPN connected
```

does not prove:

```text
DNS
Routing
Applications
```

are working.

Troubleshooting is about finding:

> **The first point in the path where expected behavior stops.**

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ COMPLETE
✅ Project 02

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES
✅ COMPLETE
✅ Project 03

🟠 PHASE 4 — NETWORK IMPLEMENTATION

✅ Lesson 17 — Network Cabling & Physical Infrastructure
✅ Lab 17

✅ Lesson 18 — Wireless Networking
✅ Lab 18

✅ Lesson 19 — WAN & Remote Connectivity
✅ Lab 19

        ↓

🟡 NEXT:
Lesson 20 — Network Monitoring, Security & Final Troubleshooting
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 20 — Network Monitoring, Security & Final Troubleshooting**

Lesson 20 will bring the course together.

We'll cover:

```text
Network Monitoring

SNMP

Syslog

Baselines

Logs

Alerts

Availability

Performance Monitoring

Common Network Threats

Firewalls

ACLs

Network Segmentation

Port Security Concepts

Secure Management

Troubleshooting Methodology

Documentation

Escalation

Final Troubleshooting Scenarios
```

Then we'll be ready for the **final course project**, where the learner can design, build, document, secure, and troubleshoot a small business network from beginning to end.

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**