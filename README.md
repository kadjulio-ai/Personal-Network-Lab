# Home Network Lab – Double NAT Configuration

## Project Overview

This project demonstrates how to configure a **Double NAT** environment using an ISP modem and a TP-Link router.

The objective was to create an isolated home network for studying networking concepts such as NAT, DHCP, routing, and network segmentation.

---

## Objectives

- Configure a Double NAT environment
- Create an isolated private network
- Understand LAN and WAN communication
- Practice DHCP configuration
- Learn IPv4 addressing
- Understand default gateways
- Study basic routing concepts

---

## Hardware

- ISP Modem (Vivo)
- TP-Link TL-WR940N V5
- Windows PC

---

## Network Topology

```
                Internet
                    │
                    │
          ISP Modem (Vivo)
          LAN: 192.168.15.1
                    │
               LAN Port
                    │
                    │
              WAN Port
                    │
        TP-Link TL-WR940N
        LAN: 192.168.50.1
        DHCP: Enabled
                    │
         ───────────────────
          Wi-Fi / LAN Clients
                    │
          PC: 192.168.50.x
```

---

## TP-Link Configuration

### Operation Mode

- Wireless Router

### LAN Configuration

| Setting | Value |
|---------|-------|
| IP Address | 192.168.50.1 |
| Subnet Mask | 255.255.255.0 |

### WAN Configuration

| Setting | Value |
|---------|-------|
| Connection Type | Dynamic IP (DHCP) |

### DHCP Server

- Enabled

---

## Physical Connections

```
ISP Modem (LAN)
       │
       ▼
TP-Link (WAN)
```

The computer was connected to the TP-Link via Wi-Fi.

---

## Challenges Encountered

### IP Address Conflict

Initially, both the ISP modem and the TP-Link router were configured using the same private subnet.

This caused:

- Loss of access to the router's management page
- Routing conflicts
- Incorrect default gateway assignment
- Communication problems between devices

### Solution

The TP-Link LAN address was changed from:

```
192.168.15.1
```

to

```
192.168.50.1
```

This created two different private networks.

### Firmware update ruined the double NAT configuration

After configuring the double NAT setup, I noticed that the TP-Link router was running an outdated firmware version. I updated the firmware to the latest release. 

This caused:

- the firmware upgrade to reset all settings to the factory defaults
- lose all the double NAT settings 

### Solution

Configure the router again from scratch.

---

## Validation

The configuration was validated by confirming:

- Successful access to the TP-Link management interface.
- PC received an IP address in the 192.168.50.0/24 network.
- Default gateway became 192.168.50.1.
- TP-Link WAN interface received an IP address from the ISP modem.
- Internet access was working correctly.

---

## Networking Concepts Practiced

- Double NAT
- Network Address Translation (NAT)
- DHCP
- IPv4 Addressing
- Default Gateway
- LAN vs WAN
- Routing
- Network Segmentation
- Basic Network Troubleshooting

---

## Windows Commands Used

```cmd
ipconfig

ipconfig /release

ipconfig /renew

ping 192.168.50.1

tracert 8.8.8.8
```

---

## Lessons Learned

During this project I learned how to:

- Configure a home router as a secondary router.
- Create a Double NAT environment.
- Configure DHCP services.
- Resolve IP address conflicts.
- Connect routers using the WAN interface.
- Troubleshoot network issues using Windows networking tools.
- Understand routing between private networks.
- Document a networking project.
- Always check for firmware updates before spending time on the initial configuration, since updating the firmware may reset all settings to the factory defaults.

---

## Skills Demonstrated

- Network Configuration
- Router Administration
- DHCP Configuration
- IPv4 Networking
- NAT
- Routing
- Troubleshooting
- Documentation
- Problem Solving

---

## Future Improvements

- Configure Port Forwarding
- Implement Firewall Rules
- Create a Guest Network
- Experiment with VLANs
- Capture network traffic using Wireshark
- Deploy a local DNS server
- Add network monitoring tools



