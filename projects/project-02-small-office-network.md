# Project 02 --- Small Office Network

## Project Overview

You have completed Section 2 --- **Ethernet & Physical Networking**.

Your task is to design, build, test, document, and troubleshoot a small
office network that combines wired Ethernet and Wi-Fi.

This project is intentionally less guided than the labs.

------------------------------------------------------------------------

# Project Objectives

Demonstrate that you can:

-   Select wired and wireless network components.
-   Design a switched star topology.
-   Choose appropriate basic cabling/media.
-   Explain MAC addressing and ARP.
-   Inspect switch MAC learning.
-   Consider Ethernet speed and bottlenecks.
-   Configure a basic WLAN.
-   Test wired and wireless connectivity.
-   Identify physical and wireless failure scope.
-   Document and troubleshoot the environment.

------------------------------------------------------------------------

# Scenario

A growing office has:

``` text
8 desktop PCs
6 employee laptops
1 server
2 network printers
1 router/firewall
1 main switch
2 wireless access points
Internet connection
```

The office occupies one floor.

A second small workspace is located in another building approximately
250 meters away and may need connectivity in the future.

Your current task is to design the main office and recommend an
appropriate medium for the future building link.

------------------------------------------------------------------------

# Part 1 --- Requirements

Document:

``` text
Wired endpoints: ____________________________
Wireless endpoints: _________________________
Infrastructure devices: _____________________
Shared resources: ___________________________
Future requirement: _________________________
```

------------------------------------------------------------------------

# Part 2 --- Design the Topology

Create a switched star design.

Your diagram should clearly show:

``` text
Router/Firewall
Switch
Desktop PCs
Server
Printers
Access Points
Wireless Laptops
Internet direction
Future building-link direction
```

------------------------------------------------------------------------

# Part 3 --- Choose Media

Document your choices.

``` text
Desktop → Switch: ___________________________
Server → Switch: ____________________________
Printer → Switch: ___________________________
AP → Switch: ________________________________
Future 250 m building link: _________________
```

Explain each choice.

Do not simply choose the fastest or most expensive medium.

Consider:

``` text
Distance
Environment
Speed
Cost
Interference
Future growth
```

------------------------------------------------------------------------

# Part 4 --- Build the Main Office

Use Cisco Packet Tracer to build a representative version.

You do not have to add all 8 desktops if your environment becomes
cluttered, but your diagram/documentation must represent the full
requirement.

A practical Packet Tracer model should include at least:

``` text
4 wired PCs
2 wireless laptops
1 server
1 printer
1 switch
1 router
1–2 access points
```

------------------------------------------------------------------------

# Part 5 --- Addressing

Use a single lab network for now:

``` text
192.168.110.0/24
```

Reserve:

``` text
192.168.110.1
```

for the gateway.

Create unique endpoint addresses.

Advanced subnetting is not required yet.

------------------------------------------------------------------------

# Part 6 --- Wireless Design

Create an employee lab SSID such as:

``` text
Office-Training
```

Document:

``` text
SSID: _______________________________________
Number of APs: ______________________________
Why more than one AP might be useful:
_____________________________________________
```

Do not reuse a real password.

------------------------------------------------------------------------

# Part 7 --- Test Connectivity

Verify:

``` text
Wired PC → Server
Wired PC → Printer
Wireless Laptop → Server
Wireless Laptop → Printer
Endpoint → Gateway
Wireless Laptop → Wired PC
```

Record pass/fail.

------------------------------------------------------------------------

# Part 8 --- Inspect MAC Learning

Generate traffic.

On the switch:

``` text
show mac address-table
```

Document at least four learned MAC addresses and their ports.

``` text
MAC                     Port
________________________________________
________________________________________
________________________________________
________________________________________
```

Explain what the table represents.

------------------------------------------------------------------------

# Part 9 --- Explain ARP

Choose one PC and one local destination.

Document:

``` text
Source IP: __________________________________
Destination IP: _____________________________
Destination MAC learned: ____________________
```

Use Simulation Mode if needed to observe ARP.

Explain:

``` text
Why was ARP required?

____________________________________________________
```

------------------------------------------------------------------------

# Part 10 --- Ethernet Performance Review

Assume:

``` text
Desktop NICs: 1 Gbps
Switch access ports: 1 Gbps
Server NIC: 1 Gbps
Internet service: 300 Mbps
```

