# 📘 Lesson 19 — WAN and Remote Connectivity

Welcome to **Lesson 19 of Networking Fundamentals**.

So far, most of our network has existed inside one location:

```text
PC
 ↓
Switch
 ↓
Router / Firewall
 ↓
Local Network
```

But businesses rarely operate entirely inside one LAN.

They need to connect to:

```text
Internet Services

Cloud Applications

Branch Offices

Remote Employees

Data Centers

Microsoft 365

Azure / AWS

Business Partners
```

That requires us to move beyond the LAN.

Welcome to the:

> **WAN — Wide Area Network**

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain the difference between a LAN and WAN
- Explain the role of an ISP
- Understand WAN edge devices
- Identify common Internet connection technologies
- Compare fiber, cable, DSL, cellular, and satellite
- Understand dedicated circuits
- Explain Metro Ethernet
- Understand MPLS
- Explain SD-WAN
- Understand site-to-site VPNs
- Understand remote-access VPNs
- Compare full-tunnel and split-tunnel VPNs
- Explain VPN encryption at a high level
- Understand public and private IP addresses
- Explain NAT in relation to Internet connectivity
- Understand bandwidth
- Understand latency
- Understand jitter
- Understand packet loss
- Explain redundancy and failover
- Recognize common WAN failures
- Troubleshoot remote connectivity systematically

---

# 🎓 Network+ Focus

For **CompTIA Network+ N10-009**, pay particular attention to:

- WAN
- ISP
- Fiber
- Cable
- DSL
- Cellular
- Satellite
- Dedicated circuits
- Metro Ethernet
- MPLS
- SD-WAN
- VPN
- Site-to-site VPN
- Remote-access VPN
- Split tunneling
- Full tunneling
- Bandwidth
- Latency
- Jitter
- Packet loss
- Redundancy
- Failover
- WAN troubleshooting

---

# 🏢 LAN vs. WAN

A:

> **LAN — Local Area Network**

generally connects devices within a limited geographic area.

Examples:

```text
Office

Building

Floor

Campus
```

A:

> **WAN — Wide Area Network**

connects networks across larger geographic distances.

---

# 🗺️ Example

Imagine Northstar Services has offices in:

```text
Springfield
Kansas City
St. Louis
```

Each office has its own LAN.

Conceptually:

```text
Springfield LAN
      │
      │
      ▼
     WAN
    /   \
   /     \
Kansas   St. Louis
City LAN    LAN
```

The WAN provides connectivity between locations.

---

# 🌎 The Internet as a WAN

The Internet is the largest example of interconnected networks spanning the world.

Your business network might look like:

```text
LAN
 │
 ▼
Firewall
 │
 ▼
ISP
 │
 ▼
Internet
 │
 ├── Microsoft 365
 ├── Azure
 ├── Websites
 ├── Remote Services
 └── Other Networks
```

---

# 🌐 ISP

ISP stands for:

> **Internet Service Provider**

The ISP provides connectivity between your organization and external networks such as the Internet.

Examples of connection technologies include:

```text
Fiber

Cable

DSL

Cellular

Satellite

Dedicated Circuits
```

---

# 🧱 The WAN Edge

The point where your organization's network connects to an external provider is commonly considered part of the:

> **WAN edge**

Equipment may include:

```text
Firewall

Router

Provider Equipment

Modem / ONT

SD-WAN Appliance
```

---

# 🗺️ Typical Business Internet Connection

```text
INTERNAL LAN
     │
     ▼
  SWITCH
     │
     ▼
 FIREWALL
     │
     ▼
 ISP DEVICE
     │
     ▼
    ISP
     │
     ▼
 INTERNET
```

---

# 🛡️ Firewall at the Edge

A firewall commonly sits between:

```text
Trusted Internal Network
          │
          ▼
       Firewall
          │
          ▼
Untrusted External Networks
```

The firewall can perform functions such as:

- Traffic filtering
- NAT
- VPN termination
- Security inspection
- Access control
- Logging

---

# 🔄 Remember NAT

Earlier we learned:

> **NAT — Network Address Translation**

A business may use private addressing internally:

```text
10.10.10.0/24
```

while communicating externally through a public address.

Conceptually:

```text
PC
10.10.10.25
     │
     ▼
Firewall
     │
     │ NAT
     ▼
Public IP
     │
     ▼
Internet
```

