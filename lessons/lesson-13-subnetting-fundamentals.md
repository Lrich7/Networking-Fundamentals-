# Lesson 13 --- Subnetting Fundamentals

## Learning Objectives

By the end of this lesson, you will be able to:

-   Explain why networks are subnetted.
-   Determine the number of required subnets or hosts.
-   Select an appropriate prefix for common small-network requirements.
-   Calculate subnet boundaries using block size.
-   Identify network, broadcast, and usable host ranges.
-   Create a simple fixed-length subnetting plan.
-   Recognize common subnetting mistakes.
-   Validate a subnet plan before deployment.

------------------------------------------------------------------------

# Why Subnet a Network?

Instead of placing every device into one large network, administrators
divide address space into smaller subnets.

Benefits include:

``` text
Organization
Smaller broadcast domains
Routing boundaries
Security design
Department/site separation
Address management
Troubleshooting
```

------------------------------------------------------------------------

# Start with Requirements

Do not begin subnetting by randomly choosing a mask.

Ask:

``` text
How many networks do I need?
How many hosts does each network need?
Will the environment grow?
Are router/gateway addresses required?
Are infrastructure addresses required?
```

------------------------------------------------------------------------

# Choosing by Host Requirement

For traditional IPv4 subnet calculations:

``` text
Usable hosts = 2^(host bits) - 2
```

Useful examples:

``` text
/25 → 126 usable hosts
/26 → 62 usable hosts
/27 → 30 usable hosts
/28 → 14 usable hosts
/29 → 6 usable hosts
/30 → 2 usable hosts
```

Choose a subnet large enough for the requirement plus reasonable growth.

------------------------------------------------------------------------

# Example Requirement

You need four equal networks, each supporting up to 50 hosts.

Starting network:

``` text
192.168.130.0/24
```

A `/26` provides:

``` text
62 usable hosts
```

and creates four equal `/26` subnets from the `/24`.

------------------------------------------------------------------------

# /26 Plan

Block size:

``` text
256 - 192 = 64
```

Subnets:

``` text
192.168.130.0/26
192.168.130.64/26
192.168.130.128/26
192.168.130.192/26
```

------------------------------------------------------------------------

# First /26

``` text
Network:   192.168.130.0
Hosts:     192.168.130.1 – 192.168.130.62
Broadcast: 192.168.130.63
```

Second:

``` text
Network:   192.168.130.64
Hosts:     192.168.130.65 – 192.168.130.126
Broadcast: 192.168.130.127
```

Continue the same pattern.

------------------------------------------------------------------------

# Fixed-Length Subnetting

When every subnet uses the same prefix, the design uses **Fixed Length
Subnet Masking (FLSM)**.

Example:

``` text
Department A → /26
Department B → /26
Department C → /26
Department D → /26
```

This is simple and predictable.

------------------------------------------------------------------------

# VLSM Preview

Real networks often need different subnet sizes.

Example:

``` text
Users      → 100 hosts
Servers    → 20 hosts
Printers   → 10 hosts
WAN link   → 2 addresses
```

Using different subnet sizes is called **Variable Length Subnet Masking
(VLSM)**.

We will keep Section 3 focused primarily on solid subnetting
fundamentals, but you should recognize the term.

------------------------------------------------------------------------

# Common Mistakes

## Mistake 1 --- Using Network Address as a Host

For:

``` text
192.168.130.64/26
```

do not normally assign:

``` text
192.168.130.64
```

to an endpoint.

------------------------------------------------------------------------

# Mistake 2 --- Using Broadcast Address

Do not normally assign:

``` text
192.168.130.127
```

in that subnet.

------------------------------------------------------------------------

# Mistake 3 --- Too Few Hosts

If you need 40 hosts, `/27` is too small because it traditionally
provides only:

``` text
30 usable hosts
```

------------------------------------------------------------------------

# Mistake 4 --- Overlapping Subnets

Subnets must not overlap.

Incorrect planning can create ambiguous addressing and routing problems.

------------------------------------------------------------------------

# Mistake 5 --- Forgetting Growth

If a department has 29 devices today, a `/27` with 30 traditional usable
addresses leaves almost no room.

Plan with realistic growth in mind.

------------------------------------------------------------------------

# A Repeatable Subnetting Process

Use:

``` text
1. Identify requirements
2. Determine required host bits
3. Select prefix
4. Find subnet mask
5. Calculate block size
6. List network boundaries
7. Determine host ranges
8. Determine broadcasts
9. Validate no overlap
10. Document
```

------------------------------------------------------------------------

# Key Terms

``` text
Subnetting
FLSM
VLSM
Host Requirement
Subnet Requirement
Block Size
Network Address
Broadcast Address
Usable Range
Overlapping Subnet
```

------------------------------------------------------------------------

# Knowledge Check

1.  Why do administrators subnet networks?
2.  How many traditional usable hosts are in a `/27`?
3.  Which is large enough for 50 hosts: `/27` or `/26`?
4.  What does FLSM mean?
5.  Why should growth be considered?
6.  What happens if two subnets overlap?

------------------------------------------------------------------------

# Lesson Summary

Subnetting is a planning process.

``` text
Requirements
    ↓
Prefix
    ↓
Block Size
    ↓
Subnet Boundaries
    ↓
Host Ranges
    ↓
Documentation
```

Accuracy matters more than speed.

------------------------------------------------------------------------

# Hands-On Lab

➡️ **[Lab 13 --- Subnetting
Fundamentals](../labs/lab-13-subnetting-fundamentals.md)**
