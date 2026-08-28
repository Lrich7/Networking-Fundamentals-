# Lesson 08 --- Network Cables and Connectors

## Learning Objectives

By the end of this lesson, you will be able to:

-   Identify common copper and fiber network cabling.
-   Explain UTP and STP at a beginner level.
-   Recognize common twisted-pair categories.
-   Identify RJ45/8P8C-style Ethernet connectors.
-   Explain straight-through and crossover cable concepts.
-   Identify single-mode and multimode fiber.
-   Recognize common fiber connectors.
-   Explain basic cable limitations and troubleshooting concerns.
-   Choose an appropriate cable type for common scenarios.

------------------------------------------------------------------------

# Physical Media Matters

Network communication ultimately needs a transmission medium.

Common media include:

``` text
Copper
Fiber optic
Wireless radio
```

This lesson focuses on physical cabling.

------------------------------------------------------------------------

# Twisted-Pair Copper

Most endpoint Ethernet connections use twisted-pair copper cabling.

Pairs of copper wires are twisted together to help reduce interference.

Two common types:

``` text
UTP — Unshielded Twisted Pair
STP — Shielded Twisted Pair
```

------------------------------------------------------------------------

# UTP

UTP does not include additional cable shielding around the twisted
pairs.

It is widely used in office Ethernet networks.

Advantages include:

``` text
Common
Relatively inexpensive
Flexible
Easy to install
```

------------------------------------------------------------------------

# STP

STP adds shielding designed to help reduce electromagnetic interference.

It may be useful in environments with greater electrical interference.

Proper installation and grounding practices matter.

------------------------------------------------------------------------

# Cable Categories

Common twisted-pair categories include:

``` text
Cat 5e
Cat 6
Cat 6A
```

Older categories also exist.

Higher category does not automatically mean every installation will
achieve the maximum advertised speed. Equipment, distance, termination
quality, and environment all matter.

------------------------------------------------------------------------

# RJ45 Terminology

Ethernet patch cables commonly use the modular connector people call
**RJ45**.

Technically, the physical modular plug is commonly an **8P8C**
connector.

For practical IT work, you will often hear:

``` text
RJ45 Ethernet cable
```

------------------------------------------------------------------------

# Straight-Through vs. Crossover

Historically:

``` text
Straight-through
    ↓
Different device types

Crossover
    ↓
Similar device types
```

Modern Ethernet equipment commonly supports **Auto-MDI/MDIX**, which can
automatically adapt.

You should still understand the historical distinction because it
appears in networking education and older equipment.

------------------------------------------------------------------------

# T568A and T568B

Ethernet twisted-pair terminations commonly use:

``` text
T568A
T568B
```

A cable terminated the same standard on both ends is commonly a
straight-through cable.

A traditional crossover cable uses different relevant pin mappings
between ends.

You do not need to memorize every wire color yet unless your training
goals require cable termination.

------------------------------------------------------------------------

# Fiber Optic Cabling

Fiber transmits information using light rather than electrical signals.

Advantages can include:

``` text
Longer distances
High bandwidth
Resistance to electromagnetic interference
Electrical isolation
```

------------------------------------------------------------------------

# Single-Mode Fiber --- SMF

Single-mode fiber is commonly used for longer-distance links.

It uses a smaller core and is designed for a single propagation mode.

Common use cases include:

``` text
Building-to-building
Campus backbone
Service provider
Long-distance links
```

------------------------------------------------------------------------

# Multimode Fiber --- MMF

Multimode fiber is commonly used for shorter high-speed links such as
within buildings or data centers, depending on the standard and
distance.

------------------------------------------------------------------------

# Fiber Connectors

Common connector types include:

``` text
LC
SC
ST
MPO/MTP
```

You should be able to recognize LC and SC in particular as common
networking connector names.

------------------------------------------------------------------------

# Transceivers

Network devices may use removable transceiver modules.

Common families include:

``` text
SFP
SFP+
QSFP
QSFP+
```

The module must be compatible with:

``` text
Device
Speed
Fiber/copper medium
Wavelength
Distance
Connector
```

Do not insert random optics into production equipment without verifying
compatibility.

------------------------------------------------------------------------

# Coaxial Cable

Coaxial cable is still used in some networking and service-provider
environments.

Examples include:

``` text
Cable Internet
RF systems
Legacy Ethernet history
```

------------------------------------------------------------------------

# Cable Distance

Copper Ethernet standards have defined distance limitations.

A commonly encountered maximum channel length for many twisted-pair
Ethernet installations is around:

``` text
100 meters
```

But always verify the specific Ethernet standard and cabling design.

Fiber distance varies significantly by fiber type, optics, speed, and
standard.

------------------------------------------------------------------------

# Patch Panels

Structured cabling commonly uses patch panels.

Conceptually:

``` text
Wall Jack
   ↓
Permanent Building Cable
   ↓
Patch Panel
   ↓
Patch Cable
   ↓
Switch
```

Patch panels help organize building cabling but do not perform Ethernet
switching.

------------------------------------------------------------------------

# Cable Troubleshooting

Check for:

``` text
Loose connection
Damaged connector
Bent/broken clip
Cable damage
Wrong patch point
Incorrect termination
Excessive distance
Electrical interference
Bad transceiver
Dirty/damaged fiber
Wrong fiber/optic type
```

------------------------------------------------------------------------

# Cable Testers

Tools may include:

``` text
Basic continuity tester
Wiremap tester
Cable certifier
Tone generator and probe
Optical power meter
Fiber inspection tools
OTDR
```

You do not need all of these for the lab, but recognize their purpose.

------------------------------------------------------------------------

# Key Terms

``` text
UTP
STP
Cat 5e
Cat 6
Cat 6A
RJ45 / 8P8C
T568A
T568B
Straight-Through
Crossover
Auto-MDI/MDIX
Single-Mode Fiber
Multimode Fiber
LC
SC
SFP
Patch Panel
```

------------------------------------------------------------------------

# Knowledge Check

1.  What does UTP stand for?
2.  Why are copper pairs twisted?
3.  What is the difference between single-mode and multimode fiber at a
    high level?
4.  Does a patch panel switch Ethernet traffic?
5.  What feature lets many modern Ethernet ports adapt to cable wiring
    automatically?
6.  Name two common fiber connector types.

------------------------------------------------------------------------

# Lesson Summary

Choose cabling based on:

``` text
Required speed
Distance
Environment
Equipment
Connector/transceiver compatibility
Cost
Future needs
```

------------------------------------------------------------------------

# Hands-On Lab

➡️ **[Lab 08 --- Network Cables and
Connectors](../labs/lab-08-network-cables-and-connectors.md)**
