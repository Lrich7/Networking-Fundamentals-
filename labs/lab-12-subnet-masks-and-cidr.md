# Lab 12 --- Subnet Masks and CIDR

## Lab Objective

Practice binary values, CIDR notation, subnet masks, host counts, block
sizes, and identifying IPv4 subnet boundaries.

------------------------------------------------------------------------

# Part 1 --- Binary Place Values

Fill in:

``` text
128  64  32  16  8  4  2  1
 _    _   _   _   _  _  _  _
```

Convert:

``` text
10000000 = ______
11000000 = ______
11100000 = ______
11110000 = ______
11111100 = ______
```

------------------------------------------------------------------------

# Part 2 --- Prefix to Mask

Fill in:

``` text
/8  = __________________
/16 = __________________
/24 = __________________
/25 = __________________
/26 = __________________
/27 = __________________
/28 = __________________
```

------------------------------------------------------------------------

# Part 3 --- Host Bits

Calculate:

``` text
/24 → ______ host bits
/25 → ______ host bits
/26 → ______ host bits
/27 → ______ host bits
/28 → ______ host bits
```

------------------------------------------------------------------------

# Part 4 --- Usable Host Counts

Using:

``` text
2^(host bits) - 2
```

calculate:

``` text
/24 → ______ usable hosts
/25 → ______ usable hosts
/26 → ______ usable hosts
/27 → ______ usable hosts
/28 → ______ usable hosts
```

------------------------------------------------------------------------

# Part 5 --- Block Sizes

Calculate:

``` text
/25 mask last octet = 128 → block size ______
/26 mask last octet = 192 → block size ______
/27 mask last octet = 224 → block size ______
/28 mask last octet = 240 → block size ______
```

------------------------------------------------------------------------

# Part 6 --- Find /26 Subnets

For:

``` text
192.168.120.0/24
```

split it into `/26` networks.

Fill in:

``` text
Subnet 1: __________________
Subnet 2: __________________
Subnet 3: __________________
Subnet 4: __________________
```

For each, identify network and broadcast.

------------------------------------------------------------------------

# Part 7 --- Address Analysis

For:

``` text
192.168.120.70/26
```

determine:

``` text
Subnet mask: ___________________________
Network address: _______________________
First host: ____________________________
Last host: _____________________________
Broadcast: _____________________________
```

------------------------------------------------------------------------

# Part 8 --- Same Subnet Exercise

Are these pairs in the same subnet?

## A

``` text
192.168.1.10/24
192.168.1.200/24
```

``` text
Same subnet? Yes / No
```

## B

``` text
192.168.1.10/26
192.168.1.100/26
```

``` text
Same subnet? Yes / No
```

## C

``` text
10.10.10.130/25
10.10.10.200/25
```

``` text
Same subnet? Yes / No
```

------------------------------------------------------------------------

# Part 9 --- Packet Tracer Test

Build:

``` text
PC0 ── Switch ── PC1
```

Configure:

``` text
PC0 192.168.121.10 /26
PC1 192.168.121.20 /26
```

Test connectivity.

Then change PC1 to:

``` text
192.168.121.70 /26
```

Without a router, test again.

Explain why the result changes.

------------------------------------------------------------------------

# Part 10 --- Prefix Mistake

Configure:

``` text
PC0 192.168.122.10 /24
PC1 192.168.122.200 /26
```

Think carefully about how each host interprets the local network.

What problem can inconsistent masks create?

``` text
____________________________________________________
```

Restore matching masks.

------------------------------------------------------------------------

# Knowledge Check

1.  What is `/27` in dotted decimal?
2.  How many host bits are in `/27`?
3.  What is the block size of `/27`?
4.  How many traditional usable hosts are in `/28`?
5.  Why must hosts use the correct subnet mask?

------------------------------------------------------------------------

# Challenge

Analyze:

``` text
172.16.50.150/27
```

Determine:

``` text
Subnet mask
Network address
First usable host
Last usable host
Broadcast address
Usable host count
```

Then verify your reasoning by building a small Packet Tracer network
with two hosts inside that subnet and one host outside it.

Save:

``` text
lab-12-cidr-challenge.pkt
```

------------------------------------------------------------------------

# Lab Completion Checklist

-   [ ] Practiced binary values
-   [ ] Converted prefixes to masks
-   [ ] Calculated host bits
-   [ ] Calculated usable host counts
-   [ ] Calculated block sizes
-   [ ] Identified /26 subnet boundaries
-   [ ] Analyzed a host address
-   [ ] Compared same/different subnets
-   [ ] Tested subnets in Packet Tracer
-   [ ] Investigated inconsistent masks
-   [ ] Completed knowledge check
-   [ ] Completed challenge

------------------------------------------------------------------------

# Lab Complete

You have completed **Lab 12 --- Subnet Masks and CIDR**.

# Next Lesson

➡️ **[Lesson 13 --- Subnetting
Fundamentals](../lessons/lesson-13-subnetting-fundamentals.md)**
