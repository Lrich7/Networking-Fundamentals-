# 🧪 Lab 18 — Wireless Networking

Welcome to **Lab 18 of Networking Fundamentals**.

This lab combines:

```text
Your Real Windows Computer
+
Wireless Observation
+
Packet Tracer
+
Troubleshooting
```

The first part lets you inspect an actual wireless connection.

The second part uses Packet Tracer to build and intentionally break a wireless network.

---

# 🎯 Lab Objectives

You will:

- Identify your wireless adapter
- Identify your current SSID
- Identify BSSID
- Identify wireless channel
- Identify radio type
- Inspect signal strength
- Observe nearby wireless networks
- Compare 2.4 GHz and 5 GHz behavior
- Build a Packet Tracer wireless network
- Configure an SSID
- Configure wireless security
- Connect clients
- Verify DHCP
- Create corporate and guest wireless
- Troubleshoot incorrect passwords
- Troubleshoot DHCP failures
- Troubleshoot AP/uplink failures
- Analyze wireless support scenarios

---

# ⏱️ Estimated Time

**75–90 minutes**

---

# 🧰 Tools

Use:

- Windows computer
- Command Prompt or PowerShell
- Cisco Packet Tracer

For the Windows observation sections, use only wireless information normally visible to your own device.

---

# 💻 PART 1 — IDENTIFY YOUR NETWORK ADAPTER

Open PowerShell.

Run:

```text
Get-NetAdapter
```

Look for your wireless adapter.

It may have a name such as:

```text
Wi-Fi
```

Record:

```text
Adapter Name:

____________________________


Status:

____________________________


Link Speed:

____________________________
```

---

# 📡 PART 2 — INSPECT YOUR WI-FI CONNECTION

Run:

```text
netsh wlan show interfaces
```

Look for information such as:

```text
SSID

BSSID

Radio type

Channel

Receive rate

Transmit rate

Signal
```

---

# 📝 Record Your Results

```text
SSID:

____________________________


BSSID:

____________________________


Radio Type:

____________________________


Channel:

____________________________


Signal:

____________________________


Receive Rate:

____________________________


Transmit Rate:

____________________________
```

---

# 🧠 PART 3 — SSID VS. BSSID

Using your output, answer:

```text
SSID identifies:

________________________________


BSSID identifies:

________________________________
```

---

# ✅ Answer

```text
SSID:
The wireless network

BSSID:
The specific AP/radio connection
```

---

# 📻 PART 4 — IDENTIFY THE BAND

Use the channel shown by:

```text
netsh wlan show interfaces
```

Determine whether your current connection is likely using:

```text
2.4 GHz

5 GHz

6 GHz
```

Record:

```text
Current Band:

____________________________
```

---

# 🧠 Helpful Clue

Common U.S. 2.4 GHz Wi-Fi channels include:

```text
1–11
```

5 GHz and 6 GHz use different channel arrangements.

Do not rely on channel number alone if your system provides explicit band/frequency information.

---

# 📡 PART 5 — OBSERVE VISIBLE NETWORKS

Run:

```text
netsh wlan show networks mode=bssid
```

Look through the wireless networks your computer can normally see.

Do not attempt to connect to networks you are not authorized to use.

---

# 📝 Record Three Observations

Do not record someone else's password or sensitive information.

Record:

```text
Network 1:

SSID:
____________________________

Channel:
____________________________

Signal:
____________________________


Network 2:

SSID:
____________________________

Channel:
____________________________

Signal:
____________________________


Network 3:

SSID:
____________________________

Channel:
____________________________

Signal:
____________________________
```

---

# 🔍 PART 6 — LOOK FOR CHANNEL USE

If you can see multiple 2.4 GHz networks, look at their channels.

Do you see:

```text
Channel 1?

Channel 6?

Channel 11?
```

Record:

```text
________________________________

________________________________
```

---

# 🧠 Question

Why would several nearby networks using overlapping 2.4 GHz channel space potentially cause problems?

> **They compete for limited radio spectrum and may interfere or create additional contention.**

---

# 📶 PART 7 — SIGNAL STRENGTH TEST

If practical, remain connected to your authorized Wi-Fi network and observe signal strength from two locations.

Example:

```text
Near AP
vs.
Farther Away
```

Run:

```text
netsh wlan show interfaces
```

in each location.

Do not move equipment or enter restricted areas just for this lab.

---

# 📝 Record

