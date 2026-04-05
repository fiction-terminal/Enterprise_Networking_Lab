# Cisco Enterprise Mega Lab

![Cisco](https://img.shields.io/badge/Cisco-Networking-blue)
![CCNA](https://img.shields.io/badge/Level-CCNA%20%2F%20CCNP-orange)
![Packet Tracer](https://img.shields.io/badge/Simulator-Packet%20Tracer-green)
![License](https://img.shields.io/badge/License-Lab%20Project-lightgrey)

---

# Overview

This repository contains a **full enterprise network simulation lab** designed to practice advanced Cisco networking concepts including switching, routing, redundancy, security, and network services.

The lab simulates **two enterprise offices connected through a core network and edge router with Internet connectivity.**

This project is ideal for practicing:

- CCNA
- CCNP Enterprise
- Real enterprise network design concepts

---

# Network Topology

```
                Internet
                   │
                   R1
              ┌────┴────┐
              │         │
            CSW1       CSW2
              │           │
     ┌────────┼────────┐ ┌┼─────────┐
     │        │        │ ││         │
   DSW-A1   DSW-A2   DSW-B1      DSW-B2
     │ │ │               │ │ │
   ASW-A1 ASW-A2 ASW-A3  ASW-B1 ASW-B2 ASW-B3
        │                     │
     PCs / Phones          PCs / Phones
```

---

# Network Architecture

| Layer | Devices |
|-----|------|
| Edge | R1 |
| Core | CSW1, CSW2 |
| Distribution | DSW-A1, DSW-A2, DSW-B1, DSW-B2 |
| Access | ASW-A1, ASW-A2, ASW-A3, ASW-B1, ASW-B2, ASW-B3 |
| Wireless | WLC1 + LWAPs |
| Server | SRV1 |

---

# Technologies Used

| Category | Technologies |
|--------|-------------|
| Switching | VLANs, VTPv2, Trunking |
| Link Aggregation | EtherChannel (PAgP / LACP) |
| Redundancy | HSRPv2 |
| Routing | OSPF |
| Spanning Tree | Rapid PVST+ |
| Network Services | DHCP, DNS, NTP |
| Management | SNMP, Syslog, SSH |
| NAT | Static NAT, Dynamic PAT |
| Security | ACL, Port Security, DHCP Snooping, DAI |
| Wireless | WLC + LWAP |
| IPv6 | Dual Stack Deployment |

---

# VLAN Design

| VLAN | Name | Purpose |
|----|------|------|
| 10 | PCs | User Devices |
| 20 | Phones | VoIP Phones |
| 30 | Servers | Server Network |
| 40 | WiFi | Wireless Clients |
| 99 | Management | Device Management |

---

# HSRP Gateway Design

### Office A

| VLAN | VIP | Active Router |
|----|----|----|
| 99 | 10.0.0.1 | DSW-A1 |
| 10 | 10.1.0.1 | DSW-A1 |
| 20 | 10.2.0.1 | DSW-A2 |
| 40 | 10.6.0.1 | DSW-A2 |

### Office B

| VLAN | VIP | Active Router |
|----|----|----|
| 99 | 10.0.0.17 | DSW-B1 |
| 10 | 10.3.0.1 | DSW-B1 |
| 20 | 10.4.0.1 | DSW-B2 |
| 30 | 10.5.0.1 | DSW-B2 |

---

# Network Services

| Service | Location |
|------|------|
| DHCP Server | R1 |
| DNS Server | SRV1 |
| NTP Server | R1 |
| Syslog Server | SRV1 |
| SNMP Monitoring | All devices |
| FTP Server | SRV1 |

---

# NAT Configuration

| Type | Description |
|----|----|
| Static NAT | Internet access to SRV1 |
| Dynamic PAT | Internal users access Internet |

Public NAT Pool:

```
203.0.113.200 – 203.0.113.207
```

---

# Security Features

| Feature | Purpose |
|------|------|
| Extended ACL | Control traffic between offices |
| Port Security | Prevent unauthorized devices |
| DHCP Snooping | Protect against rogue DHCP |
| Dynamic ARP Inspection | Prevent ARP spoofing |

---

# IPv6 Implementation

| Device | IPv6 Network |
|------|------|
| R1 | 2001:db8:a::/64 |
| R1 Backup | 2001:db8:b::/64 |
| Core Links | 2001:db8:a1::/64 |
| Core Links | 2001:db8:a2::/64 |

---

# Wireless Configuration

| Parameter | Value |
|------|------|
| SSID | Wi-Fi |
| Security | WPA2 AES |
| Password | cisco123 |
| VLAN | 40 |

---

# Repository Structure

```
Cisco-Mega-Lab
│
├── configs
│   ├── routers
│   ├── core-switches
│   ├── distribution-switches
│   └── access-switches
│
├── topology
│   └── network-diagram.png
│
├── lab-files
│   └── packet-tracer-file.pkt
│
└── README.md
```

---

# Verification Commands

Useful commands to verify configurations.

```
show ip ospf neighbor
show etherchannel summary
show standby brief
show vlan brief
show ip nat translations
show port-security interface
```

---

# Lab Objectives

This lab helps build skills in:

- Enterprise network design
- Layer-2 and Layer-3 redundancy
- Routing protocol deployment
- Network service configuration
- Security hardening
- IPv6 transition
- Wireless networking

---

# Author

Network Lab Project for hands-on **Cisco Networking practice**.


