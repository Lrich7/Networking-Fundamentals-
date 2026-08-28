# Lesson 10 --- Wireless Networking Basics

## Learning Objectives

By the end of this lesson, you will be able to:

-   Explain how a wireless LAN differs from a wired Ethernet LAN.
-   Identify access points, wireless clients, SSIDs, and channels.
-   Recognize the 2.4 GHz, 5 GHz, and 6 GHz Wi-Fi bands.
-   Explain basic coverage, interference, and channel concepts.
-   Recognize common Wi-Fi generations and IEEE 802.11 terminology.
-   Explain why signal strength does not guarantee Internet
    connectivity.
-   Apply basic wireless security practices.
-   Troubleshoot common Wi-Fi connectivity problems.
-   Build a small wireless network in Cisco Packet Tracer.

------------------------------------------------------------------------

# What Is a WLAN?

A **Wireless Local Area Network (WLAN)** allows devices to access a
local network using radio instead of an Ethernet cable.

``` text
Laptop  ))))
             \
Phone   )))) Access Point ── Switch ── Router
             /
Tablet  ))))
```

------------------------------------------------------------------------

# Wireless Access Point

An access point bridges wireless clients into the network.

It may be:

``` text
Standalone AP
Built into a home/small-office router
Enterprise managed AP
Cloud-managed AP
Virtual/controller-managed environment
```

------------------------------------------------------------------------

# SSID

The **SSID** is the wireless network name presented to clients.

Example:

``` text
Company-WiFi
Guest-WiFi
Training-WiFi
```

An SSID is not a security mechanism by itself.

------------------------------------------------------------------------

# Wi-Fi Bands

Modern Wi-Fi commonly uses:

``` text
2.4 GHz
5 GHz
6 GHz
```

## 2.4 GHz

Generally offers longer propagation and better wall penetration than
higher frequencies, but has fewer non-overlapping channels in many
regulatory domains and often more interference.

## 5 GHz

Generally offers more channel capacity and commonly higher performance
opportunities, but coverage characteristics differ from 2.4 GHz.

## 6 GHz

Used by newer Wi-Fi technologies where permitted and supported. It
provides additional spectrum but requires compatible equipment and has
its own regulatory/security requirements.

Exact channel availability depends on country and configuration.

------------------------------------------------------------------------

# Wi-Fi Generations

You may encounter IEEE names:

``` text
802.11a
802.11b
802.11g
802.11n
802.11ac
802.11ax
802.11be
```

Consumer naming also includes:

``` text
Wi-Fi 4 → 802.11n
Wi-Fi 5 → 802.11ac
Wi-Fi 6 → 802.11ax
Wi-Fi 6E → 802.11ax using 6 GHz capability
Wi-Fi 7 → 802.11be
```

You do not need to memorize every maximum theoretical speed yet.

------------------------------------------------------------------------

# Channels

Wireless networks share radio spectrum.

Nearby APs using overlapping or congested channels can affect
performance.

Wireless design considers:

``` text
Channel selection
Channel width
Transmit power
AP placement
Client density
Interference
```

------------------------------------------------------------------------

# Interference

Possible interference sources can include:

``` text
Other Wi-Fi networks
Bluetooth devices
Microwave ovens
Certain wireless devices
Physical obstructions
Industrial equipment
```

The effect depends on frequency and environment.

------------------------------------------------------------------------

# Signal Strength

A strong Wi-Fi signal does not guarantee:

``` text
Correct IP configuration
Working DNS
Working gateway
Internet connectivity
Healthy application
```

Think:

``` text
Connected to AP
      ≠
Internet guaranteed
```

------------------------------------------------------------------------

# Wireless Security

Modern wireless networks should use appropriate current security.

Avoid obsolete security such as:

``` text
WEP
```

WPA2 and WPA3 are commonly encountered, with WPA3 being newer.

Enterprise environments may use:

``` text
802.1X
RADIUS
Enterprise authentication
Certificates
```

These will be discussed more in the security section.

------------------------------------------------------------------------

# Guest Networks

A guest WLAN should normally be designed to limit access to internal
resources.

Conceptually:

``` text
Employee WLAN → Internal Resources + Internet
Guest WLAN    → Internet, restricted from internal network
```

Actual implementation may use VLANs, firewall rules, and other controls
covered later.

------------------------------------------------------------------------

# Wireless Troubleshooting

Start by determining scope.

``` text
One device?
All wireless devices?
One area?
One SSID?
All SSIDs?
Wired network also affected?
```

Then check:

``` text
Wi-Fi adapter enabled
Correct SSID
Authentication
Signal strength
AP status
IP configuration
Gateway
DNS
Internet path
```

------------------------------------------------------------------------

# Windows Wireless Tools

PowerShell:

``` powershell
Get-NetAdapter
```

Command Prompt:

``` text
netsh wlan show interfaces
```

Available networks:

``` text
netsh wlan show networks
```

These can provide useful wireless information on supported Windows
systems.

------------------------------------------------------------------------

# Roaming

Enterprise wireless networks may use multiple access points with the
same intended network identity.

Clients can move and select different APs.

Roaming quality depends on:

``` text
Client behavior
AP design
Signal
Authentication
Network configuration
```

------------------------------------------------------------------------

# Key Terms

``` text
WLAN
Access Point
SSID
2.4 GHz
5 GHz
6 GHz
Channel
Interference
Wi-Fi 5
Wi-Fi 6
Wi-Fi 6E
Wi-Fi 7
WPA2
WPA3
Guest Network
Roaming
```

------------------------------------------------------------------------

# Knowledge Check

1.  What is an SSID?
2.  Does a strong Wi-Fi signal prove the Internet works?
3.  Name the three major Wi-Fi frequency bands discussed.
4.  Which is newer: WPA2 or WPA3?
5.  What does an access point do?
6.  Why should troubleshooting first determine whether wired users are
    also affected?

------------------------------------------------------------------------

# Lesson Summary

Wireless troubleshooting should separate:

``` text
Radio / Association
       ↓
Authentication
       ↓
IP Configuration
       ↓
Local Network
       ↓
Gateway / DNS
       ↓
Internet / Application
```

------------------------------------------------------------------------

# Hands-On Lab

➡️ **[Lab 10 --- Wireless Networking
Basics](../labs/lab-10-wireless-networking-basics.md)**