```text
Location 1:

____________________________

Signal:

____________________________


Location 2:

____________________________

Signal:

____________________________
```

---

# 🧠 Observation

Did signal strength:

```text
Increase

Decrease

Stay Similar
```

as you moved?

Explain:

```text
________________________________

________________________________
```

---

# 🏗️ PART 8 — OPEN PACKET TRACER

Now we'll build a wireless network.

Create:

```text
                    R-01
                      │
                      ▼
                    SW-01
                   /     \
                  /       \
              AP-01      SERVER-01
               )))
             )))
       LAPTOP-01
       LAPTOP-02
```

---

# 🌐 PART 9 — ADDRESSING PLAN

Use:

```text
192.168.10.0/24
```

Gateway:

```text
192.168.10.1
```

Server:

```text
192.168.10.10
```

Wireless clients:

> **DHCP**

---

# 🛣️ PART 10 — CONFIGURE R-01

Configure the LAN interface:

```text
enable
configure terminal

interface g0/0
 ip address 192.168.10.1 255.255.255.0
 no shutdown

end
```

Use the actual connected interface on your router.

---

# 📦 PART 11 — CONFIGURE DHCP

You can use either a Packet Tracer server or router DHCP depending on the available devices.

For this lab, configure DHCP on R-01.

Exclude infrastructure addresses:

```text
configure terminal

ip dhcp excluded-address 192.168.10.1 192.168.10.20
```

Create:

```text
ip dhcp pool WIRELESS
 network 192.168.10.0 255.255.255.0
 default-router 192.168.10.1
 dns-server 192.168.10.10

end
```

---

# 🖥️ PART 12 — CONFIGURE SERVER-01

Configure:

```text
IP:
192.168.10.10

Mask:
255.255.255.0

Gateway:
192.168.10.1

DNS:
192.168.10.10
```

Enable:

```text
HTTP
```

---

# 📡 PART 13 — CONFIGURE AP-01

Packet Tracer AP configuration varies by device model.

Configure an SSID:

```text
Northstar-Corp
```

Use supported secure authentication such as:

```text
WPA2-PSK
```

if available on the selected Packet Tracer device.

Create a lab-only password.

Example:

```text
NorthstarLab18!
```

Do not use a real password from your workplace or personal accounts.

---

# 💻 PART 14 — CONNECT LAPTOP-01

Configure LAPTOP-01 to connect to:

```text
Northstar-Corp
```

Enter the lab password.

Set IPv4 addressing to:

> **DHCP**

---

# 💻 PART 15 — CONNECT LAPTOP-02

Repeat for LAPTOP-02.

Verify both receive:

```text
192.168.10.x
```

addresses.

---

# 🧪 PART 16 — VERIFY DHCP

On each laptop, record:

| Device | IP | Gateway | DNS |
|---|---|---|---|
| LAPTOP-01 | | | |
| LAPTOP-02 | | | |

Expected gateway:

```text
192.168.10.1
```

Expected DNS:

```text
192.168.10.10
```

---

# 🧪 PART 17 — TEST CONNECTIVITY

From LAPTOP-01:

```text
ping 192.168.10.1
```

Then:

```text
ping 192.168.10.10
```

Expected:

> **Success**

---

# 🌐 PART 18 — TEST HTTP

Open the laptop browser.

Navigate to:

```text
http://192.168.10.10
```

Expected:

> **SERVER-01 web page loads**

---

# 🧠 What Just Happened?

The communication path is:

```text
LAPTOP-01
    )))
    )))
   AP-01
     │
     ▼
   SW-01
     │
     ▼
 SERVER-01
```

The first part is wireless.

The rest is still:

> **Ethernet networking**

---

# 💥 PART 19 — BREAK THE PASSWORD

Change the wireless password on LAPTOP-02 so it no longer matches AP-01.

Try connecting.

---

# 🔍 Symptoms

You should see an:

> **Authentication / association problem**

depending on Packet Tracer behavior.

---

# 🧠 Root Cause

```text
SSID:
Correct

Password:
Incorrect
```

This is not:

```text
DHCP

DNS

Routing
```

because the client has not successfully joined the wireless network.

---

# 🔧 Repair

Restore the correct lab password.

Reconnect.

Verify DHCP again.

---

# 💥 PART 20 — BREAK DHCP

Now keep the wireless connection working but disable or incorrectly configure DHCP.

One option is to remove the router DHCP pool temporarily.

Then reconnect/renew a wireless client.

---

