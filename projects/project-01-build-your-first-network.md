# Project 01 --- Build Your First Network

## Project Overview

Combine Lessons 01--05 by designing, building, testing, documenting, and
troubleshooting a small business network in Cisco Packet Tracer.

Unlike the labs, this project gives you requirements without walking you
through every click.

## Project Objectives

You will: - Interpret a network requirement. - Select appropriate
devices. - Build a star-style Ethernet LAN. - Add wireless
connectivity. - Configure basic IPv4 settings. - Test same-network
communication. - Identify LAN, WLAN, and WAN concepts. - Apply OSI and
TCP/IP concepts. - Use Simulation Mode. - Document the network. -
Troubleshoot intentional failures.

## Scenario

A small office needs networking for:

``` text
4 employee desktop PCs
2 wireless laptops
1 server
1 network printer
Internet connectivity
```

Include infrastructure for wired Ethernet, wireless access, local
switching, and a path toward remote networks.

Advanced routing, DHCP, VLANs, and subnetting are **not** required yet.

## Part 1 --- Plan

List the endpoints and infrastructure you need.

``` text
Endpoints: __________________________________
Switch: _____________________________________
Router: _____________________________________
Wireless device: _____________________________
Server: _____________________________________
Printer: ____________________________________
```

## Part 2 --- Draw the Topology

Your design must include:

``` text
4 wired PCs
2 wireless laptops
1 server
1 printer
1 switch
1 wireless access point
1 router
```

Example concept:

``` text
                 Router
                   │
                 Switch
       ┌───────────┼───────────┐
       │           │           │
      PCs        Server      Printer
                   │
              Access Point
               ))       ))
            Laptop     Laptop
```

Identify the LAN, WLAN, WAN/Internet direction, and topology.

## Part 3 --- Build It

Create the topology in Packet Tracer using appropriate connections.

## Part 4 --- Addressing Plan

Use:

``` text
Network: 192.168.100.0/24
Subnet Mask: 255.255.255.0
Gateway reserved: 192.168.100.1
```

Create unique host addresses:

``` text
Router     192.168.100.1
PC0        __________________
PC1        __________________
PC2        __________________
PC3        __________________
Laptop0    __________________
Laptop1    __________________
Server     __________________
Printer    __________________
```

Do not assign `192.168.100.0` to a host.

## Part 5 --- Configure and Test

Configure endpoints and the router LAN interface. Configure a lab
wireless SSID such as `Training-WiFi`.

Test:

``` text
PC → another PC
PC → server
PC → printer
PC → router
Laptop → server
Laptop → router
```

Record pass/fail and troubleshoot before moving on.

## Part 6 --- Explain Device Roles

In your own words:

``` text
Switch: _____________________________________
Router: _____________________________________
Access Point: ________________________________
NIC: ________________________________________
Server: _____________________________________
```

## Part 7 --- Identify Network Types

``` text
Wired local network: _________________________
Wireless local network: ______________________
Remote-network direction: ____________________
Physical topology: ___________________________
```

## Part 8 --- Apply OSI

Identify the most relevant layer:

``` text
Ethernet cable: Layer ___
MAC address: Layer ___
IP address: Layer ___
TCP/UDP port: Layer ___
HTTP: Layer ___
```

## Part 9 --- Apply TCP/IP

Give one example for each:

``` text
Application: _________________________________
Transport: __________________________________
Internet: ___________________________________
Network Access: ______________________________
```

## Part 10 --- Simulation Mode

Send a ping from a PC to the server and observe the path.

Record:

``` text
Source IP: ___________________________________
Destination IP: ______________________________
Source MAC: __________________________________
Destination MAC: _____________________________
Path: ________________________________________
```

## Part 11 --- Troubleshooting Challenge 1

Disconnect one desktop from the switch.

Pretend the ticket says: **"PC2 has no network."**

Record:

``` text
Symptom: _____________________________________
Scope: _______________________________________
OSI layer checked first: _____________________
Cause: _______________________________________
Fix: _________________________________________
Verification: _________________________________
```

Repair it.

## Part 12 --- Troubleshooting Challenge 2

Give one endpoint an incorrect network such as `192.168.200.50/24`.

Diagnose:

``` text
Relevant OSI layer: __________________________
Relevant TCP/IP layer: _______________________
Cause: _______________________________________
Fix: _________________________________________
```

Restore the correct configuration.

## Part 13 --- Troubleshooting Challenge 3

Break one laptop's wireless connection using a safe lab change such as
wrong SSID or disabled wireless interface.

Record:

``` text
Scope: _______________________________________
Path/device investigated: ____________________
Cause: _______________________________________
Fix: _________________________________________
```

Restore it.

## Part 14 --- Final Documentation

``` text
Network: 192.168.100.0/24
Mask: 255.255.255.0
Gateway: 192.168.100.1
Topology: ____________________________________
Wired clients: _______________________________
Wireless clients: ____________________________
Infrastructure: ______________________________
Server: ______________________________________
Printer: _____________________________________
```

## Part 15 --- Save

Save as:

``` text
project-01-build-your-first-network.pkt
```

Recommended repository location:

``` text
packet-tracer/projects/
```

Do not put real company network information into a public training
repository.

## Final Validation

-   [ ] All required devices exist
-   [ ] Connections are correct
-   [ ] Wired clients communicate
-   [ ] Wireless clients communicate
-   [ ] Server is reachable
-   [ ] Printer is reachable
-   [ ] Router LAN interface is reachable
-   [ ] Every endpoint has a unique IP
-   [ ] Topology is documented
-   [ ] OSI concepts are documented
-   [ ] TCP/IP concepts are documented
-   [ ] Simulation Mode was used
-   [ ] Three failures were diagnosed/repaired
-   [ ] Final `.pkt` file was saved

## Project Reflection

1.  Which device was easiest to understand?
2.  Which concept was most difficult?
3.  How did OSI help troubleshoot?
4.  How did TCP/IP help explain communication?
5.  What would you add if the office doubled in size?

# 🏆 Project Complete

You have completed **Project 01 --- Build Your First Network**.

You have practiced planning, topology, device selection, IPv4
configuration, wired/wireless networking, testing, OSI/TCP-IP
troubleshooting, documentation, and failure isolation.

# ➡️ Continue Training

➡️ **[Lesson 06 --- Ethernet
Fundamentals](../lessons/lesson-06-ethernet-fundamentals.md)**
