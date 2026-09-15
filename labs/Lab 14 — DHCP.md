# 🧪 Lab 14 — DHCP

Welcome to **Lab 14 of Networking Fundamentals**.

In this lab, you'll stop manually configuring every client IP address.

You'll build a DHCP environment that automatically provides:

```text
IP Address
Subnet Mask
Default Gateway
DNS Server
```

Then you'll move the DHCP server to another network and discover an important problem:

> **DHCP broadcasts don't automatically cross routers.**

You'll solve that using:

> **DHCP Relay**

---

# 🎯 Lab Objectives

By the end of this lab, you should be able to:

- Configure a DHCP server
- Create a DHCP pool
- Configure DHCP clients
- Verify leased addresses
- Observe DHCP traffic
- Identify DORA
- Configure multiple DHCP scopes
- Configure DHCP relay
- Use `ip helper-address`
- Verify client gateways and DNS
- Troubleshoot missing DHCP
- Troubleshoot incorrect scope settings
- Troubleshoot DHCP relay
- Recognize APIPA
- Troubleshoot scope exhaustion

---

# 🎓 Network+ Focus

This lab reinforces:

- DHCP
- UDP 67/68
- DORA
- Scopes
- Address pools
- Leases
- Default gateway options
- DNS options
- DHCP relay
- APIPA
- Troubleshooting

---

# ⏱️ Estimated Time

**75–90 minutes**

---

# 🏗️ PART 1 — BUILD A SIMPLE DHCP NETWORK

Open:

> **Cisco Packet Tracer**

Add:

```text
PC-01
PC-02
PC-03
SW-01
DHCP-01
R-01
```

Build:

```text
PC-01 ─┐
       │
PC-02 ─┼── SW-01 ─── R-01
       │
PC-03 ─┤
       │
DHCP-01┘
```

---

# 🌐 PART 2 — NETWORK PLAN

Use:

```text
Employee Network
192.168.10.0/24
```

Router:

```text
192.168.10.1
```

DHCP server:

```text
192.168.10.10
```

DHCP clients:

```text
192.168.10.100+
```

---

# 📋 Addressing Plan

| Device | Address |
|---|---|
| R-01 | 192.168.10.1/24 |
| DHCP-01 | 192.168.10.10/24 |
| PC-01 | DHCP |
| PC-02 | DHCP |
| PC-03 | DHCP |

---

# 🔀 PART 3 — CONFIGURE R-01

On R-01:

```text
enable
```

Then:

```text
configure terminal
```

Rename:

```text
hostname R-01
```

Configure the interface toward SW-01.

Example:

```text
interface gigabitethernet 0/0
```

Then:

```text
ip address 192.168.10.1 255.255.255.0
```

Enable it:

```text
no shutdown
```

Then:

```text
end
```

---

# 🔍 Verify

Run:

```text
show ip interface brief
```

Make sure the LAN interface is:

```text
up
up
```

---

# 🗄️ PART 4 — CONFIGURE DHCP-01 STATIC ADDRESS

Open DHCP-01.

Go to:

```text
Desktop
    ↓
IP Configuration
```

Configure:

```text
IP Address:
192.168.10.10

Subnet Mask:
255.255.255.0

Default Gateway:
192.168.10.1
```

For this lab, you can use:

```text
DNS Server:
192.168.10.10
```

We'll focus deeply on DNS in Lesson 15.

---

# 🧪 Test the Server

From DHCP-01:

```text
ping 192.168.10.1
```

Expected:

> **Success**

---

# 📦 PART 5 — CREATE THE DHCP POOL

Open DHCP-01.

Go to:

```text
Services
    ↓
DHCP
```

Turn DHCP:

> **On**

Create a pool.

---

# 📋 Employee DHCP Pool

Use:

```text
Pool Name:
EMPLOYEES
```

Default Gateway:

```text
192.168.10.1
```

DNS Server:

```text
192.168.10.10
```

Starting IP Address:

```text
192.168.10.100
```

Subnet Mask:

```text
255.255.255.0
```

Maximum Number of Users:

```text
50
```

Then:

> **Add / Save the pool**

depending on your Packet Tracer version.

---

# 🧠 What Addresses Can Be Assigned?

Starting at:

```text
192.168.10.100
```

with:

```text
50 clients
```

the pool can provide addresses through approximately:

```text
192.168.10.149
```

---

# 🖥️ PART 6 — CONFIGURE PC-01 FOR DHCP

Open PC-01.

Go to:

```text
Desktop
    ↓
IP Configuration
```

Select:

> **DHCP**

Wait for configuration.

Record:

```text
IP Address:

____________________________


Subnet Mask:

____________________________


Default Gateway:

____________________________


DNS Server:

____________________________
```

---

# ⭐ Expected

PC-01 should receive something similar to:

```text
IP:
192.168.10.100

Mask:
255.255.255.0

Gateway:
192.168.10.1

DNS:
192.168.10.10
```

The exact leased address may vary.

---

# 🖥️ PART 7 — CONFIGURE THE OTHER CLIENTS

Set:

```text
PC-02
```

to:

> **DHCP**

Then:

```text
PC-03
```

to:

> **DHCP**

Record their addresses.

| Client | IPv4 | Gateway |
|---|---|---|
| PC-01 | | |
| PC-02 | | |
| PC-03 | | |

---

# 🧪 PART 8 — TEST CONNECTIVITY

From PC-01:

```text
ping 192.168.10.1
```

Then ping PC-02's leased address.

Then:

```text
ping 192.168.10.10
```

Expected:

> **Success**

---

# 🔬 PART 9 — OBSERVE DORA

We want to observe DHCP itself.

Switch Packet Tracer to:

> **Simulation Mode**

Filter for DHCP traffic if your Packet Tracer version allows it.

---

# 🔄 Force a New DHCP Request

Choose one client.

Temporarily switch it from:

```text
DHCP
```

to:

```text
Static
```

Then switch back to:

```text
DHCP
```

This should trigger DHCP activity.

---

# 🔍 Observe

Look for the DHCP sequence.

Conceptually:

```text
CLIENT
   │
   │ DHCP Discover
   ▼
SERVER
   │
   │ DHCP Offer
   ▼
CLIENT
   │
   │ DHCP Request
   ▼
SERVER
   │
   │ DHCP ACK
   ▼
CLIENT CONFIGURED
```

---

# 📝 PART 10 — DOCUMENT DORA

Complete:

```text
Step 1:

____________________________


Step 2:

____________________________


Step 3:

____________________________


Step 4:

____________________________
```

Answers:

```text
Discover
Offer
Request
Acknowledge
```

---

# 📡 PART 11 — DHCP PORTS

Record:

```text
DHCP Server Port:

UDP ______


DHCP Client Port:

UDP ______
```

Answers:

```text
Server:
UDP 67

Client:
UDP 68
```

---

# 💥 PART 12 — BREAK THE DHCP SERVICE

On DHCP-01:

```text
Services
    ↓
DHCP
```

Turn DHCP:

> **Off**

Now add:

```text
PC-04
```

to SW-01.

Set PC-04 to:

> **DHCP**

---

# ❓ What Happens?

Record:

```text
Did PC-04 receive normal DHCP configuration?

YES / NO


Address received:

____________________________
```

Depending on Packet Tracer behavior, the client may show a DHCP failure or automatic fallback behavior.

In real Windows environments, failed DHCP commonly leads to:

```text
169.254.x.x
```

APIPA.

---

# 🔧 Repair

Turn DHCP back:

> **On**

Request DHCP again.

Verify PC-04 receives a valid:

```text
192.168.10.x
```

address.

---

# 🌐 PART 13 — BUILD A SECOND NETWORK