---

# 🌐 Public vs. Private IP Addresses

Private IPv4 ranges include:

```text
10.0.0.0/8

172.16.0.0/12

192.168.0.0/16
```

These are not normally routed directly across the public Internet.

Organizations typically use NAT to provide Internet connectivity for privately addressed devices.

---

# 🔌 Common WAN Connection Types

Businesses may connect using several technologies.

Let's examine the major ones.

---

# 💡 Fiber Internet

Fiber uses optical cabling to provide connectivity.

Advantages can include:

- High bandwidth
- Low latency
- High reliability
- Symmetrical service options
- Long-distance capability

---

# ↕️ Symmetrical Connection

A symmetrical Internet service provides similar:

```text
Download
and
Upload
```

capacity.

Example:

```text
1 Gbps Download

1 Gbps Upload
```

This can be useful for businesses that send significant amounts of data.

---

# ↕️ Asymmetrical Connection

An asymmetrical service may look like:

```text
1 Gbps Download

100 Mbps Upload
```

Download capacity is significantly higher than upload capacity.

This is common with some broadband technologies.

---

# 📺 Cable Internet

Cable Internet commonly uses cable-provider infrastructure.

It can provide:

- High download speeds
- Wide availability
- Relatively affordable service

Depending on the service, upload capacity may be lower than download capacity.

---

# ☎️ DSL

DSL stands for:

> **Digital Subscriber Line**

DSL uses telephone-line infrastructure.

It is generally associated with older or lower-bandwidth deployments compared with many modern fiber and cable services.

It may still appear in:

- Older businesses
- Rural areas
- Legacy environments

---

# 📱 Cellular WAN

Businesses can use cellular networks such as:

```text
4G LTE

5G
```

for WAN connectivity.

Common uses include:

- Backup Internet
- Mobile locations
- Temporary sites
- Vehicles
- Kiosks
- Remote facilities

---

# 🧠 Cellular Backup Example

```text
Primary Fiber
      │
      ▼
   Firewall
      │
      ├──────── LAN
      │
      ▼
5G Backup
```

If fiber fails:

```text
Fiber
  X

Firewall
   │
   ▼
5G Connection
   │
   ▼
Internet
```

---

# 🛰️ Satellite

Satellite Internet can provide connectivity where terrestrial services are unavailable.

It can be useful for:

- Rural locations
- Remote sites
- Temporary locations

Performance characteristics vary considerably by satellite technology and provider.

---

# ⏱️ Satellite and Latency

Some satellite systems can have higher latency because of the distance signals must travel.

Newer low-Earth-orbit satellite systems can provide substantially different latency characteristics than traditional geostationary systems.

The important concept is:

> **Connection type affects performance characteristics.**

---

# 🔗 Dedicated Circuits

Businesses may purchase dedicated connectivity from a provider.

Compared with consumer broadband, dedicated services may provide:

- Guaranteed or committed service characteristics
- Business support
- Service-level agreements
- Symmetrical bandwidth
- Predictable performance

Exact features depend on the provider and contract.

---

# 📜 SLA

SLA stands for:

> **Service-Level Agreement**

An SLA can define provider commitments such as:

- Availability
- Response times
- Repair targets
- Performance characteristics

---

# 🏙️ Metro Ethernet

Metro Ethernet allows Ethernet-based connectivity across a metropolitan or provider network.

Conceptually:

```text
Office A
   │
Ethernet
   │
   ▼
Provider Network
   │
Ethernet
   │
   ▼
Office B
```

To the customer, it can behave somewhat like extending Ethernet connectivity across locations.

---

# ☁️ MPLS

MPLS stands for:

> **Multiprotocol Label Switching**

MPLS has long been used by organizations and service providers to connect business locations.

Conceptually:

```text
Branch A
   │
   ▼
Provider MPLS
   │
   ├──── HQ
   │
   └──── Branch B
```

The provider manages the underlying WAN transport.

---

# 🌐 SD-WAN

SD-WAN stands for:

> **Software-Defined Wide Area Network**

SD-WAN can intelligently use multiple WAN connections.

Example:

```text
             SD-WAN
             Appliance
             /      \
            /        \
         Fiber       5G
           │          │
           └────┬─────┘
                ▼
             Internet
```

---

# 🧠 Why SD-WAN?