# 🧠 Compare the Failure

Earlier:

```text
Wrong Password
      ↓
Cannot Properly Join Wi-Fi
```

Now:

```text
Wi-Fi Association
      ↓
Works

DHCP
      ↓
Fails
```

These are different failures.

---

# 🔍 Investigate

Check:

```text
Wireless connection
        ↓
Client IP configuration
        ↓
DHCP configuration
```

---

# 🔧 Repair

Restore the DHCP pool.

Confirm the client receives a valid:

```text
192.168.10.x
```

address.

---

# 💥 PART 21 — BREAK THE AP UPLINK

Disconnect:

```text
AP-01
   │
   X
SW-01
```

Leave LAPTOP-01 associated if Packet Tracer permits it.

---

# 🧠 Question

Can a client potentially appear connected to the wireless AP while still being unable to reach the rest of the LAN?

> **Yes**

The wireless link and AP's wired uplink are separate parts of the path.

---

# 🔧 Repair

Reconnect:

```text
AP-01
   │
SW-01
```

Retest:

```text
ping 192.168.10.1
```

---

# 💥 PART 22 — AP POWER SCENARIO

Imagine AP-01 uses PoE.

Users report:

```text
SSID disappeared

Everyone near AP-01 disconnected
```

What should you investigate?

```text
AP Power

PoE Switch Port

PoE Budget

Ethernet Cable

Switch Port State
```

Lesson 17 and Lesson 18 now connect together.

---

# 🏢 PART 23 — DESIGN CORPORATE AND GUEST WI-FI

Northstar wants:

```text
Northstar-Corp

Northstar-Guest
```

Corporate users need:

```text
Internal Resources
+
Internet
```

Guests need:

```text
Internet
```

but should not have normal access to:

```text
Corporate Servers
```

---

# 🧠 Design

A logical design might use:

```text
Northstar-Corp
      ↓
VLAN 10
      ↓
Corporate Network


Northstar-Guest
      ↓
VLAN 50
      ↓
Guest Network
      ↓
Firewall
      ↓
Internet
```

with policy preventing guest access to protected corporate resources.

---

# ✏️ PART 24 — CREATE THE ADDRESS PLAN

Use:

## Corporate

```text
VLAN:
10

Network:
192.168.10.0/24
```

## Guest

```text
VLAN:
50

Network:
192.168.50.0/24
```

---

# 🧠 Question

Why should guest devices not simply be placed on the normal corporate employee network?

Record:

```text
________________________________

________________________________
```

Suggested answer:

> **Segmentation allows different access policies and reduces unnecessary guest access to internal resources.**

---

# 📡 PART 25 — AP PLACEMENT DESIGN

Imagine this office:

```text
+-------------------------------------------+
|                                           |
| Offices                  Conference Room  |
|                                           |
|                 AP-01                     |
|                                           |
|------------------+------------------------|
|                  |                        |
| Metal Storage    |       Offices          |
|                  |                        |
|                  |                 AP-02  |
|                                           |
+-------------------------------------------+
```

---

# 🧠 Question

Would placing AP-01 inside:

```text
Metal Storage
```

be a good design?

> **No**

Metal and other obstacles can negatively affect wireless propagation.

---

# 📶 PART 26 — COVERAGE TROUBLESHOOTING

Ticket:

> "Wi-Fi is good at my desk, but terrible in the far conference room."

What should you investigate?

Choose all that apply:

```text
Distance

Signal Strength

Walls

AP Placement

Band

Interference

Coverage Design
```

> **All are reasonable areas to investigate.**

---

# 📻 PART 27 — CHANNEL TROUBLESHOOTING

You find:

```text
AP-01
2.4 GHz
Channel 1

AP-02
2.4 GHz
Channel 2

AP-03
2.4 GHz
Channel 3
```

What is wrong with this design?

> **The channels overlap heavily.**

---

# 🔧 Better Basic U.S. Plan

A simple starting plan is:

```text
AP-01
Channel 1

AP-02
Channel 6

AP-03
Channel 11
```

Real enterprise wireless systems may perform automatic RF/channel management, but you should understand why channel planning matters.

---

# 📊 PART 28 — SIGNAL TROUBLESHOOTING

Which signal is strongest?

```text
AP-01:
-48 dBm

AP-02:
-65 dBm

AP-03:
-81 dBm
```

Answer:

> **AP-01 at -48 dBm**

---

# 🧠 Why?

Because:

```text
-48
```

is closer to:

```text
0
```

than the other values.

---

# 💥 PART 29 — SUPPORT TICKET 1

User reports:

> "The Wi-Fi name doesn't show up at all."

Investigate:

```text
Wi-Fi adapter enabled?

Airplane mode?

SSID available?

AP powered?

AP in range?

Correct band supported?
```

---

# 💥 PART 30 — SUPPORT TICKET 2

User reports:

> "I connect to Wi-Fi, but I have a 169.254 address."

Likely area:

> **DHCP**

---

# 💥 PART 31 — SUPPORT TICKET 3

User reports:

```text
Wi-Fi connected
IP valid
Gateway reachable
8.8.8.8 reachable
example.com fails
```

Likely area:

> **DNS**

---

# 💥 PART 32 — SUPPORT TICKET 4

Only users near:

```text
AP-03
```

have problems.

Everyone near:

```text
AP-01
AP-02
```

works.

What should you investigate first?

> **AP-03 and its local environment/uplink**

---

# 💥 PART 33 — SUPPORT TICKET 5

Every wireless user in the company loses access simultaneously.

What does that tell you?

> The scope is much larger than one AP or one client.

Investigate shared systems such as:

```text
Wireless Infrastructure

Switching

DHCP

DNS

Authentication

Firewall

Internet
```

depending on the exact symptoms.

---

# 🧭 PART 34 — BUILD A TROUBLESHOOTING DECISION TREE

Use:

```text
Can User See SSID?
        │
        ├── NO
        │    ↓
        │  Radio / AP / Coverage
        │
        ▼
       YES
        │
        ▼
Can User Authenticate?
        │
        ├── NO
        │    ↓
        │  Credentials / Security
        │
        ▼
       YES
        │
        ▼
Valid IP Address?
        │
        ├── NO
        │    ↓
        │  DHCP / VLAN
        │
        ▼
       YES
        │
        ▼
Gateway Reachable?
        │
        ├── NO
        │    ↓
        │  VLAN / Routing / LAN
        │
        ▼
       YES
        │
        ▼
DNS Working?
        │
        ├── NO
        │    ↓
        │  DNS
        │
        ▼
       YES
        │
        ▼
Internet / Application Test
```

---

# 📝 PART 35 — WIRELESS TROUBLESHOOTING REPORT

Choose one problem from the lab.

Document:

```text
Problem:

________________________________


Initial Symptoms:

________________________________


SSID Visible?

YES / NO


Associated?

YES / NO


Signal:

________________________________


IP Address:

________________________________


Gateway:

________________________________


DNS:

________________________________


Scope:

One User / One AP / Multiple APs / Entire Network


Tools Used:

________________________________


Root Cause:

________________________________


Solution:

________________________________


Verification:

________________________________


What I Learned:

________________________________
```

---

# 🗺️ PART 36 — WIRELESS DESIGN DOCUMENTATION

Create:

| Item | Configuration |
|---|---|
| Corporate SSID | Northstar-Corp |
| Corporate VLAN | 10 |
| Corporate Network | 192.168.10.0/24 |
| Guest SSID | Northstar-Guest |
| Guest VLAN | 50 |
| Guest Network | 192.168.50.0/24 |
| Corporate Security | WPA2/WPA3 as supported |
| Guest Access | Internet-focused / isolated |
| AP Uplink | Ethernet |
| AP Power | PoE where supported |

---

# 🧠 Knowledge Check

### 1.
What does SSID identify?

### 2.
What does BSSID identify?

### 3.
Which frequency generally provides better range: 2.4 or 5 GHz?

### 4.
What 2.4 GHz channels are commonly used for a basic non-overlapping U.S. 20 MHz plan?

### 5.
Which is stronger: `-50 dBm` or `-75 dBm`?

### 6.
What does WPA protect?

### 7.
What happens after wireless association when a client needs automatic IPv4 configuration?

### 8.
What does a 169.254.x.x address suggest on Windows?

### 9.
Why separate guest Wi-Fi?

### 10.
If everyone near one AP has problems, what does the scope suggest?

---

# ✅ Answers

1. **The wireless network**
2. **A specific AP/radio**
3. **2.4 GHz generally**
4. **1, 6, and 11**
5. **-50 dBm**
6. **Wireless network access/communications through Wi-Fi security mechanisms**
7. **The client commonly uses DHCP**
8. **Automatic addressing failed and APIPA was assigned**
9. **To control guest access and isolate guests from protected internal resources**
10. **Investigate that AP and its local environment/uplink**

