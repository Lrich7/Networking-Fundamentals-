# Lab 13 --- Subnetting Fundamentals

## Lab Objective

Design IPv4 subnets from requirements, document the results, and
validate them with Cisco Packet Tracer.

------------------------------------------------------------------------

# Part 1 --- Choose a Prefix

Choose the smallest listed subnet that supports the requirement.

Options:

``` text
/25 = 126 hosts
/26 = 62 hosts
/27 = 30 hosts
/28 = 14 hosts
/29 = 6 hosts
```

Requirements:

``` text
10 hosts → ______
25 hosts → ______
50 hosts → ______
100 hosts → ______
5 hosts → ______
```

------------------------------------------------------------------------

# Part 2 --- Split a /24 into Four Networks

Starting network:

``` text
192.168.130.0/24
```

Create four equal subnets.

``` text
Prefix: __________________
Mask: ____________________
Block size: ______________
```

List all four network addresses.

------------------------------------------------------------------------

# Part 3 --- Complete the Table

For each subnet record:

``` text
Subnet 1
Network: __________________
First host: _______________
Last host: _________________
Broadcast: _________________

Subnet 2
Network: __________________
First host: _______________
Last host: _________________
Broadcast: _________________

Subnet 3
Network: __________________
First host: _______________
Last host: _________________
Broadcast: _________________

Subnet 4
Network: __________________
First host: _______________
Last host: _________________
Broadcast: _________________
```

------------------------------------------------------------------------

# Part 4 --- Department Plan

Assign the four subnets to:

``` text
Administration
Sales
Operations
IT
```

Choose the first usable address of each subnet as the future gateway.

Document each gateway.

------------------------------------------------------------------------

# Part 5 --- Build Two Subnets

In Packet Tracer create:

``` text
PC0 ── Switch0 ── Router ── Switch1 ── PC2
PC1 ──┘                       └── PC3
```

Use the first two subnets from your plan.

Configure the router with one interface in each subnet.

Use valid host addresses.

------------------------------------------------------------------------

# Part 6 --- Test Local Communication

Test:

``` text
PC0 → PC1
PC2 → PC3
```

Both should communicate locally if configured correctly.

------------------------------------------------------------------------

# Part 7 --- Test Routed Communication

After router interfaces and gateways are correctly configured, test:

``` text
PC0 → PC2
```

Record the path conceptually:

``` text
PC0 → __________ → Router → __________ → PC2
```

------------------------------------------------------------------------

# Part 8 --- Wrong Mask Failure

Give PC1 an incorrect subnet mask.

Test communication.

Record:

``` text
Incorrect mask: __________________________
Symptom: _________________________________
Fix: ____________________________________
```

Restore it.

------------------------------------------------------------------------

# Part 9 --- Wrong Gateway Failure

Give PC0 an incorrect gateway.

Test:

``` text
PC0 → PC1
PC0 → PC2
```

Which test may still work?

``` text
____________________________________
```

Why?

``` text
____________________________________
```

Restore the gateway.

------------------------------------------------------------------------

# Part 10 --- Address Planning Scenario

You need:

``` text
Network A: 45 hosts
Network B: 20 hosts
Network C: 12 hosts
```

For each, choose a reasonable prefix.

``` text
A: ______
B: ______
C: ______
```

You do not need to perform a full VLSM allocation yet.

------------------------------------------------------------------------

# Part 11 --- Validate the Plan

Check:

``` text
[ ] No network address assigned to hosts
[ ] No broadcast address assigned to hosts
[ ] No duplicate addresses
[ ] No overlapping subnets
[ ] Correct gateway in each subnet
[ ] Enough usable addresses
```

------------------------------------------------------------------------

# Knowledge Check

1.  What prefix supports 50 traditional usable hosts?
2.  What prefix supports 25 hosts?
3.  Why does a host need a gateway to reach another subnet?
4.  Can two subnets overlap?
5.  Why might a local ping work even if the default gateway is wrong?

------------------------------------------------------------------------

# Challenge

Starting with:

``` text
10.10.20.0/24
```

create eight equal subnets.

For each, determine:

``` text
Network
First host
Last host
Broadcast
Prefix
Mask
```

Then build two of those subnets in Packet Tracer and route between them.

Save:

``` text
lab-13-subnetting-challenge.pkt
```

------------------------------------------------------------------------

# Lab Completion Checklist

-   [ ] Selected prefixes by host requirement
-   [ ] Split a /24 into four networks
-   [ ] Calculated host ranges
-   [ ] Created department plan
-   [ ] Built two subnets
-   [ ] Tested local communication
-   [ ] Tested routed communication
-   [ ] Diagnosed wrong mask
-   [ ] Diagnosed wrong gateway
-   [ ] Completed address-planning scenario
-   [ ] Validated subnet plan
-   [ ] Completed knowledge check
-   [ ] Completed challenge

------------------------------------------------------------------------

# Lab Complete

You have completed **Lab 13 --- Subnetting Fundamentals**.

# Next Lesson

➡️ **[Lesson 14 --- IPv6
Fundamentals](../lessons/lesson-14-ipv6-fundamentals.md)**
