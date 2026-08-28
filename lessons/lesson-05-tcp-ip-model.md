# Lesson 05 --- TCP/IP Model

## Learning Objectives

By the end of this lesson, you will be able to: - Name the four layers
of the TCP/IP model used in this course. - Compare TCP/IP with OSI. -
Associate common protocols with TCP/IP layers. - Explain the
relationship between applications, TCP/UDP, IP, and Ethernet/Wi-Fi. -
Describe encapsulation and use TCP/IP for basic troubleshooting.

## Four-Layer TCP/IP Model

``` text
4 Application
3 Transport
2 Internet
1 Network Access
```

A five-layer teaching model is also common, but this course will
primarily use the four-layer version.

## Application Layer

Roughly combines OSI Layers 5--7. Examples include HTTP/HTTPS, DNS,
DHCP, SMTP, SSH, and FTP.

## Transport Layer

TCP and UDP. Important concepts include ports, segmentation, reliability
with TCP, and connectionless transport with UDP.

## Internet Layer

IP, logical addressing, packets, and routing. IPv4 and IPv6 live here
conceptually.

## Network Access Layer

Ethernet, Wi-Fi, MAC addresses, frames, interfaces, cabling, and
signaling. It broadly combines OSI Layers 1 and 2.

## OSI Mapping

``` text
OSI 7 Application ─┐
OSI 6 Presentation ├─ TCP/IP Application
OSI 5 Session ─────┘
OSI 4 Transport ───── TCP/IP Transport
OSI 3 Network ─────── TCP/IP Internet
OSI 2 Data Link ─┐
OSI 1 Physical ──┴─── TCP/IP Network Access
```

## The Core Stack

``` text
Application
   ↓
TCP / UDP
   ↓
IP
   ↓
Ethernet / Wi-Fi
```

## Encapsulation

``` text
Application data
   ↓
TCP/UDP information
   ↓
IP information
   ↓
Ethernet/Wi-Fi information
   ↓
Transmission
```

## TCP

TCP is connection-oriented and includes mechanisms for reliable, ordered
delivery. It uses port numbers.

## UDP

UDP is connectionless and has less transport overhead. It does not
provide TCP's built-in reliable ordered delivery mechanisms.
Applications may choose UDP when low overhead or timing is important.

## Addresses at Different Layers

``` text
Application    Hostname/service
Transport      Port number
Internet       IP address
Network Access MAC address
```

## Local vs. Remote

Hosts on the same IP network can communicate locally through the LAN. A
host normally sends traffic for other IP networks toward its default
gateway.

## Troubleshooting with TCP/IP

``` text
Network Access → Is the interface connected?
Internet       → Is IP configuration/routing correct?
Transport      → Is the required port reachable?
Application    → Does the service work?
```

Useful tools:

``` powershell
Get-NetAdapter
Get-NetIPConfiguration
Resolve-DnsName example.com
Test-NetConnection example.com -Port 443
```

and:

``` text
ping <destination>
tracert <destination>
```

## Knowledge Check

1.  How many layers are in this TCP/IP model? A. 3 B. 4 C. 7 D. 10
2.  Which layer contains IP? A. Application B. Transport C. Internet D.
    Network Access
3.  Which protocols are Transport? A. TCP/UDP B. Ethernet/Wi-Fi C.
    IPv4/IPv6 D. HTTP/DNS
4.  Which layer includes Ethernet/Wi-Fi? A. Application B. Transport C.
    Internet D. Network Access
5.  Which TCP/IP layer roughly combines OSI 5--7? A. Application B.
    Transport C. Internet D. Network Access

## Lesson Summary

Remember:

``` text
Application
  ↓
Transport — TCP/UDP
  ↓
Internet — IP
  ↓
Network Access — Ethernet/Wi-Fi
```

## Hands-On Lab

➡️ **[Lab 05 --- TCP/IP Model](../labs/lab-05-tcp-ip-model.md)**