Answer:

1.  What is the local desktop link speed?
2.  Does that make Internet service 1 Gbps?
3.  What is the Internet bottleneck in this simplified example?
4.  If one desktop negotiates at 100 Mbps, what would you investigate?

------------------------------------------------------------------------

# Part 11 --- Future Building Connection

The second building is about 250 meters away.

Would you recommend a normal copper Ethernet patch run directly between
the buildings?

``` text
Yes / No
```

Recommend a medium and explain your reasoning.

Consider:

``` text
Distance
Electrical isolation
Interference
Future bandwidth
```

------------------------------------------------------------------------

# Part 12 --- Failure 1: Physical

Disconnect one wired endpoint.

Troubleshoot without immediately looking at the answer.

Record:

``` text
Symptom: ____________________________________
Scope: ______________________________________
OSI starting layer: _________________________
Cause: ______________________________________
Fix: ________________________________________
Verification: ________________________________
```

------------------------------------------------------------------------

# Part 13 --- Failure 2: MAC/Local Communication

Generate traffic and inspect the MAC table.

Move an endpoint to another switch port or clear/relearn the lab state
using safe Packet Tracer actions.

Observe how the switch learns where the endpoint now resides.

Explain:

``` text
What changed in the MAC table?

____________________________________________________
```

------------------------------------------------------------------------

# Part 14 --- Failure 3: Wireless

Create one wireless problem:

``` text
Wrong SSID
Disabled AP
Disconnected AP uplink
Incorrect client configuration
```

Diagnose and repair it.

Record the scope and fix.

------------------------------------------------------------------------

# Part 15 --- Failure 4: Performance

Scenario:

> One desktop capable of 1 Gbps links at only 100 Mbps.

Create a troubleshooting plan containing at least:

``` text
NIC capability
Negotiated speed
Cable
Switch port
Adapter settings
Driver
Dock/adapter limitations
```

You do not have to reproduce every hardware fault in Packet Tracer.

------------------------------------------------------------------------

# Part 16 --- Final Documentation

Document:

``` text
Topology: ___________________________________
LAN network: 192.168.110.0/24
Gateway: 192.168.110.1
Wired devices: ______________________________
Wireless devices: ___________________________
Switch: _____________________________________
Access points: ______________________________
Server: _____________________________________
Printers: ___________________________________
Internet service assumption: 300 Mbps
Future building medium: _____________________
```

------------------------------------------------------------------------

# Part 17 --- Save

Save your Packet Tracer project as:

``` text
project-02-small-office-network.pkt
```

Recommended repository location:

``` text
packet-tracer/projects/
```

------------------------------------------------------------------------

# Final Validation

-   [ ] Network requirements documented
-   [ ] Star topology designed
-   [ ] Media choices documented
-   [ ] Main office built in Packet Tracer
-   [ ] Wired communication tested
-   [ ] Wireless communication tested
-   [ ] MAC table inspected
-   [ ] ARP process explained
-   [ ] Link speed/bottleneck scenario completed
-   [ ] Future building link recommendation completed
-   [ ] Physical failure repaired
-   [ ] MAC-learning exercise completed
-   [ ] Wireless failure repaired
-   [ ] Performance troubleshooting plan created
-   [ ] Final network documented
-   [ ] `.pkt` file saved

------------------------------------------------------------------------

# Project Reflection

1.  Why is a switch central to this design?
2.  How do MAC and IP addresses serve different purposes?
3.  Why is ARP necessary for IPv4 Ethernet communication?
4.  When would fiber make more sense than copper?
5.  Why does Wi-Fi troubleshooting require separating radio connectivity
    from IP/application connectivity?
6.  What would you improve if the office grew to 50 employees?

------------------------------------------------------------------------

# 🏆 Project Complete

You have completed **Project 02 --- Small Office Network**.

You have now applied:

``` text
Ethernet
MAC addressing
ARP
Switch learning
Copper and fiber media
Ethernet speeds
Bottleneck analysis
Wireless networking
Physical troubleshooting
Wireless troubleshooting
Network documentation
```

------------------------------------------------------------------------

# ➡️ Continue Training

Next:

➡️ **[Lesson 11 --- IPv4
Addressing](../lessons/lesson-11-ipv4-addressing.md)**
