# Lesson 03 --- Network Devices

## Learning Objectives

By the end of this lesson, you will be able to: - Distinguish endpoints
from network infrastructure. - Explain the roles of NICs, switches,
routers, access points, firewalls, modems, and gateways. - Recognize
hubs, bridges, repeaters, Layer 3 switches, proxies, load balancers,
IDS, and IPS. - Identify likely devices involved in common network
failures.

## Endpoints and Infrastructure

Endpoints consume or provide network services: desktops, laptops,
servers, printers, phones, cameras, and IoT devices.

Infrastructure connects, directs, protects, or supports traffic:
switches, routers, access points, firewalls, and provider equipment.

## NIC --- Network Interface Card

A NIC provides a device's network interface. It may be Ethernet, Wi-Fi,
USB, physical, or virtual.

Windows:

``` powershell
Get-NetAdapter
```

## Switch

A switch connects devices on a local Ethernet network.

``` text
PC ──┐
PC ──┼── Switch ── Server
PC ──┘
```

Switches use Layer 2 information such as MAC addresses. You will study
this later.

## Router

A router connects different IP networks.

``` text
192.168.10.0/24 ── Router ── 192.168.20.0/24
```

The default gateway is commonly a router or other Layer 3 device.

## Wireless Access Point

An access point connects wireless devices to a network.

``` text
Laptop )) Access Point ── Switch
```

Being connected to Wi-Fi does not by itself prove Internet access works.

## Firewall

A firewall permits or blocks traffic according to security policy. Rules
can consider source, destination, protocol, port, state, application,
and other information.

## Modem / Provider Equipment

Depending on the service, Internet access may involve a cable modem, DSL
modem, fiber ONT, or cellular equipment. Consumer devices often combine
modem, router, switch, firewall, and Wi-Fi functions.

## Gateway

A default gateway is the device a host uses to reach destinations
outside its local network. It may be a router, Layer 3 switch, firewall,
or virtual appliance.

## Other Devices

-   **Layer 3 switch:** combines switching with routing capabilities.
-   **Bridge:** connects network segments at the data-link level.
-   **Repeater/extender:** regenerates or extends signals.
-   **Hub:** older device that repeats received Ethernet traffic
    broadly; largely obsolete.
-   **Load balancer:** distributes traffic across servers/services.
-   **Proxy:** acts as an intermediary for requests.
-   **IDS:** detects suspicious activity.
-   **IPS:** detects and can actively block according to policy.

## Typical Small-Business Path

``` text
Laptop
  ↓ Wi-Fi
Access Point
  ↓
Switch
  ↓
Firewall / Router
  ↓
ISP Equipment
  ↓
Internet
```

## Failure Scope

``` text
One PC fails → NIC, cable/Wi-Fi, switch port, configuration
Wireless fails but wired works → access point/wireless settings
Devices on one switch fail → switch/uplink
Whole site loses remote access → gateway, firewall, ISP/WAN path
```

## Knowledge Check

1.  Which device primarily connects Ethernet devices on the same LAN? A.
    Switch B. Router C. Modem D. Proxy
2.  Which device connects different IP networks? A. Hub B. Router C.
    NIC D. Printer
3.  Which device provides wireless access? A. Access point B. Monitor C.
    Hub D. Patch panel
4.  Which device enforces network security rules? A. Firewall B. NIC C.
    Printer D. Cable
5.  Can one appliance perform several networking functions? A. Yes B. No

## Lesson Summary

Focus on device **function**, not just the label on the box.
Understanding each role helps you follow traffic and isolate failures.

## Hands-On Lab

➡️ **[Lab 03 --- Network Devices](../labs/lab-03-network-devices.md)**
