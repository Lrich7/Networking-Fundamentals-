# Lesson 09 --- Ethernet Standards and Speeds

## Learning Objectives

By the end of this lesson, you will be able to:

-   Explain Ethernet naming conventions at a beginner level.
-   Recognize common Ethernet speeds and standards.
-   Match common copper Ethernet standards with expected media and
    distance concepts.
-   Explain auto-negotiation.
-   Explain speed and duplex mismatches.
-   Distinguish link speed from actual application throughput.
-   Identify common reasons an Ethernet link negotiates below
    expectations.
-   Inspect link speed using Windows and PowerShell.

------------------------------------------------------------------------

# Ethernet Speed Progression

Ethernet has evolved dramatically.

Common speeds include:

``` text
10 Mbps
100 Mbps
1 Gbps
2.5 Gbps
5 Gbps
10 Gbps
40 Gbps
100 Gbps+
```

------------------------------------------------------------------------

# Common Names

You may encounter names such as:

``` text
10BASE-T
100BASE-TX
1000BASE-T
2.5GBASE-T
5GBASE-T
10GBASE-T
```

A simplified way to read these:

``` text
Speed
  +
BASE = baseband Ethernet
  +
Medium/type indicator
```

------------------------------------------------------------------------

# Common Copper Standards

## 100BASE-TX

``` text
Speed: 100 Mbps
Common name: Fast Ethernet
```

## 1000BASE-T

``` text
Speed: 1 Gbps
Common name: Gigabit Ethernet
```

## 10GBASE-T

``` text
Speed: 10 Gbps
```

The cabling category and installation quality required depend on the
standard and distance.

Always verify the actual standard when designing production cabling.

------------------------------------------------------------------------

# Common Fiber Families

Fiber Ethernet standards include many variants.

Names may include:

``` text
1000BASE-SX
1000BASE-LX
10GBASE-SR
10GBASE-LR
```

Very broadly:

``` text
SR / SX → shorter-reach optical use cases
LR / LX → longer-reach optical use cases
```

Exact distances depend on the standard, fiber, and optics.

------------------------------------------------------------------------

# Auto-Negotiation

Ethernet devices commonly use **auto-negotiation** to agree on supported
link characteristics.

These can include:

``` text
Speed
Duplex
```

Example:

``` text
PC supports 1 Gbps
Switch supports 1 Gbps
Cable supports the link correctly
        ↓
Link may negotiate at 1 Gbps
```

------------------------------------------------------------------------

# Why a Link Might Negotiate Lower

Possible reasons:

``` text
Older NIC
Older switch
Cable problem
Incorrect cable category
Damaged pairs
Manual configuration
Adapter setting
Docking station limitation
USB adapter limitation
Power-saving or driver issue
```

------------------------------------------------------------------------

# Duplex Mismatch

A duplex mismatch can produce poor performance and errors.

Modern auto-negotiation reduces this problem, but manually forced or
older equipment can still create issues.

Symptoms may include:

``` text
Very poor throughput
Errors
Retransmissions
Intermittent performance
```

------------------------------------------------------------------------

# Link Speed vs. Throughput

A 1 Gbps link does **not** guarantee an application will transfer data
at exactly 1 Gbps.

Actual throughput can be affected by:

``` text
Protocol overhead
Server performance
Storage speed
Network congestion
Other links in the path
Application behavior
CPU
Wireless/WAN bottlenecks
```

Link speed tells you the negotiated rate of that local link.

------------------------------------------------------------------------

# Bottlenecks

A network path is limited by its constraints.

Example:

``` text
PC 1 Gbps
   ↓
Switch 1 Gbps
   ↓
Router 1 Gbps
   ↓
Internet 200 Mbps
```

An Internet download cannot exceed the 200 Mbps service simply because
the PC has a 1 Gbps Ethernet link.

------------------------------------------------------------------------

# Inspect Link Speed in Windows

``` powershell
Get-NetAdapter |
    Select-Object Name, Status, LinkSpeed
```

You can also inspect adapter advanced properties:

``` powershell
Get-NetAdapterAdvancedProperty
```

Do not change advanced adapter settings in a production environment
unless you understand the impact.

------------------------------------------------------------------------

# Basic Performance Troubleshooting

If a user reports:

> "The network is slow."

Ask:

``` text
What is slow?
One application or everything?
One user or many?
LAN or Internet?
What link speed is negotiated?
Are errors present?
Is Wi-Fi involved?
What is the expected service speed?
```

"Slow network" is a symptom, not a diagnosis.

------------------------------------------------------------------------

# Key Terms

``` text
Fast Ethernet
Gigabit Ethernet
10 Gigabit Ethernet
100BASE-TX
1000BASE-T
10GBASE-T
Auto-Negotiation
Duplex
Throughput
Link Speed
Bottleneck
```

------------------------------------------------------------------------

# Knowledge Check

1.  What speed is 1000BASE-T?
2.  What is auto-negotiation?
3.  Does a 1 Gbps link guarantee 1 Gbps application throughput?
4.  Name three reasons a link might negotiate below its expected speed.
5.  What is a bottleneck?
6.  Why can duplex problems hurt performance?

------------------------------------------------------------------------

# Lesson Summary

Ethernet performance depends on the entire path.

``` text
NIC
 ↓
Cable
 ↓
Switch
 ↓
Upstream Network
 ↓
Destination
```

A fast local link cannot overcome a slower bottleneck elsewhere.

------------------------------------------------------------------------

# Hands-On Lab

➡️ **[Lab 09 --- Ethernet Standards and
Speeds](../labs/lab-09-ethernet-standards-and-speeds.md)**
