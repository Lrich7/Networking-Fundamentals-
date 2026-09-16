# 📘 Lesson 18 — Wireless Networking

Welcome to **Lesson 18 of Networking Fundamentals**.

In Lesson 17, we learned how wired networks physically connect:

```text
PC
 ↓
Patch Cable
 ↓
Wall Jack
 ↓
Patch Panel
 ↓
Switch
```

Wireless networking changes part of that path.

Instead of an Ethernet cable connecting the endpoint to the network:

```text
Laptop
   )))
   )))
Access Point
     │
     ▼
   Switch
```

the endpoint communicates using:

> **Radio frequency signals**

Wireless makes networking more convenient, but it introduces an entirely new set of variables:

- Signal strength
- Distance
- Interference
- Channels
- Frequency bands
- Security
- Roaming
- Physical obstacles

A wireless problem can therefore behave very differently from a wired Ethernet problem.

---

# 🎯 Learning Objectives

By the end of this lesson, you should be able to:

- Explain how Wi-Fi connects devices to a LAN
- Explain the role of a wireless access point
- Understand SSIDs
- Identify common IEEE 802.11 Wi-Fi generations
- Compare 2.4 GHz, 5 GHz, and 6 GHz
- Understand wireless channels
- Explain channel overlap
- Understand channel width
- Explain signal strength
- Understand RSSI
- Recognize common sources of wireless interference
- Understand attenuation
- Explain access-point placement
- Understand roaming
- Explain WPA2 and WPA3
- Compare PSK and enterprise authentication
- Understand guest wireless segmentation
- Recognize common wireless security risks
- Inspect wireless information in Windows
- Use `netsh wlan` commands
- Troubleshoot common wireless problems

---

# 🎓 Network+ Focus

For **CompTIA Network+ N10-009**, pay particular attention to:

- IEEE 802.11
- Wi-Fi generations
- 2.4 GHz
- 5 GHz
- 6 GHz
- Channels
- Channel width
- SSID
- Access points
- Wireless interference
- Signal strength
- WPA2
- WPA3
- Authentication
- PSK
- Enterprise wireless
- Guest networks
- Wireless troubleshooting

---

# 📡 What Is Wi-Fi?

Wi-Fi allows devices to communicate across a network using radio signals instead of a physical Ethernet connection.

Examples include:

```text
Laptop
Phone
Tablet
Barcode Scanner
IoT Device
Wireless Printer
```

---

# 📶 Basic Wireless Network

A simple wireless network looks like:

```text
Laptop
   )))
   )))
Access Point
     │
     │ Ethernet
     ▼
   Switch
     │
     ▼
   Router
```

The access point connects:

> **Wireless devices to the wired LAN**

---

# 📡 Wireless Access Point

A wireless access point is commonly abbreviated:

> **AP**

The AP provides wireless connectivity to clients.

An enterprise environment may have:

```text
AP-01
AP-02
AP-03
AP-04
AP-05
```

distributed throughout the building.

---

# 🧠 AP vs. Wireless Router

A home wireless router commonly combines several functions:

```text
Router
+
Switch
+
Wireless AP
+
NAT
+
DHCP
+
Firewall
```

An enterprise AP may primarily provide:

```text
Wireless Access
        ↓
Wired Network
```

while routing, DHCP, firewalling, and other services are handled elsewhere.

---

# 🏷️ SSID

SSID stands for:

> **Service Set Identifier**

In practical terms, the SSID is the wireless network name users commonly see.

Examples:

```text
Northstar-Corp

Northstar-Guest

Warehouse-WiFi
```

---

# 🧠 SSID Is Not the Password

These are different:

```text
SSID
=
Wireless Network Name

Password / Credentials
=
Authentication
```

---

# 📻 IEEE 802.11

Wi-Fi technologies are based on standards from the:

> **IEEE 802.11 family**

You will encounter both technical standard names and newer consumer-friendly Wi-Fi generation names.

---

# 📋 Common Wi-Fi Generations

| IEEE Standard | Common Name |
|---|---|
| 802.11n | Wi-Fi 4 |
| 802.11ac | Wi-Fi 5 |
| 802.11ax | Wi-Fi 6 |
| 802.11ax using 6 GHz | Wi-Fi 6E |
| 802.11be | Wi-Fi 7 |

Older standards such as:

```text
802.11a
802.11b
802.11g
```

