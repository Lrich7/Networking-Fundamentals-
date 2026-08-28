# Lesson 07 --- MAC Addresses and ARP

## Learning Objectives

By the end of this lesson, you will be able to:

-   Explain the purpose and structure of MAC addresses.
-   Identify unicast, broadcast, and multicast MAC concepts.
-   Explain why IPv4 hosts use ARP.
-   Describe the ARP request and reply process.
-   Explain the relationship between IP addresses and MAC addresses.
-   Inspect ARP information in Windows.
-   Observe ARP in Cisco Packet Tracer.
-   Use ARP information during troubleshooting.

------------------------------------------------------------------------

# MAC Address Review

Ethernet interfaces use MAC addresses for local Layer 2 communication.

Example:

``` text
00-1A-2B-3C-4D-5E
```

A traditional Ethernet MAC address contains:

``` text
48 bits
12 hexadecimal characters
```

------------------------------------------------------------------------

# MAC Address Structure

A MAC address is often discussed in two portions:

``` text
Organizationally Unique Identifier (OUI)
        +
Device/interface-specific portion
```

The OUI can identify the organization to which a MAC address block was
assigned.

However, modern operating systems can use MAC randomization, and virtual
interfaces may use generated addresses. Do not assume a MAC always
proves the physical manufacturer.

------------------------------------------------------------------------

# Why Do We Need ARP?

Suppose PC0 wants to send IPv4 traffic to PC1.

PC0 knows:

``` text
PC1 IP = 192.168.70.20
```

But Ethernet needs a destination MAC address for the local frame.

PC0 needs to discover:

``` text
Which MAC address owns 192.168.70.20?
```

For IPv4, this is the job of **ARP --- Address Resolution Protocol**.

------------------------------------------------------------------------

# ARP Request

PC0 sends an ARP request asking:

``` text
Who has 192.168.70.20?
Tell 192.168.70.10
```

The request is broadcast on the local network.

Conceptually:

``` text
          ┌→ PC1
PC0 ──────┼→ PC2
          └→ Server
```

All local devices can receive the broadcast, but the device owning the
requested IPv4 address should answer.

------------------------------------------------------------------------

# ARP Reply

PC1 replies with its MAC address.

``` text
192.168.70.20 is at AA-BB-CC-DD-EE-FF
```

PC0 can then send an Ethernet frame directly to that MAC address.

------------------------------------------------------------------------

# ARP Cache

Hosts keep recently learned mappings in an **ARP cache**.

Conceptually:

``` text
IPv4 Address        MAC Address
192.168.70.20       AA-BB-CC-DD-EE-FF
192.168.70.30       11-22-33-44-55-66
```

This prevents a new ARP request from being required for every packet.

------------------------------------------------------------------------

# Inspect ARP in Windows

Command Prompt:

``` text
arp -a
```

PowerShell:

``` powershell
Get-NetNeighbor -AddressFamily IPv4
```

You may see entries for:

``` text
Default gateway
Other local hosts
Broadcast/multicast-related entries
```

------------------------------------------------------------------------

# ARP and Remote Networks

A host does **not** normally ARP for the MAC address of a remote
Internet server.

If the destination is remote:

``` text
PC
 ↓
Default Gateway
 ↓
Remote Networks
```

The PC needs the local MAC address of the **default gateway**.

The Ethernet frame goes to the gateway locally, while the IP packet
still identifies the remote IP destination.

This distinction is extremely important.

------------------------------------------------------------------------

# Example

PC:

``` text
IP:      192.168.70.10
Gateway: 192.168.70.1
```

Remote destination:

``` text
8.8.8.8
```

The PC determines that `8.8.8.8` is not local.

It sends the local Ethernet frame toward the MAC address associated
with:

``` text
192.168.70.1
```

not the remote server's MAC address.

------------------------------------------------------------------------

# ARP Troubleshooting

ARP information can help investigate:

``` text
Duplicate IP addresses
Incorrect local communication
Unexpected MAC mappings
Gateway resolution
Layer 2 / Layer 3 interaction
```

Useful commands:

``` text
arp -a
```

``` powershell
Get-NetNeighbor -AddressFamily IPv4
```

------------------------------------------------------------------------

# Clearing Dynamic ARP Information

On Windows, administrative commands can remove neighbor/ARP entries, but
do not clear caches on production systems casually.

For training, understand that ARP entries age out and can be relearned.

------------------------------------------------------------------------

# IPv6 Note

IPv6 does not use ARP.

IPv6 uses **Neighbor Discovery Protocol (NDP)** for related functions.

You will cover IPv6 later.

------------------------------------------------------------------------

# Key Terms

``` text
MAC Address
OUI
ARP
ARP Request
ARP Reply
ARP Cache
Broadcast
Default Gateway
Neighbor Table
NDP
```

------------------------------------------------------------------------

# Knowledge Check

1.  What problem does ARP solve?
2.  Is an ARP request normally broadcast or unicast?
3.  What information is returned in an ARP reply?
4.  What command can display the Windows ARP cache?
5.  When sending to a remote network, whose MAC address does the host
    normally need locally?
6.  Does IPv6 use ARP?

------------------------------------------------------------------------

# Lesson Summary

ARP connects Layer 3 IPv4 addressing with Layer 2 Ethernet delivery.

``` text
Known IPv4 Address
       ↓
ARP Request
       ↓
MAC Address Learned
       ↓
Ethernet Frame Sent
```

------------------------------------------------------------------------

# Hands-On Lab

➡️ **[Lab 07 --- MAC Addresses and
ARP](../labs/lab-07-mac-addresses-and-arp.md)**
