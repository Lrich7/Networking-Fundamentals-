# Lesson 12 --- Subnet Masks and CIDR

## Learning Objectives

By the end of this lesson, you will be able to:

-   Explain binary place values used in IPv4.
-   Convert common octet values between binary and decimal.
-   Explain how a subnet mask separates network and host bits.
-   Explain CIDR prefix notation.
-   Recognize common subnet masks and prefixes.
-   Determine network and broadcast addresses for common prefixes.
-   Calculate usable host counts for typical IPv4 subnets.
-   Identify whether two IPv4 addresses are in the same subnet.

------------------------------------------------------------------------

# Why Subnet Masks Matter

An IPv4 address alone does not tell a host where its local network ends.

Example:

``` text
192.168.10.25
```

You also need the prefix:

``` text
192.168.10.25/24
```

The `/24` tells you how many bits represent the network portion.

------------------------------------------------------------------------

# Binary Refresher

Each IPv4 octet contains 8 bits.

Binary place values:

``` text
128 64 32 16 8 4 2 1
```

Example:

``` text
11111111 = 255
```

because:

``` text
128+64+32+16+8+4+2+1 = 255
```

------------------------------------------------------------------------

# Common Binary Values

Useful values to recognize:

``` text
00000000 = 0
10000000 = 128
11000000 = 192
11100000 = 224
11110000 = 240
11111000 = 248
11111100 = 252
11111110 = 254
11111111 = 255
```

These values appear frequently in subnet masks.

------------------------------------------------------------------------

# CIDR Prefix Length

CIDR notation uses a slash followed by the number of network bits.

Examples:

``` text
/8
/16
/24
/25
/26
/27
/28
/29
/30
```

------------------------------------------------------------------------

# Common Prefixes

``` text
/8   = 255.0.0.0
/16  = 255.255.0.0
/24  = 255.255.255.0
/25  = 255.255.255.128
/26  = 255.255.255.192
/27  = 255.255.255.224
/28  = 255.255.255.240
/29  = 255.255.255.248
/30  = 255.255.255.252
```

These are worth becoming comfortable with.

------------------------------------------------------------------------

# Network Bits and Host Bits

IPv4 has 32 total bits.

For a `/24`:

``` text
Network bits = 24
Host bits    = 8
```

For a `/26`:

``` text
Network bits = 26
Host bits    = 6
```

------------------------------------------------------------------------

# Host Count Formula

For traditional IPv4 subnets where network and broadcast addresses are
reserved:

``` text
Usable Hosts = 2^(host bits) - 2
```

Example `/24`:

``` text
Host bits = 8
2^8 - 2
256 - 2
254 usable hosts
```

Example `/26`:

``` text
Host bits = 6
2^6 - 2
64 - 2
62 usable hosts
```

There are special cases such as `/31` and `/32`, but they are outside
this beginner calculation rule and can be learned later.

------------------------------------------------------------------------

# Block Size Method

For common subnetting in one octet:

``` text
Block Size = 256 - mask value
```

Example `/26`:

``` text
Mask = 255.255.255.192

256 - 192 = 64
```

Subnets therefore begin every 64 addresses:

``` text
0
64
128
192
```

------------------------------------------------------------------------

# Example --- /26

Network:

``` text
192.168.10.0/26
```

Range:

``` text
Network:   192.168.10.0
Hosts:     192.168.10.1 – 192.168.10.62
Broadcast: 192.168.10.63
```

Next subnet:

``` text
192.168.10.64/26
```

------------------------------------------------------------------------

# Same Subnet?

Consider:

``` text
192.168.10.20/24
192.168.10.200/24
```

Both are within:

``` text
192.168.10.0/24
```

They are in the same subnet.

Now:

``` text
192.168.10.20/26
192.168.10.200/26
```

The first is in:

``` text
192.168.10.0/26
```

The second is in:

``` text
192.168.10.192/26
```

They are not in the same subnet.

------------------------------------------------------------------------

# Why Subnetting Exists

Subnetting helps organizations:

``` text
Separate networks
Control broadcast domains
Organize departments/sites
Apply security boundaries
Use address space efficiently
Support routing
```

You will practice designing subnets in Lesson 13.

------------------------------------------------------------------------

# Key Terms

``` text
Binary
Subnet Mask
CIDR
Prefix Length
Network Bits
Host Bits
Block Size
Network Address
Broadcast Address
Usable Host Range
```

------------------------------------------------------------------------

# Knowledge Check

1.  How many bits are in one IPv4 octet?
2.  What decimal value is `11111111`?
3.  What subnet mask is `/24`?
4.  What subnet mask is `/26`?
5.  How many host bits are in a `/26`?
6.  How many traditional usable hosts are in a `/26`?
7.  What is the block size of a `/26`?

------------------------------------------------------------------------

# Lesson Summary

Subnetting becomes easier when you know:

``` text
Prefix
   ↓
Subnet Mask
   ↓
Host Bits
   ↓
Block Size
   ↓
Network
   ↓
Host Range
   ↓
Broadcast
```

------------------------------------------------------------------------

# Hands-On Lab

➡️ **[Lab 12 --- Subnet Masks and
CIDR](../labs/lab-12-subnet-masks-and-cidr.md)**
