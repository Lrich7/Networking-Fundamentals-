# Lab 02 --- Network Types and Topologies

## Lab Objective

Practice identifying network types and topologies, then build and
troubleshoot a switched star network in Cisco Packet Tracer.

## Part 1 --- Classify the Network

Identify each as LAN, WLAN, WAN, or PAN: 1. Three office PCs connected
to one switch: \_\_\_\_\_\_\_\_\_\_ 2. A laptop connected to an office
access point: \_\_\_\_\_\_\_\_\_\_ 3. A smartwatch connected to a phone:
\_\_\_\_\_\_\_\_\_\_ 4. Company offices connected across two cities:
\_\_\_\_\_\_\_\_\_\_

## Part 2 --- Identify Topologies

Name each:

``` text
       PC1
        │
PC2 ─ Switch ─ PC3
```

Topology: \_\_\_\_\_\_\_\_\_\_

``` text
Router A ───── Router B
```

Topology: \_\_\_\_\_\_\_\_\_\_

A design with several redundant paths: \_\_\_\_\_\_\_\_\_\_

## Part 3 --- Build a Star Network

In Packet Tracer add one switch and four PCs.

``` text
       PC0
        │
PC1 ─ Switch ─ PC2
        │
       PC3
```

Configure:

``` text
PC0  192.168.20.10 /24
PC1  192.168.20.20 /24
PC2  192.168.20.30 /24
PC3  192.168.20.40 /24
```

Use subnet mask `255.255.255.0`. No gateway is needed for this
same-network test.

## Part 4 --- Test Connectivity

From PC0 ping the other three PCs. Record pass/fail.

``` text
PC1: ______
PC2: ______
PC3: ______
```

Save as `lab-02-star-topology.pkt`.

## Part 5 --- Test Failure Scope

Disconnect only PC3. Verify PC0 can still reach PC1 and PC2. Reconnect
it.

Then temporarily disconnect/power off the central switch. What changes?
Why?

``` text
____________________________________________________
```

## Part 6 --- Simulation Mode

Switch to Simulation Mode and send a ping from PC0 to PC2. Observe the
traffic passing through the switch.

Path:

``` text
________ → ________ → ________
```

## Part 7 --- Create a Hybrid Diagram

Add a router, second switch, and two PCs.

``` text
PC0 ── Switch0 ── Router ── Switch1 ── PC4
```

You do not need to configure routing yet. The goal is to visualize
multiple network segments.

Save as `lab-02-hybrid-topology.pkt`.

## Part 8 --- Document It

Record:

``` text
Topology: __________________
Number of PCs: _____________
Switches: __________________
IP network: ________________
Central device: ____________
```

## Knowledge Check

1.  Which topology uses a central device? A. Bus B. Star C. Ring D.
    Point-to-point
2.  If one endpoint cable fails in a star, what normally happens?
3.  What does a WAN commonly connect?
4.  Why is a network diagram useful?
5.  If every PC on one switch fails, which shared device should you
    inspect early?

## Challenge

Build a small-office diagram containing 6 desktops, 3 wireless laptops,
a printer, server, switch, access point, router, and Internet. Label
LAN, WLAN, WAN, and the central switch.

## Lab Completion Checklist

-   [ ] Classified network types
-   [ ] Identified topologies
-   [ ] Built a star network
-   [ ] Tested connectivity
-   [ ] Tested endpoint and central-device failures
-   [ ] Used Simulation Mode
-   [ ] Created a hybrid layout
-   [ ] Documented the network
-   [ ] Completed the knowledge check
-   [ ] Completed the challenge

# Lab Complete

You have completed **Lab 02 --- Network Types and Topologies**.

# Next Lesson

➡️ **[Lesson 03 --- Network
Devices](../lessons/lesson-03-network-devices.md)**
