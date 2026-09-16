# 🧪 Lab 20 — Network Monitoring, Security & Final Troubleshooting

Welcome to **Lab 20**.

This is the final guided lab of Networking Fundamentals.

Instead of introducing one isolated technology, this lab combines:

```text
Switching
+
VLANs
+
Routing
+
DHCP
+
DNS
+
Servers
+
Security
+
Monitoring
+
Troubleshooting
```

You will build a working network.

Then you will break it.

Then you will troubleshoot it systematically.

---

# 🎯 Lab Objectives

You will:

- Build a multi-VLAN network
- Configure VLANs
- Configure trunks
- Configure inter-VLAN routing
- Configure DHCP
- Configure DNS
- Configure a server
- Verify connectivity
- Establish a basic network baseline
- Review monitoring concepts
- Apply basic network segmentation
- Disable unused ports
- Troubleshoot physical connectivity
- Troubleshoot VLAN configuration
- Troubleshoot DHCP
- Troubleshoot DNS
- Troubleshoot routing
- Troubleshoot WAN connectivity
- Use show commands
- Determine issue scope
- Establish and test theories
- Verify repairs
- Document incidents
- Practice escalation

---

# ⏱️ Estimated Time

**90–120 minutes**

---

# 🧰 Tools

Use:

> **Cisco Packet Tracer**

Optional:

- Windows PowerShell
- Command Prompt
- Notes or troubleshooting worksheet

---

# 🏢 Scenario

Northstar Services has a small office.

The company needs separate networks for:

```text
Employees

Servers

Guests
```

The network also needs:

```text
DHCP

DNS

Web Server

Internet/WAN Simulation

Security Segmentation
```

---

# 🗺️ PART 1 — BUILD THE TOPOLOGY

Build:

```text
                  ISP-RTR
                     │
                     │
                   R-01
                     │
                   TRUNK
                     │
                   SW-01
                /      |      \
               /       |       \
          PC-EMP1   SERVER-01   AP-01
          PC-EMP2                )))
                                 )))
                              GUEST-01
```

---

# 📋 PART 2 — VLAN PLAN

Create:

| VLAN | Name | Purpose |
|---:|---|---|
| 10 | EMPLOYEES | Employee devices |
| 20 | SERVERS | Servers |
| 50 | GUESTS | Guest devices |
| 99 | MANAGEMENT | Management |

---

# 🌐 PART 3 — ADDRESSING PLAN

Use:

| VLAN | Network | Gateway |
|---:|---|---|
| 10 | 192.168.10.0/24 | 192.168.10.1 |
| 20 | 192.168.20.0/24 | 192.168.20.1 |
| 50 | 192.168.50.0/24 | 192.168.50.1 |
| 99 | 192.168.99.0/24 | 192.168.99.1 |

WAN:

```text
R-01:
10.0.0.1/30

ISP-RTR:
10.0.0.2/30
```

---

# 🔀 PART 4 — CREATE VLANS

On SW-01:

```text
enable
configure terminal

vlan 10
 name EMPLOYEES

vlan 20
 name SERVERS

vlan 50
 name GUESTS

vlan 99
 name MANAGEMENT

end
```

Verify:

```text
show vlan brief
```

---

# 🔌 PART 5 — ASSIGN ACCESS PORTS

Assign your actual connected interfaces.

Example:

```text
configure terminal

interface fa0/1
 switchport mode access
 switchport access vlan 10

interface fa0/2
 switchport mode access
 switchport access vlan 10

interface fa0/3
 switchport mode access
 switchport access vlan 20

interface fa0/4
 switchport mode access
 switchport access vlan 50

end
```

---

# 🌉 PART 6 — CONFIGURE THE TRUNK

Configure the switch interface connected to R-01.

Example:

```text
configure terminal

interface g0/1
 switchport mode trunk

end
```

Verify:

```text
show interfaces trunk
```

---

# 🛣️ PART 7 — ROUTER-ON-A-STICK

On R-01:

```text
enable
configure terminal

interface g0/0
 no shutdown
```

Employee VLAN:

```text
interface g0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
```

Server VLAN:

```text
interface g0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
```

Guest VLAN:

```text
interface g0/0.50
 encapsulation dot1Q 50
 ip address 192.168.50.1 255.255.255.0
```

Management VLAN:

```text
interface g0/0.99
 encapsulation dot1Q 99
 ip address 192.168.99.1 255.255.255.0

end
```

---

# 🌎 PART 8 — WAN

Configure R-01:

```text
configure terminal

interface g0/1
 ip address 10.0.0.1 255.255.255.252
 no shutdown

end
```

Configure ISP-RTR:

```text
enable
configure terminal

interface g0/0
 ip address 10.0.0.2 255.255.255.252
 no shutdown

end
```

---

# 🛣️ PART 9 — DEFAULT ROUTE

On R-01:

```text
configure terminal

ip route 0.0.0.0 0.0.0.0 10.0.0.2

end
```

---

# 📦 PART 10 — DHCP

Exclude infrastructure addresses:

```text
configure terminal

ip dhcp excluded-address 192.168.10.1 192.168.10.20
ip dhcp excluded-address 192.168.50.1 192.168.50.20
```

Employee DHCP:

```text
ip dhcp pool EMPLOYEES
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
 dns-server 192.168.20.10
```

Guest DHCP:

```text
ip dhcp pool GUESTS
 network 192.168.50.0 255.255.255.0
 default-router 192.168.50.1
 dns-server 192.168.20.10

end
```

---

# 🖥️ PART 11 — SERVER

Configure SERVER-01:

```text
IP:
192.168.20.10

Mask:
255.255.255.0

Gateway:
192.168.20.1

DNS:
192.168.20.10
```

Enable:

```text
HTTP

DNS
```

---

# 📛 PART 12 — DNS

Create:

```text
intranet.northstar.local
```

pointing to:

```text
192.168.20.10
```

---

# 💻 PART 13 — EMPLOYEE CLIENTS

Set:

```text
PC-EMP1

PC-EMP2
```

to:

> **DHCP**

Verify they receive:

```text
192.168.10.x
```

---

# 📡 PART 14 — GUEST CLIENT

Connect GUEST-01 through the wireless AP if practical in your Packet Tracer build.

Configure it for DHCP.

Expected:

```text
192.168.50.x
```

---

# 🧪 PART 15 — VERIFY THE NETWORK

From PC-EMP1 test:

```text
ping 192.168.10.1
```

Then:

```text
ping 192.168.20.10
```

Then browse:

```text
http://intranet.northstar.local
```

Everything should work before continuing.

---

# 📊 PART 16 — CREATE A BASELINE

Record:

| Test | Normal Result |
|---|---|
| Employee Gateway | Reachable |
| Server Gateway | Reachable |
| Server IP | Reachable |
| DNS | Resolves |
| HTTP | Loads |
| WAN Router | Reachable |
| Employee DHCP | Working |
| Guest DHCP | Working |

This becomes your:

> **Baseline**

---

# 📸 Save Your Working Network

Before intentionally breaking anything:

> **Save the Packet Tracer file.**

Suggested name:

```text
lab-20-working-baseline.pkt
```

Now you have a known-good configuration.

---

# 🔐 PART 17 — BASIC SEGMENTATION

Guests should not have normal access to the server network.

Conceptually:

```text
GUEST VLAN 50
      │
      X
      │
SERVER VLAN 20
```

while employees should be able to reach required services.

---

# 📋 PART 18 — APPLY AN ACL

Create a simplified ACL on R-01.

Example concept:

```text
configure terminal

ip access-list extended GUEST_FILTER

 deny ip 192.168.50.0 0.0.0.255 192.168.20.0 0.0.0.255

 permit ip 192.168.50.0 0.0.0.255 any

exit
```

Apply it inbound to the guest subinterface:

```text
interface g0/0.50
 ip access-group GUEST_FILTER in

end
```

---

# 🧪 PART 19 — VERIFY SEGMENTATION

From GUEST-01:

Try:

```text
ping 192.168.20.10
```

Expected:

> **Blocked**

Employee access should remain operational.

---

# ⚠️ Packet Tracer Note

Because the lab DNS server is also inside VLAN 20, blocking all guest access to VLAN 20 means guests cannot use that DNS server.

That is intentional for this simplified security exercise.

A production design would normally provide guests with an appropriate DNS service that does not require broad access to protected server resources.

---

# 🔒 PART 20 — SECURE UNUSED PORTS

Choose unused switch ports.

Example:

```text
configure terminal

interface range fa0/10-24
 shutdown

end
```

Verify:

```text
show interfaces status
```

if supported.

---

# 💾 PART 21 — SAVE CONFIGURATION

On network devices:

```text
copy running-config startup-config
```

This is part of good configuration management.

---

# 💥 TROUBLESHOOTING BEGINS

For each failure:

1. Observe symptoms
2. Determine scope
3. Establish a theory
4. Test it
5. Repair the issue
6. Verify
7. Document

---

# 💥 INCIDENT 1 — PHYSICAL FAILURE

Disconnect PC-EMP1 from SW-01.

Symptom:

```text
PC-EMP1
No Connectivity
```

PC-EMP2 still works.