SD-WAN can provide capabilities such as:

- Centralized management
- Multiple WAN links
- Dynamic path selection
- Application-aware routing
- Failover
- Policy-based traffic handling

Implementation varies by vendor.

---

# 🛣️ Path Selection

Imagine:

```text
Fiber
Latency: 15 ms

5G
Latency: 55 ms
```

Normal business traffic may use fiber.

If fiber fails:

```text
Fiber
  X
```

SD-WAN may move traffic to:

```text
5G
```

according to configured policies.

---

# 🔄 WAN Redundancy

Businesses often need more than one path to the Internet.

Example:

```text
             Firewall
             /      \
            /        \
        ISP 1        ISP 2
        Fiber         5G
```

This provides:

> **Redundancy**

---

# 🚨 Single Point of Failure

This design:

```text
LAN
 │
Firewall
 │
Single ISP
 │
Internet
```

means the ISP connection is a potential:

> **Single point of failure**

---

# 🛡️ Redundant Design

```text
                 LAN
                  │
               Firewall
               /      \
              /        \
         ISP-01       ISP-02
         Fiber          5G
```

Now a second path may be available if the primary connection fails.

---

# 🔄 Failover

Failover occurs when service moves from a failed primary resource to an available backup.

Example:

```text
PRIMARY
Fiber
  X
  │
  ▼

BACKUP
5G
 ✓
```

---

# 🔐 VPN

VPN stands for:

> **Virtual Private Network**

A VPN creates a protected logical connection across another network such as the Internet.

---

# 🔐 Why Use a VPN?

The public Internet is not your private corporate network.

VPN technologies can provide:

- Encryption
- Authentication
- Protected communication
- Remote network access

---

# 🏢 Site-to-Site VPN

A site-to-site VPN connects networks.

Example:

```text
SPRINGFIELD OFFICE
       │
    Firewall
       │
       │
   INTERNET
       │
       │
    Firewall
       │
KANSAS CITY OFFICE
```

The VPN tunnel exists between the sites' VPN endpoints.

---

# 🔐 Conceptually

```text
LAN A
  │
Firewall
  ║
  ║ Encrypted Tunnel
  ║
Firewall
  │
LAN B
```

Users may not need to manually start a VPN client for normal site-to-site traffic.

---

# 💻 Remote-Access VPN

Remote-access VPNs connect individual remote users to organizational resources.

Example:

```text
REMOTE LAPTOP
      │
      ▼
Home Internet
      │
      ▼
   Internet
      │
      ▼
Company VPN
      │
      ▼
Corporate Network
```

---

# 🏠 Remote Worker Example

An employee working from home may have:

```text
Laptop
  │
  ▼
Home Wi-Fi
  │
  ▼
Home Router
  │
  ▼
ISP
  │
  ▼
Internet
  │
  ▼
VPN Gateway
  │
  ▼
Company Network
```

Notice how many separate systems are involved.

---

# 🧠 Important Troubleshooting Concept

When a remote employee says:

> **"The VPN is broken."**

the VPN may not actually be the problem.

The failure could be:

```text
Laptop Wi-Fi

Home Router

Home ISP

DNS

Internet

VPN Client

Credentials

MFA

VPN Gateway

Corporate Routing

Corporate DNS

Application
```

Determine where the path fails.

---

# 🔐 VPN Authentication

VPN access commonly requires authentication.

Depending on the organization, this could include:

```text
Username + Password

Certificate

MFA

Security Token
```

---

# 🔐 MFA

MFA stands for:

> **Multi-Factor Authentication**

A user might provide:

```text
Password
+
Authenticator Approval
```

or another combination of authentication factors.

---

# 🚇 Full-Tunnel VPN

With full tunneling:

> **Most or all client network traffic is sent through the VPN tunnel according to the VPN configuration.**

Conceptually:

```text
Remote Laptop
     │
     ▼
 VPN Tunnel
     │
     ▼
Company
     │
     ▼
Internet
```

---

# 🔀 Split-Tunnel VPN

With split tunneling:

> **Selected traffic uses the VPN while other traffic may use the user's local Internet connection directly.**

Conceptually:

```text
               Remote Laptop
                  /      \
                 /        \
        Corporate        Public
         Traffic         Internet
            │               │
            ▼               ▼
           VPN          Home ISP
            │
            ▼
         Company
```

