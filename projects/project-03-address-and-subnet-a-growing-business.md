# Project 03 --- Address and Subnet a Growing Business

## Project Overview

You have completed Section 3 --- **IP Addressing & Subnetting**.

Now design the addressing plan for a growing small business.

This project is intentionally less guided than the labs. You will
receive requirements, choose subnet sizes, document your work, build
representative networks in Cisco Packet Tracer, and troubleshoot faults.

------------------------------------------------------------------------

# Scenario

A company has been using one large flat network.

Growth has made the network harder to manage.

Management wants separate IPv4 networks for:

``` text
Administration — 45 devices
Operations     — 50 devices
IT             — 20 devices
Servers        — 12 devices
```

The company has been allocated this private training block:

``` text
192.168.160.0/23
```

For this project, create a simple, clearly documented subnet plan that
provides enough room for each group.

You will also add IPv6 documentation prefixes for the major networks.

------------------------------------------------------------------------

# Project Objectives

You will demonstrate:

-   IPv4 subnet planning.
-   CIDR and subnet-mask calculation.
-   Host-capacity planning.
-   Network/broadcast identification.
-   Default-gateway planning.
-   Routed subnet configuration.
-   IPv6 `/64` planning.
-   IPv4 and IPv6 testing.
-   Addressing troubleshooting.
-   Technical documentation.

------------------------------------------------------------------------

# Part 1 --- Review Requirements

Record:

``` text
Administration hosts: 45
Operations hosts: 50
IT hosts: 20
Servers hosts: 12
```

Add reasonable growth estimates.

``` text
Administration future target: ______________
Operations future target: __________________
IT future target: __________________________
Servers future target: _____________________
```

------------------------------------------------------------------------

# Part 2 --- Choose IPv4 Prefixes

Choose an appropriate subnet size for each department.

Do not choose a subnet that barely supports the current requirement if
reasonable growth would immediately exhaust it.

Document:

``` text
Administration prefix: _____________________
Operations prefix: _________________________
IT prefix: _________________________________
Servers prefix: ____________________________
```

------------------------------------------------------------------------

# Part 3 --- Create the IPv4 Plan

Starting block:

``` text
192.168.160.0/23
```

Create non-overlapping subnets.

For each network document:

``` text
Department:
Network:
Prefix:
Subnet mask:
Gateway:
First usable:
Last usable:
Broadcast:
Usable host capacity:
```

You may use equal-size subnets for simplicity if they fit cleanly, or
apply different sizes if you are comfortable with VLSM.

Accuracy and documentation matter more than minimizing every unused
address.

------------------------------------------------------------------------

# Part 4 --- Validate the Plan

Before building anything, confirm:

``` text
[ ] Every subnet fits inside 192.168.160.0/23
[ ] No subnets overlap
[ ] Every subnet supports its required hosts
[ ] Gateway is a valid host address
[ ] Network address is not assigned to a host
[ ] Broadcast address is not assigned to a host
[ ] Growth has been considered
```

------------------------------------------------------------------------

# Part 5 --- Build a Representative Topology

In Packet Tracer build at least:

``` text
2 Administration PCs
2 Operations PCs
2 IT PCs
1 Server
Appropriate switches
Router or Layer 3 routing device
```

Conceptually:

``` text
Administration ── Switch ──┐
Operations ───── Switch ───┤
IT ───────────── Switch ───┼── Router / Layer 3 Device
Servers ──────── Switch ───┘
```

Use the routing method appropriate to what you have learned so far.

------------------------------------------------------------------------

# Part 6 --- Configure IPv4

Configure each representative host with:

``` text
Valid IPv4 address
Correct prefix/mask
Correct gateway
```

Configure the routing interfaces.

------------------------------------------------------------------------

# Part 7 --- Test IPv4

Verify:

``` text
Same-subnet communication
Administration → Operations
Administration → Server
Operations → Server
IT → Administration
IT → Server
```

Document pass/fail.

------------------------------------------------------------------------

# Part 8 --- Document Routing Logic

Explain:

``` text
Why can two hosts in the same subnet communicate without sending normal traffic through the default gateway?

____________________________________________________

Why is the gateway required between subnets?

____________________________________________________
```

------------------------------------------------------------------------

# Part 9 --- Add IPv6 Plan

Use documentation space.

Example structure:

``` text
Administration → 2001:db8:160:1::/64
Operations     → 2001:db8:160:2::/64
IT             → 2001:db8:160:3::/64
Servers        → 2001:db8:160:4::/64
```

You may use this plan or create another valid documentation-based plan.

Document the router/gateway address you will use in each `/64`.

------------------------------------------------------------------------

# Part 10 --- Configure Representative IPv6

Configure IPv6 on at least:

``` text
1 Administration PC
1 Operations PC
1 IT PC
1 Server
Routing interfaces
```

Verify local and routed IPv6 communication.

------------------------------------------------------------------------

# Part 11 --- Compare IPv4 and IPv6

Complete:

``` text
IPv4 address size: ______________________
IPv6 address size: ______________________

IPv4 local resolution: __________________
IPv6 local resolution: __________________

IPv4 loopback: __________________________
IPv6 loopback: __________________________

IPv4 broadcast exists? __________________
IPv6 broadcast exists? __________________
```

------------------------------------------------------------------------

# Part 12 --- Failure 1: Wrong IPv4 Address

Give one Administration host an address from the Operations subnet.

Ticket:

> "The computer is connected but cannot reach its department resources."

Troubleshoot and document:

``` text
Symptom:
Scope:
Observed configuration:
Expected configuration:
Root cause:
Fix:
Verification:
```

------------------------------------------------------------------------

# Part 13 --- Failure 2: Wrong Prefix

Give one IT host the wrong subnet mask/prefix.

Do not immediately look at your address table.

Calculate the correct prefix from the subnet plan.

Repair and verify.

------------------------------------------------------------------------

# Part 14 --- Failure 3: Wrong Gateway

Give a Server host an incorrect gateway.

Test:

``` text
Server → another server-side/local host if present
Server → Administration host
```

Explain the different results.

------------------------------------------------------------------------

# Part 15 --- Failure 4: Duplicate IPv4

In the isolated lab only, create a duplicate IPv4 address.

Use:

``` text
ARP information
Switch MAC information
Observed connectivity
```

to help diagnose it.

Restore unique addressing.

------------------------------------------------------------------------

# Part 16 --- Failure 5: IPv6

Give one IPv6 host an address from the wrong `/64`.

Diagnose and repair it.

Document the relevant:

``` text
IPv6 address
Prefix
Gateway/router
Expected network
```

------------------------------------------------------------------------

# Part 17 --- Help-Desk Scenario

Ticket:

> "The user's PC shows 169.254.73.20. Everyone else in the department is
> working."

Create a troubleshooting plan.

Do not simply write "restart DHCP."

Include:

``` text
Client interface
Cable/Wi-Fi
Switch path
Correct network/VLAN
DHCP process
Address renewal
Comparison with working client
```

------------------------------------------------------------------------

# Part 18 --- DNS Scenario

Ticket:

> "The user can reach a remote IP address but websites fail by name."

Write the commands you would use.

Include:

``` text
Resolve-DnsName
nslookup
Test-NetConnection
```

Explain why this may not be a subnetting failure.

------------------------------------------------------------------------

# Part 19 --- Final Addressing Document

Create a final table or clearly formatted section containing:

``` text
Department
IPv4 network
IPv4 prefix
Subnet mask
Gateway
Usable host range
Broadcast
Capacity
IPv6 /64
IPv6 gateway/router address
```

This should be clear enough that another technician could configure a
device without asking you what address range to use.

------------------------------------------------------------------------

# Part 20 --- Save

Save the Packet Tracer file as:

``` text
project-03-address-and-subnet-a-growing-business.pkt
```

Recommended repository location:

``` text
packet-tracer/projects/
```

Do not use real company addressing information in the public repository.

------------------------------------------------------------------------

# Final Validation

-   [ ] Requirements documented
-   [ ] Growth considered
-   [ ] IPv4 prefixes selected
-   [ ] All IPv4 subnets fit within the assigned block
-   [ ] No subnet overlap
-   [ ] Network/broadcast ranges calculated
-   [ ] Gateways documented
-   [ ] Representative topology built
-   [ ] Same-subnet IPv4 tested
-   [ ] Routed IPv4 tested
-   [ ] IPv6 plan created
-   [ ] IPv6 configured/tested
-   [ ] IPv4/IPv6 comparison completed
-   [ ] Wrong IPv4 address repaired
-   [ ] Wrong prefix repaired
-   [ ] Wrong gateway repaired
-   [ ] Duplicate IP diagnosed
-   [ ] Wrong IPv6 network repaired
-   [ ] APIPA ticket plan completed
-   [ ] DNS scenario completed
-   [ ] Final addressing documentation completed
-   [ ] `.pkt` file saved

------------------------------------------------------------------------

# Project Reflection

1.  Which subnet calculation was hardest?
2.  How did host requirements affect your prefix choices?
3.  Why is address documentation important?
4.  What symptoms can a wrong gateway produce?
5.  Why can an incorrect mask be harder to diagnose than a disconnected
    cable?
6.  What differences between IPv4 and IPv6 were most important?
7.  What would you change if the company doubled in size?

------------------------------------------------------------------------

# 🏆 Project Complete

You have completed **Project 03 --- Address and Subnet a Growing
Business**.

You have now applied:

``` text
IPv4 addressing
CIDR
Subnet masks
Subnet calculations
Address planning
Default gateways
Routing between subnets
IPv6
NDP concepts
Address troubleshooting
APIPA troubleshooting
DNS isolation
Network documentation
```

------------------------------------------------------------------------

# ➡️ Continue Training

Next:

➡️ **[Lesson 16 --- TCP, UDP, Ports, and
Protocols](../lessons/lesson-16-tcp-udp-ports-and-protocols.md)**
