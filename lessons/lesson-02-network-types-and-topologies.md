# Lesson 02 --- Network Types and Topologies

## Learning Objectives

By the end of this lesson, you will be able to: - Distinguish LAN, WLAN,
WAN, PAN, MAN, and campus networks. - Explain physical versus logical
topology. - Recognize star, bus, ring, mesh, point-to-point, and hybrid
topologies. - Explain how topology helps identify the scope of a network
failure. - Select an appropriate basic topology for a small network.

## Network Types

### LAN --- Local Area Network

A LAN connects devices within a relatively small area such as a home,
office, classroom, or building.

``` text
PC1 ──┐
PC2 ──┼── Switch ── Printer
PC3 ──┘
```

### WLAN --- Wireless LAN

A WLAN provides local network access over Wi-Fi.

``` text
Laptop ))))
             Access Point ── Switch
Phone  ))))
```

A network can contain both wired LAN and WLAN devices.

### WAN --- Wide Area Network

A WAN connects networks across larger geographic areas.

``` text
Office A ── Router ── WAN ── Router ── Office B
```

### PAN --- Personal Area Network

A PAN covers a very small area around an individual. Bluetooth
connections between a phone, watch, keyboard, or earbuds are common
examples.

### MAN and Campus Networks

A MAN can span a metropolitan area. A campus network connects LANs
across nearby buildings such as a hospital, university, or corporate
campus.

## What Is Topology?

Topology describes how network devices and connections are arranged.

**Physical topology** describes the actual device/cable layout.
**Logical topology** describes how communication logically flows.

## Star Topology

Endpoints connect to a central device, normally a switch in modern
Ethernet LANs.

``` text
       PC1
        │
PC2 ─ Switch ─ PC3
        │
      Printer
```

Advantages include simple expansion and fault isolation. If one endpoint
cable fails, the other endpoints normally remain connected. The central
switch, however, is a critical shared component.

## Bus Topology

Devices share a common backbone.

``` text
PC1 ─── PC2 ─── PC3 ─── PC4
```

This is mainly important for recognizing older network designs.

## Ring Topology

Devices form a circular path.

``` text
PC1 ── PC2
│       │
PC4 ── PC3
```

## Mesh Topology

Mesh designs provide multiple paths. A full mesh connects every node to
every other node; a partial mesh provides redundancy only where needed.

## Point-to-Point

A direct link joins two endpoints.

``` text
Router A ───────── Router B
```

## Hybrid Topology

Real networks often combine designs. A business may use star LANs at
each office and WAN links between offices.

## Topology and Troubleshooting

Ask whether the failure affects one device, one area, one switch, the
whole LAN, or remote connectivity. Shared failures often point toward
shared infrastructure.

``` text
One PC fails → inspect that PC, cable, NIC, and switch port
All PCs on one switch fail → inspect the switch and uplink
Whole site loses remote access → inspect gateway/WAN path
```

## Key Terms

LAN, WLAN, WAN, PAN, MAN, campus network, physical topology, logical
topology, star, bus, ring, mesh, point-to-point, hybrid.

## Knowledge Check

1.  Which network type normally covers one office? A. WAN B. LAN C.
    PAN D. Internet
2.  Which topology connects endpoints to a central switch? A. Ring B.
    Star C. Bus D. Mesh
3.  Which topology provides multiple possible paths? A. Mesh B. Bus C.
    PAN D. Star only
4.  What is the difference between physical and logical topology?
5.  Why is topology useful during troubleshooting?

## Lesson Summary

You should now recognize common network scopes and topologies and
understand how a diagram can help isolate failures.

## Hands-On Lab

➡️ **[Lab 02 --- Network Types and
Topologies](../labs/lab-02-network-types-and-topologies.md)**