may still appear in certification material and legacy environments.

---

# ⭐ Network+ Tip

Do not focus only on memorizing maximum theoretical speeds.

For troubleshooting, you also need to understand:

```text
Frequency
Channels
Interference
Distance
Security
Compatibility
```

---

# 📻 Frequency Bands

Modern Wi-Fi commonly operates in:

```text
2.4 GHz

5 GHz

6 GHz
```

Not every client or AP supports every band.

---

# 📶 2.4 GHz

2.4 GHz generally provides:

> **Longer range and better obstacle penetration**

than higher-frequency Wi-Fi bands under comparable conditions.

But it also has disadvantages:

- Fewer non-overlapping channel options
- More congestion
- More interference from other technologies

---

# 📶 5 GHz

5 GHz generally provides:

- More channel capacity
- Less congestion than 2.4 GHz in many environments
- Higher performance potential

But generally:

> **Shorter range / less obstacle penetration than 2.4 GHz**

under comparable conditions.

---

# 📶 6 GHz

6 GHz provides additional spectrum for newer Wi-Fi technologies.

Benefits can include:

- More available spectrum
- More wide-channel opportunities
- Less legacy-device congestion

But:

> Client and AP hardware must support 6 GHz.

6 GHz also generally has less range and obstacle penetration than lower-frequency bands under similar conditions.

---

# 📋 Band Comparison

| Feature | 2.4 GHz | 5 GHz | 6 GHz |
|---|---|---|---|
| Range | Generally longer | Generally shorter | Generally shorter |
| Obstacle Penetration | Better | Less | Less |
| Available Spectrum | Limited | More | Much more |
| Legacy Support | Excellent | Very common | Newer devices |
| Congestion | Often high | Usually lower | Often lower |
| Wide Channels | Limited | Better | Excellent |

---

# 🧠 Practical Example

Suppose a laptop is:

```text
Far from AP
+
Behind several walls
```

It might maintain a usable 2.4 GHz connection while struggling on a higher-frequency band.

But in a crowded office close to the AP:

```text
5 GHz
or
6 GHz
```

may provide much better performance.

There is no single "best band" for every situation.

---

# 📡 Wireless Channels

Wi-Fi frequency bands are divided into:

> **Channels**

An AP transmits on a selected channel.

Nearby APs using conflicting channel space can interfere with each other.

---

# 📻 2.4 GHz Channels

In the United States, a common 2.4 GHz channel plan using 20 MHz channels is:

```text
1

6

11
```

These are commonly used because they do not overlap one another in the typical 2.4 GHz Wi-Fi channel arrangement.

---

# ⭐ Network+ Memory Tip

For 2.4 GHz in the U.S., remember:

> **1 — 6 — 11**

---

# 🚨 Overlapping Channels

Imagine three nearby APs:

```text
AP-01
Channel 1

AP-02
Channel 3

AP-03
Channel 6
```

Channel 3 overlaps surrounding channel space.

A cleaner basic design might use:

```text
AP-01
Channel 1

AP-02
Channel 6

AP-03
Channel 11
```

---

# 📡 5 GHz Channels

5 GHz provides many more channel options than 2.4 GHz.

This makes it easier to design networks with:

- Less overlap
- Greater capacity
- Wider channels

Some 5 GHz channels may be subject to DFS requirements depending on the regulatory domain.

---

# 📏 Channel Width

Wireless networks can use different channel widths.

Common examples include:

```text
20 MHz
40 MHz
80 MHz
160 MHz
```

Newer technologies may support additional options.

---

# 🧠 Wider Is Not Always Better

A wider channel can provide:

> **More potential throughput**

but consumes:

> **More spectrum**

In a dense environment:

```text
Many APs
+
Very Wide Channels
```

can actually make channel planning more difficult.

---

# 🏢 Example

Small home:

```text
One AP
Few Neighbors
```

A wider channel may work well.

Dense office:

```text
20 APs
Many Clients
Neighboring Networks
```

Narrower channel widths may provide better overall spectrum reuse.

Wireless design is about:

> **Capacity and reliability — not just maximum link speed.**

---

# 📶 Signal Strength

Wireless performance depends heavily on signal strength.

Signal strength is commonly represented using:

> **dBm**

Values are usually negative.

Example:

```text
-40 dBm
```

is stronger than:

```text
-75 dBm
```