---

# 🧠 Scope

```text
One Device
```

Check Layer:

> **Layer 1**

---

# 🔧 Repair

Reconnect the cable.

Verify:

```text
ping 192.168.10.1
```

---

# 💥 INCIDENT 2 — WRONG VLAN

Move PC-EMP1's switch port from VLAN 10 to VLAN 50.

---

# 🔍 Symptoms

PC-EMP1 may receive:

```text
192.168.50.x
```

instead of:

```text
192.168.10.x
```

---

# 🧰 Investigate

Run:

```text
show vlan brief
```

Check the switch port assignment.

---

# 🔧 Repair

Return the port to:

```text
VLAN 10
```

Renew DHCP if necessary.

---

# 💥 INCIDENT 3 — DHCP FAILURE

Remove or incorrectly configure:

```text
ip dhcp pool EMPLOYEES
```

Then renew PC-EMP1.

---

# 🔍 Symptoms

The client fails to obtain the expected:

```text
192.168.10.x
```

configuration.

---

# 🧰 Investigate

Check:

```text
show running-config
```

and DHCP configuration.

---

# 🔧 Repair

Restore the correct DHCP pool.

Verify:

```text
IP Address

Gateway

DNS
```

---

# 💥 INCIDENT 4 — DNS FAILURE

Change the DNS record for:

```text
intranet.northstar.local
```

to an incorrect IP.

---

# 🔍 Symptoms

Server IP:

```text
192.168.20.10
```

works.

Name:

```text
intranet.northstar.local
```

fails or reaches the wrong destination.

---

# 🧠 Theory

> **DNS**

---

# 🔧 Repair

Restore:

```text
intranet.northstar.local
        ↓
192.168.20.10
```

Verify name-based access.

---

# 💥 INCIDENT 5 — ROUTING FAILURE

Remove or disable the VLAN 20 router subinterface.

---

# 🔍 Symptoms

Employees may still reach:

```text
192.168.10.1
```

but cannot reach:

```text
192.168.20.10
```

---

# 🧰 Investigate

Run:

```text
show ip interface brief
```

and:

```text
show ip route
```

---

# 🔧 Repair

Restore the VLAN 20 interface.

Retest.

---

# 💥 INCIDENT 6 — TRUNK FAILURE

Change the switch/router connection so it no longer operates correctly as the required trunk.

---

# 🔍 Scope

Potentially:

```text
Multiple VLANs
```

are affected.

---

# 🧰 Investigate

Use:

```text
show interfaces trunk
```

and:

```text
show vlan brief
```

---

# 🔧 Repair

Restore the trunk configuration.

---

# 💥 INCIDENT 7 — WAN FAILURE

Shut down R-01's WAN interface.

---

# 🔍 Symptoms

Local services may still work:

```text
Employee → Server
✓
```

but WAN access fails.

---

# ⭐ Important

This proves:

```text
WAN Down
```

does not automatically mean:

```text
LAN Down
```

---

# 🔧 Repair

Restore the WAN interface.

---

# 💥 INCIDENT 8 — SECURITY FAILURE

Remove:

```text
GUEST_FILTER
```

from the guest interface.

---

# 🔍 Test

Can GUEST-01 now reach:

```text
192.168.20.10
```

?

If yes, a security control has failed.

---

# 🧠 Important

Connectivity can be:

```text
Working
```

while security is:

```text
Broken
```

Troubleshooting includes verifying that systems behave:

> **As intended**

not merely that packets can travel.

---

# 🔧 Repair

Restore the ACL.

Retest.

---

# 📊 PART 22 — MONITORING EXERCISE

Imagine your monitoring platform reports:

```text
09:01
R-01 WAN latency:
18 ms

09:05
R-01 WAN latency:
95 ms

09:07
Packet loss:
8%

09:08
VPN users report disconnects
```

---

# 🧠 Questions

What changed from baseline?

> **Latency increased and packet loss appeared.**

What might you investigate?

```text
WAN Congestion

ISP Problems

Interface Errors

Provider Path

Firewall Load
```

---

# 📝 PART 23 — SYSLOG EXERCISE

Imagine these messages:

```text
09:14:02
R-01 WAN interface DOWN

09:14:04
VPN tunnel disconnected

09:14:06
Remote monitoring failed

09:15:10
First user calls Help Desk
```

---

# 🧠 What Happened First?

> **The WAN interface went down.**

Logs help establish the timeline.

---

# 🚨 PART 24 — ALERT DESIGN

Which of these deserve alerts?

```text
Core Router Down

WAN Link Down

Critical Switch Down

Packet Loss Above Threshold

Firewall CPU Critical
```