Now we'll move beyond local DHCP.

Add:

```text
SW-02
PC-REMOTE
```

Connect them to another R-01 interface.

Topology:

```text
EMPLOYEE NETWORK
192.168.10.0/24

PC-01 ─┐
PC-02 ─┤
       SW-01
DHCP-01┘
          │
          ▼
         R-01
          │
          ▼
        SW-02
          │
          ▼
      PC-REMOTE

REMOTE NETWORK
192.168.20.0/24
```

---

# 🔀 PART 14 — CONFIGURE R-01 REMOTE INTERFACE

On R-01:

```text
configure terminal
```

Select the interface connected to SW-02.

Example:

```text
interface gigabitethernet 0/1
```

Configure:

```text
ip address 192.168.20.1 255.255.255.0
```

Then:

```text
no shutdown
```

Then:

```text
end
```

---

# 🔍 Verify

Run:

```text
show ip interface brief
```

You should now have:

```text
192.168.10.1
```

and:

```text
192.168.20.1
```

on active router interfaces.

---

# 📦 PART 15 — CREATE A SECOND DHCP POOL

On DHCP-01:

```text
Services
    ↓
DHCP
```

Create:

```text
Pool Name:
REMOTE
```

Default Gateway:

```text
192.168.20.1
```

DNS Server:

```text
192.168.10.10
```

Starting IP:

```text
192.168.20.100
```

Subnet Mask:

```text
255.255.255.0
```

Maximum Users:

```text
50
```

Save the pool.

---

# 🖥️ PART 16 — REQUEST DHCP FROM PC-REMOTE

Set PC-REMOTE to:

> **DHCP**

Does it receive:

```text
192.168.20.x
```

?

At this stage, it should:

> **Fail**

if no DHCP relay has been configured.

---

# 🧠 Why Did It Fail?

PC-REMOTE sends a local DHCP broadcast.

```text
PC-REMOTE
     ↓
DHCP Discover
     ↓
SW-02
     ↓
R-01
```

But DHCP-01 is on:

```text
192.168.10.0/24
```

The client is on:

```text
192.168.20.0/24
```

Routers don't simply forward the client's Layer 2 broadcast into another subnet.

---

# 🌉 PART 17 — CONFIGURE DHCP RELAY

On R-01, enter the interface facing:

```text
192.168.20.0/24
```

Example:

```text
configure terminal
```

```text
interface gigabitethernet 0/1
```

Configure:

```text
ip helper-address 192.168.10.10
```

Then:

```text
end
```

---

# ⭐ Important

The helper is configured on:

> **The interface receiving the client DHCP broadcast.**

In this topology:

```text
PC-REMOTE
     ↓
SW-02
     ↓
R-01 G0/1
```

Therefore:

```text
G0/1
```

needs the helper.

---

# 🔍 PART 18 — VERIFY THE HELPER

Run:

```text
show running-config
```

Find the remote-facing interface.

You should see:

```text
ip helper-address 192.168.10.10
```

---

# 🔄 PART 19 — REQUEST DHCP AGAIN

On PC-REMOTE:

Select:

> **DHCP**

again.

It should now receive something similar to:

```text
IP:
192.168.20.100

Mask:
255.255.255.0

Gateway:
192.168.20.1

DNS:
192.168.10.10
```

---

# 🏆 Major Checkpoint

You've now created:

```text
PC-REMOTE
192.168.20.x
      │
      ▼
DHCP Broadcast
      │
      ▼
R-01
DHCP RELAY
      │
      ▼
192.168.10.10
DHCP-01
```

The DHCP server is:

> **Not on the client's subnet**

but DHCP still works because of:

> **DHCP Relay**

---

# 🧪 PART 20 — TEST ROUTING

From PC-REMOTE:

```text
ping 192.168.20.1
```

Then:

```text
ping 192.168.10.10
```

Expected:

> **Success**

