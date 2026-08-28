# Lab 10 --- Wireless Networking Basics

## Lab Objective

Inspect wireless information in Windows and build, test, document, and
troubleshoot a small wired/wireless network in Cisco Packet Tracer.

------------------------------------------------------------------------

# Part 1 --- Inspect Wireless Interfaces

On a Windows computer with Wi-Fi:

``` powershell
Get-NetAdapter
```

Then:

``` text
netsh wlan show interfaces
```

If Wi-Fi is unavailable on your machine, review the output conceptually.

Record if available:

``` text
SSID: __________________________________
Radio type: _____________________________
Signal: _________________________________
Channel: ________________________________
```

Do not publish organizational wireless details.

------------------------------------------------------------------------

# Part 2 --- View Available Networks

Run:

``` text
netsh wlan show networks
```

Observe nearby SSIDs.

Do not attempt to connect to networks you are not authorized to use.

------------------------------------------------------------------------

# Part 3 --- Build a WLAN

In Packet Tracer create:

``` text
Laptop0 ))))
             Access Point ── Switch ── PC0
Laptop1 ))))
```

Configure the wired and wireless endpoints on:

``` text
192.168.80.0/24
```

Example:

``` text
PC0      192.168.80.10
Laptop0  192.168.80.20
Laptop1  192.168.80.30
```

------------------------------------------------------------------------

# Part 4 --- Configure the SSID

Use a lab SSID:

``` text
Training-WiFi
```

Configure the access point and clients according to the options
available in your Packet Tracer version.

If security is supported, use a lab-only password.

Never reuse a real organizational password.

------------------------------------------------------------------------

# Part 5 --- Test Wireless-to-Wired Communication

From Laptop0:

``` text
ping 192.168.80.10
```

From Laptop1:

``` text
ping 192.168.80.10
```

Record:

``` text
Laptop0 → PC0: __________________
Laptop1 → PC0: __________________
```

------------------------------------------------------------------------

# Part 6 --- Test Wireless-to-Wireless

Ping between the laptops.

Record:

``` text
Result: ________________________________
```

------------------------------------------------------------------------

# Part 7 --- Wrong SSID Failure

Change Laptop1 to an incorrect lab SSID.

Test connectivity.

Record:

``` text
Symptom: _______________________________
Scope: __________________________________
Cause: __________________________________
Fix: ____________________________________
```

Restore the correct SSID.

------------------------------------------------------------------------

# Part 8 --- Access Point Failure

Disconnect or disable the access point.

Answer:

``` text
Wireless clients affected? ______________
Wired PC affected locally? ______________
```

Explain why the scope differs.

Restore the AP.

------------------------------------------------------------------------

# Part 9 --- IP Configuration Failure

Give Laptop0 an incorrect IP network.

Example:

``` text
192.168.90.20 /24
```

The laptop may still appear associated with Wi-Fi while IP communication
fails.

What does this demonstrate?

``` text
____________________________________________________
```

Restore `192.168.80.20/24`.

------------------------------------------------------------------------

# Part 10 --- Wireless Troubleshooting Flow

Build:

``` text
Adapter enabled?
     ↓
Correct SSID?
     ↓
Authenticated?
     ↓
Signal/AP available?
     ↓
Correct IP?
     ↓
Gateway/DNS?
     ↓
Application/Internet?
```

Add any additional checks you would use.

------------------------------------------------------------------------

# Part 11 --- Design Scenario

A small office has:

``` text
20 employees
10 laptops
5 phones
Wired desktops
Guest visitors
```

Answer:

``` text
Would you use only Wi-Fi? Why/why not?

____________________________________________________

Would you separate guest access from internal access?

____________________________________________________
```

------------------------------------------------------------------------

# Knowledge Check

1.  What is an SSID?
2.  What device connects wireless clients into the LAN?
3.  Can a device have excellent Wi-Fi signal but incorrect IP
    configuration?
4.  What should you check if every Wi-Fi user fails but wired users
    work?
5.  Why should guest access be restricted from internal resources?

------------------------------------------------------------------------

# Challenge

Build a small office network with:

``` text
4 wired PCs
4 wireless laptops
1 switch
1 access point
1 router
```

Use a lab SSID and a single local IP network.

Test every endpoint.

Then create and repair three failures:

``` text
Wrong SSID
Disabled/disconnected AP
Wrong client IP network
```

Save:

``` text
lab-10-wireless-challenge.pkt
```

------------------------------------------------------------------------

# Lab Completion Checklist

-   [ ] Inspected Windows wireless information
-   [ ] Viewed available networks safely
-   [ ] Built a Packet Tracer WLAN
-   [ ] Configured a lab SSID
-   [ ] Tested wireless-to-wired communication
-   [ ] Tested wireless-to-wireless communication
-   [ ] Diagnosed wrong SSID
-   [ ] Diagnosed AP failure
-   [ ] Diagnosed incorrect IP configuration
-   [ ] Built wireless troubleshooting flow
-   [ ] Completed design scenario
-   [ ] Completed knowledge check
-   [ ] Completed challenge

------------------------------------------------------------------------

# Lab Complete

You have completed **Lab 10 --- Wireless Networking Basics** and
**Section 2 --- Ethernet & Physical Networking**.

You now have hands-on experience with:

``` text
Ethernet
MAC addresses
ARP
Switch MAC tables
Copper cabling
Fiber cabling
Connectors
Ethernet speeds
Link negotiation
Performance bottlenecks
Wireless LANs
SSID configuration
Wireless troubleshooting
```

Now apply those skills in Project 02.

------------------------------------------------------------------------

# 🛠️ Project 02 --- Small Office Network

➡️ **[Project 02 --- Small Office
Network](../projects/project-02-small-office-network.md)**

In this project, you will design a practical wired and wireless office
network, choose appropriate media, document Ethernet and wireless
components, test communication, and troubleshoot physical and wireless
failures.

Unlike the labs, you will receive requirements rather than exact
configuration steps.

➡️ **[Begin Project 02 --- Small Office
Network](../projects/project-02-small-office-network.md)**
