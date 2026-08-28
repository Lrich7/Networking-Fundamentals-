# Lesson 11 --- IPv4 Addressing

## Learning Objectives

By the end of this lesson, you will be able to:

-   Explain the purpose of an IPv4 address.
-   Recognize dotted-decimal IPv4 notation.
-   Explain network and host portions at a beginner level.
-   Recognize private, public, loopback, APIPA, and special-use
    addresses.
-   Explain the purpose of a subnet mask and prefix length.
-   Identify a default gateway.
-   Inspect IPv4 configuration in Windows and PowerShell.
-   Recognize common IPv4 configuration problems.

------------------------------------------------------------------------

# What Is an IPv4 Address?

An IPv4 address is a logical Layer 3 address used to identify an
interface on an IPv4 network.

Example:

``` text
192.168.10.25
```

IPv4 addresses contain:

``` text
32 bits
```

They are normally written as four decimal octets:

``` text
192 . 168 . 10 . 25
```

Each octet represents 8 bits and ranges from:

``` text
0–255
```

------------------------------------------------------------------------

# IPv4 and the OSI Model

IPv4 operates at:

``` text
OSI Layer 3 — Network
```

Compare:

``` text
MAC Address → Layer 2
IPv4 Address → Layer 3
```

MAC addresses help with local frame delivery.

IPv4 addresses allow logical addressing and routing between networks.

------------------------------------------------------------------------

# Network and Host Portions

An IPv4 address works with a subnet mask or prefix length.

Example:

``` text
IP Address: 192.168.10.25
Prefix:     /24
```

A `/24` means the first 24 bits identify the network portion.

Conceptually:

``` text
192.168.10 | .25
 Network      Host
```

You will calculate this more deeply in Lesson 12.

------------------------------------------------------------------------

# Subnet Masks

A subnet mask identifies which portion of an IPv4 address represents the
network.

Example:

``` text
255.255.255.0
```

This is equivalent to:

``` text
/24
```

Common examples:

``` text
255.0.0.0       = /8
255.255.0.0     = /16
255.255.255.0   = /24
```

------------------------------------------------------------------------

# Default Gateway

A host uses its default gateway to reach destinations outside its local
IP network.

Example:

``` text
PC
IP:      192.168.10.25
Mask:    255.255.255.0
Gateway: 192.168.10.1
```

Traffic for another network is normally sent toward:

``` text
192.168.10.1
```

------------------------------------------------------------------------

# Private IPv4 Address Ranges

Private IPv4 addresses are intended for private/internal networks.

The three private ranges are:

``` text
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

These addresses are not routed across the public Internet as normal
public destinations.

Organizations commonly use NAT when private hosts access the Internet.

NAT will be covered later.

------------------------------------------------------------------------

# Public IPv4 Addresses

Public IPv4 addresses are globally routable addresses assigned for
Internet use, subject to allocation and routing policies.

Do not assume that every address outside the private ranges is
automatically usable by you. Many ranges have special purposes or are
reserved.

------------------------------------------------------------------------

# Loopback

IPv4 loopback addresses are within:

``` text
127.0.0.0/8
```

The most familiar address is:

``` text
127.0.0.1
```

Test:

``` text
ping 127.0.0.1
```

This tests the local TCP/IP stack, not the physical network.

------------------------------------------------------------------------

# APIPA / Link-Local IPv4

Windows may self-assign an address in:

``` text
169.254.0.0/16
```

when automatic IPv4 configuration is expected but DHCP is unavailable.

Example:

``` text
169.254.25.80
```

Seeing a `169.254.x.x` address on a corporate workstation can be an
important troubleshooting clue.

It often suggests:

``` text
DHCP was expected
        ↓
DHCP assignment failed
```

------------------------------------------------------------------------

# Network and Broadcast Addresses

Within a traditional IPv4 subnet, some addresses have special roles.

For:

``` text
192.168.10.0/24
```

typically:

``` text
Network address:   192.168.10.0
Usable hosts:      192.168.10.1 – 192.168.10.254
Broadcast address: 192.168.10.255
```

Do not assign the network or broadcast address to a normal host in this
example.

------------------------------------------------------------------------

# Duplicate IP Addresses

Two devices using the same IPv4 address can cause connectivity problems.

Possible symptoms include:

``` text
Intermittent connectivity
Address conflict warning
Unexpected ARP behavior
One device works while another fails
```

Every host interface in the same IP network should have an appropriate
unique address.

------------------------------------------------------------------------

# Inspect IPv4 in Windows

Command Prompt:

``` text
ipconfig
```

More detail:

``` text
ipconfig /all
```

PowerShell:

``` powershell
Get-NetIPConfiguration
```

IPv4-specific information:

``` powershell
Get-NetIPAddress -AddressFamily IPv4
```

------------------------------------------------------------------------

# Basic IPv4 Troubleshooting

Check:

``` text
Adapter connected?
      ↓
IPv4 address present?
      ↓
Correct subnet/prefix?
      ↓
Correct default gateway?
      ↓
Duplicate address?
      ↓
Can ping local host?
      ↓
Can ping gateway?
      ↓
Can reach remote IP?
```

------------------------------------------------------------------------

# Key Terms

``` text
IPv4
Octet
Subnet Mask
Prefix Length
Default Gateway
Private Address
Public Address
Loopback
APIPA
Network Address
Broadcast Address
Duplicate IP
```

------------------------------------------------------------------------

# Knowledge Check

1.  How many bits are in an IPv4 address?
2.  Which OSI layer uses IPv4?
3.  What is the purpose of a subnet mask?
4.  Name the three private IPv4 ranges.
5.  What does `127.0.0.1` represent?
6.  What might a `169.254.x.x` address indicate?
7.  What is the purpose of a default gateway?

------------------------------------------------------------------------

# Lesson Summary

An IPv4 configuration normally requires you to understand:

``` text
IP Address
    +
Subnet Mask / Prefix
    +
Default Gateway
    +
DNS information
```

The IP address alone is not enough to fully understand a host's network
configuration.

------------------------------------------------------------------------

# Hands-On Lab

➡️ **[Lab 11 --- IPv4 Addressing](../labs/lab-11-ipv4-addressing.md)**