because `-40` is closer to zero.

---

# ⭐ Easy Memory Trick

```text
Closer to 0
=
Stronger Signal
```

So:

```text
-45 dBm
```

is stronger than:

```text
-80 dBm
```

---

# 📊 Example Signal Levels

These are rough guidelines, not universal guarantees:

| RSSI | General Interpretation |
|---|---|
| -30 dBm | Extremely strong |
| -50 dBm | Strong |
| -60 dBm | Generally good |
| -67 dBm | Often usable for many business applications |
| -70 dBm | Weaker |
| -80 dBm | Poor |
| -90 dBm | Near unusable |

Actual requirements depend on the application, device, environment, noise, data rate, and design goals.

---

# 📉 Attenuation

Attenuation means:

> **Loss of signal strength**

Wireless signals weaken as they travel.

---

# 🧱 Things That Weaken Wi-Fi

Examples include:

- Distance
- Concrete
- Brick
- Metal
- Elevators
- Filing cabinets
- HVAC equipment
- Dense walls
- Certain types of glass
- People and water-containing materials

---

# 🧠 Example

This AP placement:

```text
AP
 │
 │ Open Hallway
 │
 ▼
Laptop
```

may perform much better than:

```text
AP
 │
 █ Concrete Wall
 │
 █ Elevator Shaft
 │
 █ Metal Storage
 │
 ▼
Laptop
```

even if the straight-line distance is similar.

---

# 📻 Wireless Interference

Wireless networks share radio spectrum with other devices.

Possible interference sources include:

- Other Wi-Fi networks
- Bluetooth devices
- Microwave ovens
- Wireless cameras
- Some cordless devices
- IoT devices
- Neighboring businesses

---

# 🍿 Microwave Example

Microwave ovens can produce interference in the 2.4 GHz range.

A user might report:

> "Wi-Fi gets terrible every day around lunchtime."

That sounds strange until you investigate the physical environment.

---

# 📊 Signal vs. Noise

Strong signal alone is not the entire story.

Wireless communication also depends on how clearly the signal can be distinguished from background noise.

This relationship is often described using:

> **SNR — Signal-to-Noise Ratio**

Higher usable SNR generally provides better conditions for communication.

---

# 🏢 AP Placement

Poor AP placement can create major problems.

Avoid blindly placing APs:

- Inside metal cabinets
- Behind large obstacles
- At one extreme end of the building
- Wherever an Ethernet jack happens to exist

Wireless coverage should be intentionally designed.

---

# 📡 Better Placement

A simplified office might use:

```text
        AP-01
          )))
       Offices

AP-02  )))     (((  AP-03

Conference      Offices
Rooms
```

The goal is appropriate:

- Coverage
- Capacity
- Channel reuse
- Roaming

---

# 🚫 More APs Is Not Automatically Better

Adding access points without planning can increase:

- Interference
- Co-channel contention
- Management complexity

Wireless design is not:

> **Bad Wi-Fi → Keep adding APs**

---

# 🔄 Roaming

In an enterprise wireless network, a user may move:

```text
Office
   ↓
Hallway
   ↓
Conference Room
```

while remaining connected to the same wireless network.

The client may transition between:

```text
AP-01
   ↓
AP-02
```

This is called:

> **Roaming**

---

# 🧠 Who Decides to Roam?

The wireless client plays an important role in deciding when to roam.

Different devices may behave differently.

One laptop might switch APs quickly.

Another might remain connected to a distant AP for too long.

This is sometimes described as a:

> **Sticky client**

---

# 📛 Same SSID Across APs

Enterprise APs commonly broadcast the same corporate SSID:

```text
Northstar-Corp
```

from multiple APs.

Example:

```text
AP-01 → Northstar-Corp

AP-02 → Northstar-Corp

AP-03 → Northstar-Corp
```

This allows users to move throughout the coverage area while using the same network identity.

---

# 🔐 Wireless Security

Wireless signals can extend beyond your physical walls.

That makes security extremely important.

Common Wi-Fi security technologies include:

```text
WPA2

WPA3
```

---

# 🔐 WPA2

WPA2 has been widely deployed for many years.

It remains common in existing networks.

---

# 🔐 WPA3

WPA3 provides newer wireless security capabilities and is generally preferred when supported by the environment and clients.

---

# 🚫 Avoid Legacy Wireless Security

Older security mechanisms such as:

```text
WEP
```

should not be used for modern secure wireless networks.

WEP is obsolete and insecure.

---

# 🔑 Personal / PSK Authentication

A small wireless network might use:

> **Pre-Shared Key — PSK**

Example:

```text
SSID:
Northstar-WiFi

Password:
One shared wireless password
```

Every authorized user may know the same secret.

This is simple, but it becomes harder to manage at scale.

---

# 🏢 Enterprise Authentication

Business wireless networks may use individual authentication instead of one shared password.

Commonly this involves:

```text
802.1X
+
RADIUS
```

Conceptually:

```text
Laptop
   )))
   )))
Access Point
     │
     ▼
Authentication System
```

Users or devices authenticate with individual credentials or certificates depending on the implementation.

---

# ⭐ PSK vs. Enterprise

| PSK | Enterprise |
|---|---|
| Shared secret | Individual authentication |
| Simpler | More infrastructure |
| Common at home/small networks | Common in business |
| Harder to revoke one person's access | Individual access can be managed |

---

# 👥 Guest Wireless

Businesses often provide:

```text
Corporate Wi-Fi

Guest Wi-Fi
```

These should not necessarily provide the same network access.

---

# 🧱 Guest Segmentation

A guest network might be designed:

```text
GUEST DEVICES
      )))
      )))
   Guest SSID
       │
       ▼
   Guest VLAN
       │
       ▼
   Firewall
       │
       ├────X──── Internal Servers
       │
       ▼
    Internet
```

The goal:

> Guests can reach the Internet without receiving normal corporate LAN access.

---

# 🧠 SSID and VLANs

Wireless SSIDs can be mapped to VLANs.

Example:

| SSID | VLAN |
|---|---:|
| Northstar-Corp | 10 |
| Northstar-Guest | 50 |
| Northstar-IoT | 60 |

Now concepts from Lesson 12 return:

> **Wireless still connects into the switched network.**

---

# 🔗 Wireless Is Still Networking

A wireless client still needs:

```text
Wi-Fi Association
        ↓
Correct VLAN
        ↓
DHCP
        ↓
IP Address
        ↓
Subnet Mask
        ↓
Gateway
        ↓
DNS
        ↓
Routing
        ↓
Services
```

Wireless replaces the endpoint's physical Ethernet connection.

It does not eliminate TCP/IP.

---

# 📦 DHCP on Wireless

After connecting to an SSID, a wireless client commonly requests addressing using DHCP.

So:

```text
Connected to Wi-Fi
```

does not necessarily mean:

```text
Has Valid IP Configuration
```

---

# 🧠 Example

Laptop shows:

```text
Connected
```

but receives:

```text
169.254.x.x
```

That tells you:

> The wireless association may be working, but DHCP may not be.

This is an important troubleshooting distinction.

---

# 📛 DNS on Wireless

Suppose:

```text
Wi-Fi Connected
IP Valid
Gateway Reachable
8.8.8.8 Reachable
Hostname Fails
```

That looks more like:

> **DNS**

than a radio problem.

Use the troubleshooting skills from Lesson 15.

---

# 🛠️ Windows Wireless Commands

Windows includes useful wireless troubleshooting commands.

Open Command Prompt or PowerShell.

---

# 📡 Show Wireless Interfaces

Run:

```text
netsh wlan show interfaces
```

This can display information such as:

- SSID
- BSSID
- Radio type
- Channel
- Receive rate
- Transmit rate
- Signal percentage

---

# 📡 Show Wireless Networks

Run:

```text
netsh wlan show networks mode=bssid
```

This can show nearby visible wireless networks and information about their AP radios.

Use this only for normal observation of wireless networks visible to your own device.

---

# 🧠 BSSID

SSID identifies the wireless network.

BSSID identifies a particular wireless radio/AP interface.

Conceptually:

```text
SSID:
Northstar-Corp

AP-01 BSSID:
AA:AA:AA:AA:AA:01

AP-02 BSSID:
AA:AA:AA:AA:AA:02
```

Both APs can advertise:

```text
Northstar-Corp
```

while having different BSSIDs.

---

# 🧰 Windows Network Commands Still Matter

Also use:

```text
ipconfig /all
```

```text
ping
```

```text
tracert
```

```text
nslookup
```

```text
Get-NetAdapter
```

```text
Get-NetIPConfiguration
```

