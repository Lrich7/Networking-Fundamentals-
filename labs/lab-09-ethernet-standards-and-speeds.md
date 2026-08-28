# Lab 09 --- Ethernet Standards and Speeds

## Lab Objective

Inspect Ethernet link speeds and practice diagnosing speed and
bottleneck scenarios.

------------------------------------------------------------------------

# Part 1 --- Inspect Link Speed

Run:

``` powershell
Get-NetAdapter |
    Select-Object Name,
        InterfaceDescription,
        Status,
        LinkSpeed
```

Record:

``` text
Adapter: __________________________________
Link Speed: ________________________________
```

------------------------------------------------------------------------

# Part 2 --- Inspect Adapter Properties

Run:

``` powershell
Get-NetAdapterAdvancedProperty
```

Find your active adapter.

Do not change production settings.

Look for any properties related to:

``` text
Speed
Duplex
Energy saving
```

Record what you find.

------------------------------------------------------------------------

# Part 3 --- Match Standards

Fill in:

``` text
100BASE-TX  = __________ Mbps
1000BASE-T  = __________ Gbps
10GBASE-T   = __________ Gbps
```

------------------------------------------------------------------------

# Part 4 --- Packet Tracer Interface Inspection

Build:

``` text
PC0 ── Switch ── PC1
```

Inspect the interfaces/devices available in your Packet Tracer version.

Record the displayed or supported interface speeds if visible.

------------------------------------------------------------------------

# Part 5 --- Bottleneck Exercise

For each path, identify the likely maximum bottleneck.

## A

``` text
PC 1 Gbps → Switch 1 Gbps → Internet 100 Mbps
```

Bottleneck: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## B

``` text
PC 100 Mbps → Switch 1 Gbps → Server 1 Gbps
```

Bottleneck: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## C

``` text
PC 10 Gbps → Switch 10 Gbps → Server NIC 1 Gbps
```

Bottleneck: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

------------------------------------------------------------------------

# Part 6 --- Troubleshooting a Slow Link

A workstation should connect at 1 Gbps but shows 100 Mbps.

List at least five things you would investigate.

``` text
1. __________________________________
2. __________________________________
3. __________________________________
4. __________________________________
5. __________________________________
```

------------------------------------------------------------------------

# Part 7 --- Link Speed vs. Throughput

Answer:

A PC shows a 1 Gbps link but downloads from the Internet at 150 Mbps.

Does that automatically prove the Ethernet link is broken?

``` text
Yes / No
```

Explain:

``` text
____________________________________________________
```

------------------------------------------------------------------------

# Part 8 --- Duplex Scenario

A manually configured legacy link has severe performance problems.

One side is configured differently from the other.

What configuration concept should you investigate?

``` text
____________________________________
```

------------------------------------------------------------------------

# Part 9 --- Create a Performance Checklist

Build your own:

``` text
Scope of issue
   ↓
Adapter/link speed
   ↓
Cable
   ↓
Switch port
   ↓
Upstream links
   ↓
Service/WAN speed
   ↓
Destination/application
```

Add any checks you think are useful.

------------------------------------------------------------------------

# Knowledge Check

1.  What speed is Gigabit Ethernet?
2.  What is the purpose of auto-negotiation?
3.  What is the difference between link speed and throughput?
4.  What can cause a 1 Gbps-capable device to link at 100 Mbps?
5.  If the Internet service is 200 Mbps, can a 1 Gbps NIC make the
    Internet service itself 1 Gbps?

------------------------------------------------------------------------

# Challenge

Write a troubleshooting response for this ticket:

> "My desktop says 1.0 Gbps, but copying files to one particular server
> is slow."

Your plan must avoid assuming the NIC is the problem. Include endpoint,
switch, path, server, and application/storage considerations.

------------------------------------------------------------------------

# Lab Completion Checklist

-   [ ] Inspected link speed
-   [ ] Inspected advanced adapter properties
-   [ ] Matched Ethernet standards
-   [ ] Inspected Packet Tracer interfaces
-   [ ] Identified bottlenecks
-   [ ] Troubleshot a low negotiated speed
-   [ ] Compared link speed and throughput
-   [ ] Reviewed duplex mismatch
-   [ ] Built performance checklist
-   [ ] Completed knowledge check
-   [ ] Completed challenge

------------------------------------------------------------------------

# Lab Complete

You have completed **Lab 09 --- Ethernet Standards and Speeds**.

# Next Lesson

➡️ **[Lesson 10 --- Wireless Networking
Basics](../lessons/lesson-10-wireless-networking-basics.md)**