This proves the client received useful configuration and routing is functioning.

---

# 🔬 PART 21 — OBSERVE RELAY IN SIMULATION MODE

Switch to:

> **Simulation Mode**

Force PC-REMOTE to request DHCP again.

Observe:

```text
PC-REMOTE
     ↓
SW-02
     ↓
R-01
     ↓
DHCP-01
```

Look at how the router participates in the process.

The important concept is:

> The router is relaying DHCP communication between different IP networks.

---

# 💥 PART 22 — BREAK THE HELPER ADDRESS

On R-01, enter the remote interface.

Remove:

```text
ip helper-address 192.168.10.10
```

using:

```text
no ip helper-address 192.168.10.10
```

---

# 🧪 Test

Force PC-REMOTE to request DHCP again.

What happens?

```text
________________________________
```

---

# 🔍 Diagnose

Ask:

```text
Does the client have link?
        ↓
Is the switch working?
        ↓
Is the router interface up?
        ↓
Is the DHCP server running?
        ↓
Does a 192.168.20.0/24 scope exist?
        ↓
Is DHCP relay configured?
```

---

# 🔧 Repair

Restore:

```text
ip helper-address 192.168.10.10
```

Retest.

---

# 💥 PART 23 — WRONG HELPER ADDRESS

Now intentionally change the helper to:

```text
192.168.10.99
```

instead of:

```text
192.168.10.10
```

Force PC-REMOTE to request DHCP.

Expected:

> **Failure**

---

# 🔍 Investigate

Use:

```text
show running-config
```

Find:

```text
ip helper-address
```

Identify the incorrect DHCP server address.

---

# 🔧 Repair

Restore:

```text
ip helper-address 192.168.10.10
```

---

# 💥 PART 24 — WRONG GATEWAY OPTION

On the REMOTE DHCP pool, intentionally change:

```text
Default Gateway
```

from:

```text
192.168.20.1
```

to:

```text
192.168.20.254
```

Request new DHCP configuration on PC-REMOTE.

---

# 🧪 Test

Try:

```text
ping 192.168.20.1
```

Then:

```text
ping 192.168.10.10
```

---

# 🧠 Expected Pattern

PC-REMOTE may reach devices in:

```text
192.168.20.0/24
```

but remote-network communication will fail because its gateway is wrong.

This is a:

> **DHCP configuration problem**

even though DHCP successfully assigned an address.

---

# 🔧 Repair

Restore:

```text
Default Gateway:
192.168.20.1
```

Renew/re-request DHCP configuration.

---

# 💥 PART 25 — WRONG SUBNET SCOPE

Imagine the REMOTE scope is accidentally configured to provide:

```text
192.168.30.100
```

to clients physically connected to:

```text
192.168.20.0/24
```

What problem would this create?

> The client receives an address for the wrong IP subnet.

This is an important lesson:

> **Receiving an address from DHCP does not prove the DHCP configuration is correct.**

Always verify:

```text
IP
Mask
Gateway
DNS
```

---

# 💥 PART 26 — SCOPE EXHAUSTION

Create a temporary test pool or modify the lab pool so only a very small number of addresses are available.

For example:

```text
Starting Address:
192.168.20.100

Maximum Users:
2
```

Connect/request DHCP from more clients than the pool supports.

---

# 🧠 Observe

Possible pattern:

```text
Client 1
✅ Address

Client 2
✅ Address

Client 3
❌ No Available Lease
```

This demonstrates:

> **DHCP Scope Exhaustion**

---

# 🔧 Repair

Increase the number of available addresses.

Then request DHCP again.

---

# 🛠️ PART 27 — TROUBLESHOOT BY SCOPE

Suppose:

```text
PC-01
192.168.10.x
DHCP works
```

but:

```text
PC-REMOTE
192.168.20.x
DHCP fails
```

What can you infer?

Probably:

> **The entire DHCP server isn't simply offline.**