---

# 🎓 Network+ Challenge 1

A laptop sees the SSID but cannot connect after the company changed its wireless password.

What should you investigate?

> **Authentication credentials / saved wireless profile**

---

# 🎓 Network+ Challenge 2

A user connects successfully but receives:

```text
169.254.55.20
```

What should you investigate?

> **DHCP**

---

# 🎓 Network+ Challenge 3

Which signal is strongest?

```text
A. -88 dBm
B. -74 dBm
C. -62 dBm
D. -41 dBm
```

> **D — -41 dBm**

---

# 🎓 Network+ Challenge 4

An AP is connected to the switch but will not power on.

It is supposed to use PoE.

What should you investigate?

> **PoE capability, port configuration, cable, power budget, and device power requirements.**

---

# 🎓 Network+ Challenge 5

Corporate Wi-Fi works, but guests can unexpectedly reach internal servers.

What should you investigate?

> **Guest VLAN segmentation and firewall/access-control policy.**

---

# 🎓 Network+ Challenge 6

All users in one conference room experience poor Wi-Fi, especially when the room is full.

What should you investigate?

> **Coverage, capacity, signal, interference, client density, AP placement, and channel design.**

---

# 🏆 LAB COMPLETION CHECKLIST

- [ ] I identified my Windows wireless adapter
- [ ] I used `netsh wlan show interfaces`
- [ ] I identified SSID
- [ ] I identified BSSID
- [ ] I identified radio type
- [ ] I identified wireless channel
- [ ] I inspected signal strength
- [ ] I observed visible wireless networks
- [ ] I reviewed 2.4 GHz channel use
- [ ] I compared wireless signal at different locations
- [ ] I built a Packet Tracer wireless network
- [ ] I configured an SSID
- [ ] I configured wireless security
- [ ] I connected wireless clients
- [ ] I verified DHCP
- [ ] I tested LAN connectivity
- [ ] I tested HTTP connectivity
- [ ] I troubleshot incorrect authentication
- [ ] I troubleshot DHCP failure
- [ ] I troubleshot an AP uplink failure
- [ ] I designed corporate and guest Wi-Fi
- [ ] I mapped wireless networks to VLAN concepts
- [ ] I reviewed AP placement
- [ ] I reviewed channel overlap
- [ ] I interpreted signal strength
- [ ] I worked through wireless support tickets
- [ ] I completed a troubleshooting report
- [ ] I documented the wireless design

---

# 🏆 Lab 18 Complete

You can now follow the path:

```text
Wireless Client
      )))
      )))
Access Point
      │
      ▼
Switch
      │
      ▼
VLAN
      │
      ▼
DHCP / DNS / Routing
      │
      ▼
Network Resources
```

More importantly, when someone says:

> **"The Wi-Fi isn't working."**

you now know that could mean:

```text
No Signal

SSID Missing

Authentication Failure

Weak Signal

Interference

Wrong VLAN

DHCP Failure

DNS Failure

Routing Failure

AP Uplink Failure

Internet Failure
```

Those are very different problems.

---

# 📍 Course Progress

```text
🟠 PHASE 4 — NETWORK IMPLEMENTATION

✅ Lesson 17 — Network Cabling & Physical Infrastructure
✅ Lab 17

✅ Lesson 18 — Wireless Networking
✅ Lab 18

        ↓

🟡 NEXT:
Lesson 19 — WAN & Remote Connectivity
```

---

# ➡️ Next Lesson

Continue to:

> **📘 Lesson 19 — WAN and Remote Connectivity**

Next we'll leave the local office network and learn how businesses connect:

```text
Office
   ↓
ISP
   ↓
Internet / WAN
   ↓
Branch Office

Remote Employee
   ↓
VPN
   ↓
Corporate Network
```

We'll cover concepts such as:

- LAN vs. WAN
- ISP connections
- Fiber Internet
- Cable Internet
- DSL
- Cellular
- Satellite
- Dedicated circuits
- Metro Ethernet
- MPLS
- SD-WAN
- Site-to-site VPNs
- Remote-access VPNs
- Split tunneling
- Full tunneling
- Latency
- Bandwidth
- Jitter
- Packet loss
- WAN troubleshooting

---

# 📚 Course Navigation

➡️ **[Networking Lessons](../lessons/README.md)**

➡️ **[Networking Labs](README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**