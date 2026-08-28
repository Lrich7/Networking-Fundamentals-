# Lab 14 --- IPv6 Fundamentals

## Lab Objective

Inspect IPv6 on Windows, practice IPv6 notation, and configure a simple
IPv6 Packet Tracer network.

------------------------------------------------------------------------

# Part 1 --- Inspect Windows IPv6

Run:

``` powershell
Get-NetIPAddress -AddressFamily IPv6
```

Look for:

``` text
Link-local address
Prefix length
Interface
```

Do not publish organizational addressing.

------------------------------------------------------------------------

# Part 2 --- IPv6 Loopback

Run:

``` text
ping ::1
```

Record:

``` text
Result: ________________________________
```

What does this test?

``` text
____________________________________________________
```

------------------------------------------------------------------------

# Part 3 --- Recognize Address Types

Classify:

``` text
::1
fe80::1234
2001:db8:10::25
ff02::1
```

Use:

``` text
Loopback
Link-local
Documentation/global-unicast-style example
Multicast
```

------------------------------------------------------------------------

# Part 4 --- Compress Addresses

Compress:

``` text
2001:0db8:0000:0001:0000:0000:0000:0010
```

Answer:

``` text
____________________________________
```

Compress:

``` text
2001:0db8:0000:0000:0000:0000:0000:0025
```

Answer:

``` text
____________________________________
```

------------------------------------------------------------------------

# Part 5 --- Expand an Address

Expand:

``` text
2001:db8:1::10
```

into eight hextets.

``` text
____________________________________
```

------------------------------------------------------------------------

# Part 6 --- Build IPv6 LAN

Packet Tracer:

``` text
PC0 ── Switch ── PC1
```

Use documentation addresses:

``` text
PC0 2001:db8:14:1::10/64
PC1 2001:db8:14:1::20/64
```

Test:

``` text
ping 2001:db8:14:1::20
```

------------------------------------------------------------------------

# Part 7 --- Observe Link-Local

Inspect the IPv6 configuration on both PCs.

Record the link-local addresses if Packet Tracer displays them.

``` text
PC0: __________________________________
PC1: __________________________________
```

------------------------------------------------------------------------

# Part 8 --- Simulation Mode

Observe IPv6 communication.

Look for ICMPv6 and Neighbor Discovery-related traffic.

Compare it with the ARP process you observed in IPv4.

``` text
IPv4 used: ____________________________
IPv6 uses: ____________________________
```

------------------------------------------------------------------------

# Part 9 --- Add a Router

Create:

``` text
PC0 ── Switch0 ── Router ── Switch1 ── PC2
```

Use:

``` text
LAN A: 2001:db8:14:1::/64
LAN B: 2001:db8:14:2::/64
```

Configure appropriate router interface addresses and host gateways
according to your Packet Tracer version.

Test routed IPv6 communication.

------------------------------------------------------------------------

# Part 10 --- Wrong Prefix Scenario

Give one endpoint an address from the wrong `/64`.

Observe the failure.

Record:

``` text
Cause: __________________________________
Fix: ____________________________________
```

------------------------------------------------------------------------

# Part 11 --- IPv4 vs. IPv6

Fill in:

``` text
IPv4 bits: __________________
IPv6 bits: __________________

IPv4 loopback: ______________
IPv6 loopback: ______________

IPv4 address resolution: ____
IPv6 address resolution: ____

IPv4 broadcast: Yes / No
IPv6 broadcast: Yes / No
```

------------------------------------------------------------------------

# Knowledge Check

1.  What is `::1`?
2.  What is `fe80::/10` used for?
3.  What is the purpose of `2001:db8::/32`?
4.  What protocol family handles IPv6 neighbor discovery?
5.  Why is `/64` important to recognize?

------------------------------------------------------------------------

# Challenge

Build two IPv6 LANs connected by a router:

``` text
2001:db8:140:1::/64
2001:db8:140:2::/64
```

Use at least two PCs per LAN.

Test:

``` text
Local IPv6 communication
Router interface reachability
Cross-subnet IPv6 communication
```

Then create one incorrect prefix/address and troubleshoot it.

Save:

``` text
lab-14-ipv6-challenge.pkt
```

------------------------------------------------------------------------

# Lab Completion Checklist

-   [ ] Inspected Windows IPv6
-   [ ] Tested IPv6 loopback
-   [ ] Classified IPv6 address types
-   [ ] Practiced compression
-   [ ] Practiced expansion
-   [ ] Built IPv6 LAN
-   [ ] Observed link-local addressing
-   [ ] Used Simulation Mode
-   [ ] Compared ARP and NDP
-   [ ] Built routed IPv6 network
-   [ ] Diagnosed wrong IPv6 prefix
-   [ ] Completed knowledge check
-   [ ] Completed challenge

------------------------------------------------------------------------

# Lab Complete

You have completed **Lab 14 --- IPv6 Fundamentals**.

# Next Lesson

➡️ **[Lesson 15 --- IP Addressing
Troubleshooting](../lessons/lesson-15-ip-addressing-troubleshooting.md)**