---

# 📋 Full vs. Split Tunnel

| Full Tunnel | Split Tunnel |
|---|---|
| More traffic goes through company path | Selected traffic goes through VPN |
| Centralized inspection may be easier | Reduces corporate WAN load |
| Can consume more company bandwidth | Internet traffic may bypass corporate path |
| Security policy can be centralized | Requires careful security design |

The correct choice depends on organizational requirements and security policy.

---

# 📊 WAN Performance

Four important concepts are:

```text
Bandwidth

Latency

Jitter

Packet Loss
```

These are not the same thing.

---

# 🚚 Bandwidth

Bandwidth represents the amount of data that a connection can carry over time.

Example:

```text
100 Mbps

500 Mbps

1 Gbps
```

Think:

> **How much traffic can the road carry?**

---

# ⏱️ Latency

Latency is delay.

It measures how long data takes to travel between points.

Often measured in:

> **milliseconds — ms**

Example:

```text
15 ms
```

is lower latency than:

```text
150 ms
```

---

# 🧠 Bandwidth vs. Latency

Imagine two roads.

Road A:

```text
10 lanes
but
500 miles long
```

Road B:

```text
2 lanes
but
5 miles long
```

Capacity and delay are different characteristics.

Similarly:

> **High bandwidth does not automatically mean low latency.**

---

# 📈 Jitter

Jitter is:

> **Variation in packet delay over time**

Example:

```text
Packet 1 → 20 ms
Packet 2 → 21 ms
Packet 3 → 85 ms
Packet 4 → 19 ms
```

The delay is inconsistent.

---

# ☎️ Why Jitter Matters

Real-time applications such as:

```text
Voice

Video Meetings

Real-Time Communications
```

can be sensitive to jitter.

---

# 📦 Packet Loss

Packet loss occurs when packets fail to reach their destination.

Example:

```text
Sent:
100 packets

Received:
92 packets

Lost:
8 packets
```

Packet loss:

```text
8%
```

---

# 🚨 Effects of Packet Loss

Packet loss can cause:

- Choppy voice
- Video problems
- Slow applications
- Retransmissions
- VPN instability
- Poor remote desktop performance

---

# 📊 Performance Summary

| Metric | Meaning |
|---|---|
| Bandwidth | Data-carrying capacity |
| Latency | Delay |
| Jitter | Variation in delay |
| Packet Loss | Packets that fail to arrive |

---

# 🏎️ Speed Test Caution

A speed test can tell you useful information about:

```text
Download

Upload

Latency
```

But one speed test does not automatically prove:

```text
Wi-Fi is healthy

VPN is healthy

DNS is healthy

Application server is healthy

Entire ISP path is healthy
```

Use it as one piece of evidence.

---

# 🧰 Ping

`ping` can help test:

- Reachability
- Round-trip time
- Packet loss

Example:

```text
ping 8.8.8.8
```

---

# 🧰 Continuous Ping

On Windows:

```text
ping 8.8.8.8 -t
```

This continues until stopped.

Use:

```text
Ctrl + C
```

to stop it.

---

# 🧠 What Can This Reveal?

You might see:

```text
Reply 20 ms
Reply 21 ms
Reply 19 ms
Request timed out
Reply 150 ms
Reply 22 ms
```

Possible clues include:

- Packet loss
- Latency spikes
- Instability

---

# 🧰 Traceroute

Windows uses:

```text
tracert
```

Example:

```text
tracert 8.8.8.8
```

This displays network hops along the path when those devices respond to traceroute probes.

---

# 🗺️ Example

```text
Laptop
  │
  ▼
Home Router
  │
  ▼
ISP
  │
  ▼
Provider Network
  │
  ▼
Internet
  │
  ▼
Destination
```

`tracert` can help you understand portions of that path.

---

# ⚠️ Traceroute Limitations

A hop showing:

```text
*
*
*
```

does not automatically mean:

> **That router is broken.**

Some devices intentionally do not respond to traceroute probes or may rate-limit them.

Look at the entire path and actual application symptoms.

---

# 🧰 PathPing

Windows also includes:

```text
pathping
```

Example:

```text
pathping 8.8.8.8
```

It combines aspects of:

```text
Ping
+
Traceroute
```

and can provide useful packet-loss information over time.

---

# 🧠 Scope Matters