Usually:

> **All could justify alerts depending on organizational requirements and thresholds.**

---

# 🧠 Should Every Port Down Generate an Emergency?

No.

A user unplugging a laptop should not necessarily generate the same alert severity as:

```text
Core Switch Down
```

Monitoring needs meaningful priorities.

---

# 📝 PART 25 — INCIDENT REPORT

Document one of your failures:

```text
INCIDENT:

________________________________


DATE/TIME:

________________________________


USERS AFFECTED:

________________________________


SCOPE:

________________________________


SYMPTOMS:

________________________________


BASELINE:

________________________________


THEORY:

________________________________


TESTS PERFORMED:

________________________________


ROOT CAUSE:

________________________________


SOLUTION:

________________________________


VERIFICATION:

________________________________


PREVENTION:

________________________________
```

---

# 🧗 PART 26 — ESCALATION EXERCISE

Scenario:

```text
Entire Office:
No Internet

LAN:
Working

Gateway:
Working

Firewall:
Working

WAN Interface:
Up

ISP Next Hop:
Unreachable
```

You do not administer the ISP network.

What should happen?

> **Escalate to the ISP/provider with your troubleshooting evidence.**

---

# 📝 Example Escalation Notes

```text
Site:
Northstar HQ

Impact:
Entire office Internet outage

LAN:
Operational

Firewall:
Operational

WAN Interface:
Up

ISP Next Hop:
Unreachable

Started:
09:14

Local Changes:
None known

Requested Action:
Provider circuit investigation
```

---

# 🧠 PART 27 — FINAL MYSTERY INCIDENT

Do not look for the answer until you troubleshoot it.

Symptoms:

```text
PC-EMP1:
Cannot open intranet.northstar.local

PC-EMP2:
Cannot open intranet.northstar.local

Both PCs:
Receive correct DHCP

Both PCs:
Can ping 192.168.10.1

Both PCs:
Can ping 192.168.20.10

SERVER-01:
HTTP enabled
```

What should you test next?

---

# 🔍 Test

Check:

> **DNS**

---

# ✅ Likely Cause

If IP connectivity works but hostname resolution fails:

> **DNS configuration or the DNS record**

is the likely area.

---

# 🏆 FINAL LAB CHALLENGE

Restore the entire network to:

```text
EMPLOYEES
    ↓
DHCP
    ↓
Gateway
    ↓
DNS
    ↓
SERVER
    ↓
WAN
```

with:

```text
GUEST
  ↓
Blocked from protected Server VLAN
```

Verify every expected behavior.

---

# 📋 FINAL VERIFICATION TABLE

| Test | Expected | Result |
|---|---|---|
| PC-EMP1 DHCP | Works | |
| PC-EMP2 DHCP | Works | |
| Employee Gateway | Reachable | |
| Server | Reachable | |
| DNS | Works | |
| HTTP | Works | |
| WAN | Reachable | |
| Guest DHCP | Works | |
| Guest → Server | Blocked | |
| Unused Ports | Disabled | |

---

# 🏆 LAB COMPLETION CHECKLIST

- [ ] I created VLANs
- [ ] I configured access ports
- [ ] I configured a trunk
- [ ] I configured inter-VLAN routing
- [ ] I configured DHCP
- [ ] I configured DNS
- [ ] I configured a server
- [ ] I configured a WAN
- [ ] I established a working baseline
- [ ] I applied guest segmentation
- [ ] I configured an ACL
- [ ] I disabled unused ports
- [ ] I saved configurations
- [ ] I troubleshot Layer 1
- [ ] I troubleshot VLAN assignment
- [ ] I troubleshot DHCP
- [ ] I troubleshot DNS
- [ ] I troubleshot routing
- [ ] I troubleshot trunking
- [ ] I troubleshot WAN connectivity
- [ ] I troubleshot a security failure
- [ ] I analyzed monitoring data
- [ ] I analyzed logs
- [ ] I created an incident report
- [ ] I practiced escalation
- [ ] I completed the mystery incident
- [ ] I verified the final network

---

# 🏁 Lab 20 Complete

You have completed all guided Networking Fundamentals labs.

You can now troubleshoot:

```text
Physical
   ↓
Switching
   ↓
VLAN
   ↓
IP Addressing
   ↓
DHCP
   ↓
Routing
   ↓
DNS
   ↓
Wireless
   ↓
WAN
   ↓
Security
   ↓
Application
```

The final step is to prove you can put it all together without being given every command.

---

# 🏆 NEXT — PROJECT 04

Continue to:

> **Project 04 — Small Business Network Capstone**

This time:

> **You get the requirements. You design the solution.**

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**