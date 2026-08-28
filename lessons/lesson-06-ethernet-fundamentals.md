# Lesson 06 --- Ethernet Fundamentals

## Learning Objectives

By the end of this lesson, you will be able to:

-   Explain the purpose of Ethernet in a local area network.
-   Identify Ethernet frames, MAC addresses, switches, and Ethernet
    ports.
-   Explain the difference between MAC addresses and IP addresses.
-   Describe how a switch learns and forwards traffic.
-   Explain unicast, broadcast, and multicast at a beginner level.
-   Recognize common Ethernet speeds.
-   Use Windows and PowerShell to inspect Ethernet information.
-   Observe Ethernet communication in Cisco Packet Tracer.

------------------------------------------------------------------------

# What Is Ethernet?

**Ethernet** is one of the most widely used technologies for wired local
area networks.

A basic Ethernet LAN may look like:

``` text
PC1 ─────┐
         │
PC2 ── Switch ── Server
         │
Printer ─┘
```

Ethernet defines rules for how devices communicate across the local
network.

Important Ethernet concepts include:

``` text
Frames
MAC addresses
Switches
Ethernet ports
Cabling
Link speed
Duplex
```

------------------------------------------------------------------------

# Ethernet and the OSI Model

Ethernet is primarily associated with:

``` text
OSI Layer 2 — Data Link
OSI Layer 1 — Physical
```

Layer 2 deals with concepts such as:

``` text
Frames
MAC addresses
Switching
```

Layer 1 deals with:

``` text
Cables
Connectors
Signals
Physical ports
```

------------------------------------------------------------------------

# Ethernet Frames

Ethernet sends information across the local network using **frames**.

A simplified Ethernet frame contains information such as:

``` text
Destination MAC Address
Source MAC Address
Type / Payload Information
Data
Error-checking information
```

You do not need to memorize the entire frame structure yet.

The important idea is:

``` text
Ethernet Frame
      ↓
Carries data across the local link
```

------------------------------------------------------------------------

# MAC Addresses

A **MAC address** identifies a network interface at the data-link layer.

Example format:

``` text
00-1A-2B-3C-4D-5E
```

or:

``` text
00:1A:2B:3C:4D:5E
```

MAC addresses are normally represented as 48-bit hexadecimal values.

------------------------------------------------------------------------

# MAC vs. IP Address

Do not treat MAC and IP addresses as interchangeable.

``` text
MAC Address
    ↓
Local-link identification
OSI Layer 2

IP Address
    ↓
Logical network addressing
OSI Layer 3
```

A host may use both during the same communication.

------------------------------------------------------------------------

# Switches and Ethernet

A switch connects Ethernet devices and learns which MAC addresses are
reachable through its ports.

Conceptually:

``` text
Port 1 → PC1 MAC
Port 2 → PC2 MAC
Port 3 → Server MAC
```

The switch builds a **MAC address table**.

When a frame arrives, the switch examines the destination MAC address
and determines where the frame should be forwarded.

------------------------------------------------------------------------

# Unknown Destinations

If a switch has not yet learned where a destination MAC address is
located, it may initially forward the frame out multiple appropriate
ports within the same broadcast domain.

After learning where devices are located, it can make more specific
forwarding decisions.

You will observe this behavior in Packet Tracer.

------------------------------------------------------------------------

# Unicast

**Unicast** communication is intended for one destination.

``` text
PC1 ─────→ PC2
```

Most normal client/server communication is unicast.

------------------------------------------------------------------------

# Broadcast

A **broadcast** is intended for all devices in the local broadcast
domain.

Conceptually:

``` text
        ┌→ PC1
Sender ─┼→ PC2
        ├→ PC3
        └→ Server
```

ARP requests are an important example you will study in Lesson 07.

Routers normally separate broadcast domains.

------------------------------------------------------------------------

# Multicast

**Multicast** allows traffic to be sent to a group of interested
receivers rather than every device.

You do not need to configure multicast yet.

Remember:

``` text
Unicast   → One destination
Broadcast → Everyone in local broadcast domain
Multicast → Selected group
```

------------------------------------------------------------------------

# Ethernet Speeds

Common Ethernet speeds include:

``` text
10 Mbps
100 Mbps
1 Gbps
2.5 Gbps
5 Gbps
10 Gbps
40 Gbps
100 Gbps and beyond
```

You will explore standards and speeds more deeply in Lesson 09.

------------------------------------------------------------------------

# Duplex

Ethernet links can operate using duplex concepts.

## Half Duplex

Communication can occur in both directions, but not simultaneously.

## Full Duplex

Both sides can transmit and receive at the same time.

Modern switched Ethernet commonly uses full duplex.

------------------------------------------------------------------------

# Collision Domains

Older shared Ethernet technologies such as hubs created shared collision
domains.

Modern switches create separate collision domains per switch port.

This is one reason switches provide major advantages over hubs.

------------------------------------------------------------------------

# Inspect Ethernet in Windows

Run:

``` powershell
Get-NetAdapter
```

Useful properties include:

``` text
Name
InterfaceDescription
Status
MacAddress
LinkSpeed
```

For more detail:

``` powershell
Get-NetAdapter |
    Select-Object Name,
        InterfaceDescription,
        Status,
        MacAddress,
        LinkSpeed
```

------------------------------------------------------------------------

# Ethernet Troubleshooting

When an Ethernet connection fails, check:

``` text
Cable connected?
        ↓
Link light / adapter status?
        ↓
Correct switch port?
        ↓
Adapter enabled?
        ↓
Correct IP configuration?
        ↓
Local communication working?
```

Do not immediately change IP settings if the physical Ethernet link is
down.

------------------------------------------------------------------------

# Key Terms

``` text
Ethernet
Frame
MAC Address
Switch
MAC Address Table
Unicast
Broadcast
Multicast
Duplex
Collision Domain
Link Speed
```

------------------------------------------------------------------------

# Knowledge Check

1.  Which OSI layer is most associated with Ethernet frames and MAC
    addresses?
2.  What does a switch learn in its MAC address table?
3.  What is the difference between unicast and broadcast?
4.  What is the difference between a MAC address and an IP address?
5.  What is full duplex?
6.  Why are switches better than hubs for modern Ethernet LANs?

------------------------------------------------------------------------

# Lesson Summary

Ethernet provides the foundation for most wired LANs.

Remember:

``` text
Ethernet
   ↓
Frames
   ↓
MAC Addresses
   ↓
Switches
   ↓
Local Network Communication
```

------------------------------------------------------------------------

# Hands-On Lab

➡️ **[Lab 06 --- Ethernet
Fundamentals](../labs/lab-06-ethernet-fundamentals.md)**