Suppose:

```text
One User
```

cannot access the Internet.

Possible client-specific issue.

Suppose:

```text
Entire Office
```

cannot access the Internet.

Investigate shared infrastructure.

Suppose:

```text
All Offices
```

cannot reach one cloud service.

Investigate the shared service/path rather than immediately changing every workstation.

---

# 🛠️ WAN Troubleshooting Scenario 1

Entire office loses Internet.

Check:

```text
LAN Working?
     ↓
Firewall Up?
     ↓
WAN Interface Up?
     ↓
ISP Equipment Up?
     ↓
Public IP Present?
     ↓
Gateway Reachable?
     ↓
ISP Outage?
```

---

# 🛠️ Scenario 2 — Internet Works, VPN Fails

User can:

```text
Browse Websites
```

but cannot:

```text
Connect VPN
```

This tells you:

> Basic Internet connectivity exists.

Now investigate:

- VPN client
- Credentials
- MFA
- VPN gateway
- VPN configuration
- Firewall policy
- Certificates
- VPN service status

---

# 🛠️ Scenario 3 — VPN Connects, Internal Name Fails

User can connect to VPN.

They can reach:

```text
10.20.30.40
```

but cannot reach:

```text
fileserver.company.local
```

Likely area:

> **DNS**

Check the DNS configuration provided to the VPN client.

---

# 🛠️ Scenario 4 — VPN Connects but Internal Network Fails

VPN says:

```text
Connected
```

but internal resources cannot be reached.

Investigate:

```text
VPN Routes

Corporate Routing

Firewall Rules

Address Conflicts

Client IP Configuration
```

---

# 🛠️ Scenario 5 — Home Network Conflict

Suppose:

```text
Home LAN:
192.168.1.0/24

Corporate Network:
192.168.1.0/24
```

The remote computer now sees the same subnet on:

```text
Local Network

and

Remote Corporate Network
```

This can cause routing conflicts depending on the VPN design.

---

# ⭐ Real-World Lesson

Overlapping private IP ranges can create VPN problems.

This is one reason thoughtful IP address planning matters.

---

# 🛠️ Scenario 6 — Video Calls Are Choppy

Internet works.

Download speed looks acceptable.

But:

```text
Voice cuts out

Video freezes
```

Investigate:

```text
Latency

Jitter

Packet Loss

Wi-Fi Quality

Upload Capacity

WAN Congestion
```

Do not look only at download bandwidth.

---

# 🛠️ Scenario 7 — Primary ISP Failure

The organization has:

```text
ISP-01
Fiber

ISP-02
5G
```

Fiber fails.

Traffic automatically moves to 5G.

This is:

> **Failover**

---

# 🧭 Remote Worker Troubleshooting Workflow

When a remote employee reports:

> **"I can't connect to work."**

Use:

```text
Laptop Working?
      ↓
Connected to Home Wi-Fi?
      ↓
Valid Local IP?
      ↓
Gateway Reachable?
      ↓
Internet Working?
      ↓
DNS Working?
      ↓
VPN Client Working?
      ↓
Authentication Successful?
      ↓
MFA Successful?
      ↓
VPN Connected?
      ↓
VPN Address / Routes Correct?
      ↓
Corporate DNS Working?
      ↓
Internal Resource Reachable?
```

---

# 🧠 Do Not Start by Reinstalling the VPN

If:

```text
User cannot reach Google
```

the VPN client is probably not your first problem.

If:

```text
Internet works
but
VPN authentication fails
```

now VPN authentication becomes relevant.

Follow the evidence.

---

# 📋 Quick Reference

| Term | Meaning |
|---|---|
| LAN | Local Area Network |
| WAN | Wide Area Network |
| ISP | Internet Service Provider |
| SLA | Service-Level Agreement |
| MPLS | Multiprotocol Label Switching |
| SD-WAN | Software-Defined WAN |
| VPN | Virtual Private Network |
| Site-to-Site VPN | Connects networks/sites |
| Remote-Access VPN | Connects individual remote clients |
| Full Tunnel | Most/all traffic follows VPN path |
| Split Tunnel | Selected traffic follows VPN path |
| Bandwidth | Connection capacity |
| Latency | Delay |
| Jitter | Variation in delay |
| Packet Loss | Packets failing to arrive |
| Failover | Moving service to backup resource |
| Redundancy | Additional resources/paths for resilience |

