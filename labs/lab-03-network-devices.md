# Lab 03 --- Network Devices

## Lab Objective

Identify network device roles and build a small wired/wireless Packet
Tracer network.

## Part 1 --- Inspect Your NIC

Run:

``` powershell
Get-NetAdapter
```

Record:

``` text
Name: ______________________
Description: _______________
Status: ____________________
Link Speed: _________________
MAC Address: ________________
Ethernet / Wi-Fi / Other: ___
```

## Part 2 --- Match the Device

Match switch, router, access point, firewall, NIC, and ISP equipment
to: - Connects a computer to a network - Connects devices on a local
Ethernet LAN - Connects different IP networks - Provides wireless
network access - Controls traffic using security rules - Provides
connectivity toward a service-provider network

## Part 3 --- Build a Wired LAN

Add one switch, three PCs, and one server.

``` text
PC0 ───┐
PC1 ───┼── Switch
PC2 ───┤
Server ┘
```

Configure:

``` text
PC0     192.168.30.10 /24
PC1     192.168.30.20 /24
PC2     192.168.30.30 /24
Server  192.168.30.100 /24
```

Test from PC0 to every endpoint. Save as `lab-03-switched-lan.pkt`.

## Part 4 --- Add a Router

Connect a router to the switch.

``` text
Endpoints ── Switch ── Router
```

Do not worry about advanced routing yet.

Explain:

``` text
Switch role: ______________________________________
Router role: ______________________________________
```

## Part 5 --- Add Wireless

Add an access point and wireless laptop.

``` text
Laptop )) Access Point ── Switch ── Router
```

Configure the laptop to join the lab wireless network supported by your
chosen Packet Tracer device.

## Part 6 --- Follow the Path

For a wireless laptop communicating with the local server:

``` text
Laptop → __________ → __________ → Server
```

Is the router required when both endpoints are on the same local IP
network? Explain.

## Part 7 --- Failure Tests

1.  Disconnect PC1 only. Which devices remain functional?
2.  Disconnect the switch. What is the scope?
3.  Disconnect the access point. Do wired PCs necessarily fail?

Record what each failure teaches you.

## Part 8 --- Troubleshooting Scenarios

-   One Ethernet PC has no link: where do you start?
-   All Wi-Fi clients fail while wired works: where do you start?
-   Local devices communicate but remote networks are unreachable: which
    devices/path do you inspect?
-   A security rule blocks traffic: which device/function is likely
    involved?

## Part 9 --- Simulation Mode

Send a ping between two endpoints and observe the path through the
switch.

## Knowledge Check

1.  What connects Ethernet devices on a LAN?
2.  What routes between IP networks?
3.  What does a NIC provide?
4.  What should you investigate when Wi-Fi alone fails?
5.  Can routing and firewall functions exist on one appliance?

## Challenge

Build a topology with 4 PCs, server, switch, router, access point, and 2
wireless clients. Label each device's role. Save as
`lab-03-device-challenge.pkt`.

## Lab Completion Checklist

-   [ ] Inspected a NIC
-   [ ] Matched device roles
-   [ ] Built a switched LAN
-   [ ] Added a router
-   [ ] Added wireless
-   [ ] Tested failures
-   [ ] Used Simulation Mode
-   [ ] Completed knowledge check
-   [ ] Completed challenge

# Lab Complete

You have completed **Lab 03 --- Network Devices**.

# Next Lesson

➡️ **[Lesson 04 --- OSI Model](../lessons/lesson-04-osi-model.md)**
