# Lesson 04 --- OSI Model

## Learning Objectives

By the end of this lesson, you will be able to: - Name all seven OSI
layers in order. - Describe the basic purpose of each layer. - Associate
common protocols, devices, and addressing with relevant layers. -
Explain frames, packets, segments/datagrams, and bits. - Explain
encapsulation at a beginner level. - Use the OSI model as a
troubleshooting framework.

## Why Use a Model?

Networking involves many technologies working together. A layered model
helps with learning, standards, design, communication, and
troubleshooting.

## The Seven Layers

``` text
7 Application
6 Presentation
5 Session
4 Transport
3 Network
2 Data Link
1 Physical
```

Memory aid from Layer 7 down: **All People Seem To Need Data
Processing**.

## Layer 7 --- Application

Network-facing application services and protocols. Examples include
HTTP/HTTPS, DNS, SMTP, FTP, and SSH.

## Layer 6 --- Presentation

Associated with representation of data: formatting, encoding,
encryption, and compression concepts.

## Layer 5 --- Session

Associated with establishing, maintaining, and ending communication
sessions.

## Layer 4 --- Transport

TCP and UDP operate here. Important concepts include ports,
segmentation, end-to-end transport, TCP reliability, and UDP datagrams.

## Layer 3 --- Network

IP addressing and routing. Routers are strongly associated with Layer 3.
The protocol data unit is commonly called a **packet**.

## Layer 2 --- Data Link

Local-link delivery, Ethernet frames, MAC addresses, and switching.
Traditional Ethernet switches are strongly associated with Layer 2.

## Layer 1 --- Physical

Cables, connectors, radio/electrical/optical signals, physical ports,
and bits.

## Protocol Data Units

``` text
Layers 7–5   Data
Layer 4      Segment / Datagram
Layer 3      Packet
Layer 2      Frame
Layer 1      Bits
```

## Encapsulation

As information moves down the stack, layers add information needed for
delivery.

``` text
Application data
   ↓
Transport information
   ↓
IP information
   ↓
Ethernet/Wi-Fi information
   ↓
Bits/signals
```

## Devices and Layers

``` text
Hub/repeater       Layer 1
Traditional switch Layer 2
Router             Layer 3
Firewall           May inspect/control several layers
Load balancer      Often Layer 4 and/or Layer 7
```

Modern devices often work across multiple layers.

## Troubleshooting Bottom-Up

``` text
Layer 1 — Is there link/signal?
Layer 2 — Is local Ethernet/Wi-Fi working?
Layer 3 — Is IP addressing/routing correct?
Layer 4 — Is the required TCP/UDP service reachable?
Layers 5–7 — Is the application/service working?
```

Useful Windows tools:

``` powershell
Get-NetAdapter
Get-NetIPConfiguration
Test-NetConnection example.com -Port 443
```

Also:

``` text
ping <address>
```

## Knowledge Check

1.  How many OSI layers are there? A. 4 B. 5 C. 7 D. 10
2.  Which layer handles IP addressing/routing? A. 1 B. 2 C. 3 D. 7
3.  Which layer uses Ethernet frames/MAC addresses? A. 2 B. 3 C. 5 D. 7
4.  Which layer uses TCP/UDP? A. 1 B. 4 C. 6 D. 7
5.  An unplugged Ethernet cable points first to which layer? A. 7 B.
    4 C. 3 D. 1

## Lesson Summary

Remember the practical anchors:

``` text
Ports → Layer 4
IP → Layer 3
MAC/Ethernet → Layer 2
Cable/signal → Layer 1
```

## Hands-On Lab

➡️ **[Lab 04 --- OSI Model](../labs/lab-04-osi-model.md)**