Focus on what's different:

```text
Remote Scope
DHCP Relay
Remote VLAN/Subnet
Routing
Remote Interface
```

This is:

> **Troubleshooting by scope**

---

# 🖥️ PART 28 — WINDOWS DHCP INSPECTION

On a Windows computer where you have permission to inspect configuration:

```text
ipconfig /all
```

Look for:

```text
DHCP Enabled
DHCP Server
IPv4 Address
Subnet Mask
Default Gateway
DNS Servers
Lease Obtained
Lease Expires
```

---

# ⚡ PowerShell

Run:

```text
Get-NetIPConfiguration
```

Then:

```text
Get-NetIPAddress -AddressFamily IPv4
```

Compare the information.

---

# ⚠️ Optional Release/Renew

Only on a test system or where you understand the impact:

```text
ipconfig /release
```

Then:

```text
ipconfig /renew
```

Do not intentionally disconnect a production user just to complete the lab.

Packet Tracer already provides a safe environment for DHCP failure testing.

---

# 📋 PART 29 — DOCUMENT THE DHCP ENVIRONMENT

Complete:

## Employee Scope

```text
Network:

____________________________

Starting Address:

____________________________

Gateway:

____________________________

DNS:

____________________________
```

## Remote Scope

```text
Network:

____________________________

Starting Address:

____________________________

Gateway:

____________________________

DNS:

____________________________
```

## DHCP Server

```text
IP Address:

____________________________
```

## DHCP Relay

```text
Router:

____________________________

Client-Facing Interface:

____________________________

Helper Address:

____________________________
```

---

# 🛠️ PART 30 — FINAL TROUBLESHOOTING CHALLENGE

A user on the Remote network reports:

> "My computer won't get on the network."

You find:

```text
IPv4:
169.254.22.51
```

You are not told what's wrong.

Troubleshoot:

```text
Physical Link
      ↓
Switch Port
      ↓
Correct Network/VLAN
      ↓
Router Interface
      ↓
DHCP Relay
      ↓
Routing
      ↓
DHCP Server
      ↓
Correct Scope
      ↓
Available Addresses
```

Document:

```text
Problem:

________________________________


Client Address:

________________________________


Link Working?

YES / NO


Correct VLAN/Subnet?

YES / NO


Router Interface Up?

YES / NO


Helper Configured?

YES / NO


Correct Helper Address?

YES / NO


Correct Scope Exists?

YES / NO


Addresses Available?

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

What does DHCP stand for?

### 2.

What does DORA stand for?

### 3.

Which transport protocol does DHCP use?

### 4.

Which UDP port does the DHCP server use?

### 5.

Which UDP port does the DHCP client use?

### 6.

What is a DHCP scope?

### 7.

What is a reservation?

### 8.

What does a 169.254.x.x address commonly indicate?

### 9.

Why was DHCP relay needed in this lab?

### 10.

What Cisco command configured the relay?

---

# ✅ Answers

1. **Dynamic Host Configuration Protocol**
2. **Discover, Offer, Request, Acknowledge**
3. **UDP**
4. **67**
5. **68**
6. **A DHCP configuration/address pool associated with a subnet**
7. **A predictable DHCP assignment associated with a particular client**
8. **Normal DHCP configuration was not obtained**
9. **The DHCP server was on a different routed subnet**
10. **`ip helper-address`**

---

# 🎓 Network+ Challenge 1

A client receives:

```text
169.254.15.20
```

Which service should be investigated?

> **DHCP**

---

# 🎓 Network+ Challenge 2

Clients on VLAN 10 receive DHCP.

Clients on VLAN 20 do not.

The DHCP server is on VLAN 10.

What should you check on VLAN 20's Layer 3 interface?

> **DHCP relay / helper configuration**

---

# 🎓 Network+ Challenge 3

DHCP successfully gives a client:

```text
192.168.20.100/24
```

but assigns gateway:

```text
192.168.20.254
```

instead of:

```text
192.168.20.1
```

Where is the likely problem?

> **DHCP scope configuration**

---

# 🎓 Network+ Challenge 4

Existing clients work, but additional clients cannot obtain addresses.

What should you check?

> **Available addresses in the DHCP pool**

---

# 🎓 Network+ Challenge 5

Which DORA message is sent first?

> **DHCP Discover**

---

# 🎓 Network+ Challenge 6

Which DORA message confirms the client's lease?

> **DHCP Acknowledge / ACK**

---

# 📋 Lab Review

In this lab, you:

- Built a DHCP server
- Created a DHCP scope
- Configured DHCP clients
- Automatically assigned IPv4 configuration
- Verified gateways and DNS
- Observed DORA
- Reviewed UDP ports 67 and 68
- Broke the DHCP service
- Recognized APIPA behavior
- Built a second routed subnet
- Created a second DHCP pool
- Demonstrated why broadcasts don't cross routers
- Configured DHCP relay
- Used `ip helper-address`
- Assigned DHCP across a routed boundary
- Troubleshot a missing helper
- Troubleshot an incorrect helper
- Troubleshot a wrong gateway option
- Examined wrong-subnet configuration
- Simulated scope exhaustion
- Practiced troubleshooting by scope
- Inspected Windows DHCP configuration

---

# 💾 Save Your Packet Tracer Lab

Save as:

```text
lab-14-dhcp.pkt
```

You don't need to upload the completed `.pkt` file to the public repository.

Building and troubleshooting DHCP yourself is part of the exercise.

---

# 🏆 Lab Complete

You can now follow DHCP from:

```text
NEW CLIENT
     ↓
