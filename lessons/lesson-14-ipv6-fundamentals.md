# Lesson 14 --- IPv6 Fundamentals

## Learning Objectives

By the end of this lesson, you will be able to:

-   Explain why IPv6 was developed.
-   Recognize IPv6 hexadecimal notation.
-   Explain IPv6 address compression rules.
-   Recognize global unicast, link-local, loopback, and multicast
    addresses.
-   Explain the purpose of a `/64` on common IPv6 LANs.
-   Explain that IPv6 does not use broadcast.
-   Explain that IPv6 uses Neighbor Discovery instead of ARP.
-   Inspect IPv6 configuration in Windows.
-   Configure and test basic IPv6 addresses in Cisco Packet Tracer.

------------------------------------------------------------------------

# Why IPv6?

IPv4 uses 32-bit addresses.

IPv6 uses:

``` text
128-bit addresses
```

IPv6 was developed in part to provide an enormously larger address space
and modernize IP networking.

------------------------------------------------------------------------

# IPv6 Format

An IPv6 address is written in hexadecimal.

Example:

``` text
2001:db8:1234:5678:abcd:ef01:2345:6789
```

There are eight groups called **hextets**, each representing 16 bits.

------------------------------------------------------------------------

# Hexadecimal

Hexadecimal uses:

``` text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

You do not need advanced hexadecimal math for this lesson.

You should become comfortable recognizing IPv6 addresses.

------------------------------------------------------------------------

# Leading Zero Compression

Leading zeros within a hextet can be omitted.

Example:

``` text
2001:0db8:0000:0001:0000:0000:0000:0010
```

can become:

``` text
2001:db8:0:1:0:0:0:10
```

------------------------------------------------------------------------

# Double-Colon Compression

One continuous sequence of all-zero hextets can be replaced with:

``` text
::
```

Example:

``` text
2001:db8:0:1:0:0:0:10
```

can become:

``` text
2001:db8:0:1::10
```

Use `::` only once in an IPv6 address so the omitted groups can be
determined unambiguously.

------------------------------------------------------------------------

# IPv6 Prefix Length

IPv6 also uses CIDR-style prefix notation.

Example:

``` text
2001:db8:100:1::10/64
```

A `/64` is extremely common on IPv6 LANs.

Do not apply the IPv4 `2^hostbits - 2` host-count rule to IPv6 LAN
planning.

------------------------------------------------------------------------

# Global Unicast

Global unicast addresses are generally analogous to publicly routable
IPv4 unicast addresses.

A major global unicast allocation range is:

``` text
2000::/3
```

------------------------------------------------------------------------

# Documentation Prefix

For examples and documentation, use:

``` text
2001:db8::/32
```

This range is reserved for documentation.

That is why it is useful in public training repositories.

------------------------------------------------------------------------

# Link-Local

IPv6 interfaces normally use link-local addressing.

Link-local addresses are within:

``` text
fe80::/10
```

They are used for communication on the local link and are important to
IPv6 operation.

------------------------------------------------------------------------

# Loopback

IPv6 loopback:

``` text
::1
```

Compare:

``` text
IPv4 loopback → 127.0.0.1
IPv6 loopback → ::1
```

------------------------------------------------------------------------

# Multicast

IPv6 uses multicast extensively.

Multicast addresses begin with:

``` text
ff00::/8
```

------------------------------------------------------------------------

# No IPv6 Broadcast

IPv6 does not use broadcast the way IPv4 does.

Instead, IPv6 uses mechanisms including multicast.

Remember:

``` text
IPv4 → Broadcast exists
IPv6 → No broadcast
```

------------------------------------------------------------------------

# Neighbor Discovery

IPv6 does not use ARP.

It uses **Neighbor Discovery Protocol (NDP)**, which is based on ICMPv6.

NDP performs functions such as:

``` text
Neighbor discovery
Router discovery
Address resolution
Reachability information
```

------------------------------------------------------------------------

# IPv6 Address Configuration

IPv6 hosts may obtain addressing through mechanisms including:

``` text
Static configuration
SLAAC
DHCPv6
```

You will encounter these more later.

------------------------------------------------------------------------

# Dual Stack

Many networks run:

``` text
IPv4 + IPv6
```

at the same time.

This is called **dual stack**.

Do not assume IPv6 is disabled just because an organization primarily
discusses IPv4.

------------------------------------------------------------------------

# Inspect IPv6 in Windows

``` powershell
Get-NetIPAddress -AddressFamily IPv6
```

and:

``` powershell
Get-NetIPConfiguration
```

Command Prompt:

``` text
ipconfig /all
```

------------------------------------------------------------------------

# Test IPv6 Loopback

``` text
ping ::1
```

This tests the local IPv6 stack.

------------------------------------------------------------------------

# Key Terms

``` text
IPv6
128-bit
Hexadecimal
Hextet
Prefix
/64
Global Unicast
Link-Local
Loopback
Multicast
NDP
SLAAC
DHCPv6
Dual Stack
```

------------------------------------------------------------------------

# Knowledge Check

1.  How many bits are in an IPv6 address?
2.  What numbering system does IPv6 use?
3.  What is the IPv6 loopback address?
4.  What prefix identifies link-local IPv6 addresses?
5.  Does IPv6 use broadcast?
6.  What replaces ARP in IPv6?
7.  What documentation prefix should be used in examples?

------------------------------------------------------------------------

# Lesson Summary

Remember the core IPv6 anchors:

``` text
128 bits
Hexadecimal
/64 common on LANs
fe80:: → link-local
::1 → loopback
No broadcast
NDP instead of ARP
```

------------------------------------------------------------------------

# Hands-On Lab

➡️ **[Lab 14 --- IPv6
Fundamentals](../labs/lab-14-ipv6-fundamentals.md)**