Wireless troubleshooting often requires both:

```text
Wi-Fi Information
+
IP Networking Information
```

---

# 🛠️ Wireless Troubleshooting Scenario 1

User says:

> "I don't see the company Wi-Fi."

Investigate:

```text
Wi-Fi enabled?
        ↓
Airplane mode?
        ↓
SSID being broadcast?
        ↓
AP powered?
        ↓
AP connected?
        ↓
Client supports required band?
        ↓
Client in coverage area?
```

---

# 🛠️ Scenario 2 — Connected but No IP

User:

```text
Connected to SSID
```

but:

```text
169.254.25.18
```

Investigate:

> **DHCP path**

Possible causes:

- DHCP server unavailable
- Wrong VLAN
- DHCP relay problem
- Scope exhausted
- AP/uplink configuration problem

---

# 🛠️ Scenario 3 — Weak Signal

User:

```text
Works near AP

Fails in conference room
```

Investigate:

- Distance
- Walls
- Metal
- AP placement
- Band
- Signal strength
- Coverage design

---

# 🛠️ Scenario 4 — Slow Wi-Fi

Possible causes include:

```text
Interference

Congestion

Weak Signal

Channel Overlap

Too Many Clients

Poor AP Placement

Client Capability

Backhaul/Uplink Problem

Internet Problem
```

Do not automatically assume:

> **Slow Internet = Bad Wi-Fi**

---

# 🛠️ Scenario 5 — One User Only

If:

```text
50 users work normally
```

and:

```text
1 laptop has problems
```

investigate the client.

Potential areas:

- Wireless adapter
- Driver
- Saved profile
- Authentication
- Client band support
- Power-saving behavior
- Local configuration

---

# 🛠️ Scenario 6 — Everyone Near One AP

If:

```text
Everyone near AP-03 has problems
```

but other areas work:

> Investigate AP-03 and its local environment.

Check:

- AP status
- Ethernet uplink
- Switch port
- PoE
- Channel
- Interference
- Configuration

---

# 🛠️ Scenario 7 — Entire Wireless Network

If:

```text
All APs
All Users
All Locations
```

are affected, investigate shared dependencies such as:

- DHCP
- DNS
- Authentication
- Wireless controller/cloud management
- Switching
- Firewall
- Internet connectivity

Scope is one of your best troubleshooting clues.

---

# 🧭 Wireless Troubleshooting Workflow

```text
Wi-Fi Enabled?
      ↓
SSID Visible?
      ↓
Can Client Associate?
      ↓
Authentication Successful?
      ↓
Signal Acceptable?
      ↓
Valid IP Address?
      ↓
Correct VLAN?
      ↓
Gateway Reachable?
      ↓
DNS Working?
      ↓
Internal Resources?
      ↓
Internet?
```

---

# 📋 Quick Reference

| Concept | Meaning |
|---|---|
| AP | Wireless Access Point |
| SSID | Wireless network identifier/name |
| BSSID | Identifier for a specific AP/radio |
| 2.4 GHz | Longer-range, more congested band |
| 5 GHz | More spectrum, shorter range |
| 6 GHz | Newer spectrum with more capacity |
| Channel | Portion of wireless spectrum |
| Channel Width | Amount of spectrum used |
| RSSI | Received signal strength indicator |
| SNR | Signal-to-noise ratio |
| WPA2 | Common wireless security standard |
| WPA3 | Newer wireless security standard |
| PSK | Pre-shared key |
| 802.1X | Port/network access authentication framework |
| RADIUS | Common centralized AAA protocol/server role |
| Roaming | Client moves between AP coverage areas |

---

# 🧠 Knowledge Check

### 1.
What does an access point do?

### 2.
What is an SSID?

### 3.
What are the three major Wi-Fi frequency bands currently encountered?

### 4.
Which band generally provides better range: 2.4 GHz or 5 GHz?

### 5.
What three 2.4 GHz channels are commonly used as non-overlapping 20 MHz channels in the U.S.?

### 6.
Is `-45 dBm` stronger or weaker than `-80 dBm`?

### 7.
What does roaming mean?

### 8.
What is a PSK?

### 9.
What is the purpose of guest wireless segmentation?

### 10.
Does connecting to an SSID prove DHCP and DNS are working?

---

# ✅ Answers