DISCOVER
     ↓
OFFER
     ↓
REQUEST
     ↓
ACK
     ↓
IP CONFIGURATION
```

and across a routed network:

```text
CLIENT
     ↓
DHCP BROADCAST
     ↓
ROUTER
DHCP RELAY
     ↓
DHCP SERVER
     ↓
CORRECT SCOPE
     ↓
LEASE
```

More importantly, when you see:

```text
169.254.x.x
```

you now have a troubleshooting path instead of simply saying:

> "The network doesn't work."

---

# 📍 Course Progress

```text
🟢 PHASE 1 — NETWORKING FOUNDATIONS
✅ COMPLETE

🔵 PHASE 2 — ADDRESSING & COMMUNICATION
✅ COMPLETE

🟣 PHASE 3 — SWITCHING, ROUTING & SERVICES

✅ Lesson 11 — Switching Fundamentals
✅ Lab 11

✅ Lesson 12 — VLANs & Network Segmentation
✅ Lab 12

✅ Lesson 13 — Routing Fundamentals
✅ Lab 13

✅ Lesson 14 — DHCP
✅ Lab 14

        ↓

🟡 NEXT:
Lesson 15 — DNS

⬜ Lab 15 — DNS

        ↓

⬜ Lesson 16 — NAT & Address Translation
⬜ Lab 16

        ↓

🏗️ Project 03
Build a Routed Small-Business Network
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 15 — DNS**

DHCP gave our clients settings such as:

```text
IP Address
Subnet Mask
Default Gateway
DNS Server
```

But why does the client need a DNS server?

Because people prefer:

```text
server.company.local
```

or:

```text
www.example.com
```

instead of remembering:

```text
192.168.20.10
```

Next we'll cover:

- DNS
- Names vs. IP addresses
- DNS clients and resolvers
- DNS servers
- DNS hierarchy
- Root servers
- TLD servers
- Authoritative servers
- Recursive queries
- DNS caching
- A records
- AAAA records
- CNAME records
- MX records
- PTR records
- NS records
- TXT records
- DNS UDP/TCP 53
- `nslookup`
- `Resolve-DnsName`
- DNS troubleshooting
- Packet Tracer DNS services

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**