---

# 🧠 Knowledge Check

### 1.
What is the difference between a LAN and WAN?

### 2.
What does ISP stand for?

### 3.
What is a site-to-site VPN used for?

### 4.
What is a remote-access VPN used for?

### 5.
What is split tunneling?

### 6.
What does bandwidth measure?

### 7.
What does latency measure?

### 8.
What is jitter?

### 9.
What is packet loss?

### 10.
What is failover?

---

# ✅ Answers

1. **A LAN covers a limited local area; a WAN connects networks across larger distances.**
2. **Internet Service Provider**
3. **Connecting networks/sites across another network such as the Internet**
4. **Connecting an individual remote client to organizational resources**
5. **Sending selected traffic through the VPN while other traffic can use the local Internet path**
6. **Data-carrying capacity**
7. **Delay**
8. **Variation in packet delay**
9. **Packets that fail to reach their destination**
10. **Moving service/traffic to an available backup when the primary resource fails**

---

# 🎓 Network+ Challenge 1

A branch office needs automatic backup Internet if its fiber circuit fails.

What should you consider?

> **A redundant WAN connection with failover, such as fiber plus cellular.**

---

# 🎓 Network+ Challenge 2

A remote user can browse websites but cannot establish the corporate VPN.

What has already been demonstrated?

> **Basic Internet connectivity is working.**

The troubleshooting scope can move toward the VPN path, authentication, client, or gateway.

---

# 🎓 Network+ Challenge 3

A VPN connects successfully.

The user can ping:

```text
10.20.30.10
```

but cannot access:

```text
server.company.local
```

What should you investigate?

> **DNS**

---

# 🎓 Network+ Challenge 4

Voice calls sound choppy even though a speed test shows high bandwidth.

What other metrics matter?

> **Latency, jitter, and packet loss**

---

# 🎓 Network+ Challenge 5

The primary ISP fails and traffic automatically moves to the backup connection.

What occurred?

> **Failover**

---

# 🎓 Network+ Challenge 6

A remote employee's home LAN and corporate LAN both use:

```text
192.168.1.0/24
```

What potential problem exists?

> **Overlapping IP addressing can cause routing conflicts.**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- LANs connect local devices and WANs connect networks over larger distances.
- ISPs provide external connectivity.
- Fiber, cable, DSL, cellular, satellite, and dedicated services have different characteristics.
- Businesses may use multiple WAN connections for redundancy.
- Failover moves connectivity to a backup path.
- MPLS is a provider WAN technology.
- SD-WAN can manage multiple WAN paths using centralized policies.
- VPNs create protected logical connections over other networks.
- Site-to-site VPNs connect networks.
- Remote-access VPNs connect individual remote users.
- Split and full tunneling handle traffic differently.
- Private IP addresses commonly use NAT to reach the public Internet.
- Bandwidth, latency, jitter, and packet loss measure different things.
- High bandwidth does not guarantee good real-time performance.
- Remote-access problems can originate before, inside, or after the VPN.
- Troubleshooting should identify where the path fails instead of assuming the VPN is responsible.

---

# 🧪 Next Step — Complete Lab 19

In Lab 19 you'll:

- Inspect your real network path
- Identify your default gateway
- Test Internet connectivity
- Measure latency
- Run continuous ping
- Use `tracert`
- Use `pathping`
- Build two sites in Packet Tracer
- Simulate a WAN
- Configure routing between offices
- Test site-to-site connectivity
- Simulate WAN failures
- Work through remote-access VPN scenarios
- Diagnose DNS, routing, and Internet problems
- Compare bandwidth, latency, jitter, and packet loss

➡️ **[Lab 19 — WAN and Remote Connectivity](../labs/lab-19-wan-remote-connectivity.md)**

---

# 📍 Course Progress

```text
🟠 PHASE 4 — NETWORK IMPLEMENTATION

✅ Lesson 17 — Network Cabling & Physical Infrastructure
✅ Lab 17

✅ Lesson 18 — Wireless Networking
✅ Lab 18

✅ Lesson 19 — WAN & Remote Connectivity

        ↓

🟡 NEXT:
Lab 19 — WAN & Remote Connectivity

        ↓

Lesson 20 — Network Monitoring, Security & Final Troubleshooting
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**