1. **It connects wireless clients to the network.**
2. **The identifier/name of a wireless network.**
3. **2.4 GHz, 5 GHz, and 6 GHz.**
4. **2.4 GHz generally provides better range under comparable conditions.**
5. **1, 6, and 11.**
6. **Stronger.**
7. **Moving between wireless AP coverage areas while maintaining network connectivity.**
8. **A pre-shared key used to authenticate to a wireless network.**
9. **To separate guest devices from protected internal resources while providing appropriate access such as Internet connectivity.**
10. **No.**

---

# 🎓 Network+ Challenge 1

An office has three nearby 2.4 GHz APs using:

```text
Channel 1
Channel 3
Channel 6
```

What is the concern?

> **Channel overlap**

A basic U.S. 2.4 GHz design commonly uses:

```text
1
6
11
```

---

# 🎓 Network+ Challenge 2

Which is the stronger signal?

### A. -82 dBm
### B. -72 dBm
### C. -60 dBm
### D. -45 dBm

> **Answer: D — -45 dBm**

---

# 🎓 Network+ Challenge 3

A laptop connects to Wi-Fi but receives:

```text
169.254.10.20
```

Which service should you investigate?

> **DHCP**

---

# 🎓 Network+ Challenge 4

Employees can access corporate servers through `Northstar-Corp`.

Guests should only have Internet access.

What should you implement?

> **A separate guest SSID mapped to an appropriately isolated guest network/VLAN with firewall policy controlling access.**

---

# 🎓 Network+ Challenge 5

Wi-Fi becomes unreliable only in a break room when a particular appliance is operating.

What should you investigate?

> **Radio-frequency interference**

---

# 🎓 Network+ Challenge 6

All users near one AP lose wireless connectivity, but every other area works normally.

What does the scope suggest?

> **Investigate that AP, its power/uplink, configuration, and local RF environment before assuming the entire wireless infrastructure has failed.**

---

# 📝 Key Takeaways

Before moving on, make sure you understand:

- Wi-Fi uses radio signals to connect clients to a network.
- APs bridge wireless clients into the wired network.
- SSID identifies the wireless network.
- BSSID identifies a specific AP/radio.
- Modern Wi-Fi commonly uses 2.4, 5, and 6 GHz.
- 2.4 GHz generally travels farther but has less available spectrum.
- 5 GHz provides more channel options.
- 6 GHz provides substantial additional spectrum but requires compatible devices.
- Channels and channel width affect wireless performance.
- In the U.S., 1, 6, and 11 are commonly used for 20 MHz 2.4 GHz channel planning.
- Signal values closer to 0 dBm are stronger.
- Physical obstacles and interference affect Wi-Fi.
- More APs do not automatically mean better Wi-Fi.
- Clients roam between APs.
- WPA2 and WPA3 protect wireless networks.
- PSK uses a shared secret.
- Enterprise wireless can use 802.1X/RADIUS-based authentication.
- Guest wireless should generally be separated from corporate resources.
- Wireless clients still depend on DHCP, DNS, VLANs, routing, and other network services.
- Troubleshooting should determine whether the problem is RF, authentication, addressing, DNS, routing, or something else.

---

# 🧪 Next Step — Complete Lab 18

In Lab 18 you'll:

- Inspect your own Windows Wi-Fi connection
- Identify SSID and BSSID
- Identify channel and radio type
- Examine nearby wireless networks
- Compare signal levels
- Build a wireless network in Packet Tracer
- Configure an SSID
- Configure wireless security
- Connect wireless clients
- Verify DHCP
- Build corporate and guest wireless
- Break authentication
- Break DHCP
- Troubleshoot coverage
- Diagnose several wireless support tickets

➡️ **[Lab 18 — Wireless Networking](../labs/lab-18-wireless-networking.md)**

---

# 📍 Course Progress

```text
🟠 PHASE 4 — NETWORK IMPLEMENTATION

✅ Lesson 17 — Network Cabling & Physical Infrastructure
✅ Lab 17
✅ Lesson 18 — Wireless Networking

        ↓

🟡 NEXT:
Lab 18 — Wireless Networking

        ↓

Lesson 19 — WAN & Remote Connectivity
```

---

# 📚 Course Navigation

➡️ **[Networking Lessons](README.md)**

➡️ **[Networking Labs](../labs/README.md)**

➡️ **[Projects](../projects/README.md)**

➡️ **[Return to Main README](../README.md)**