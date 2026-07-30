# Enterprise Multi-Site Network Infrastructure

# IP Addressing Plan

---

**Project Name:** Enterprise Multi-Site Network Infrastructure

**Project Author:** Gabriel Tobi Idowu

**Version:** 1.0

**Date:** July 2026

---

# Table of Contents

1. Overview
2. Addressing Strategy
3. DMVPN Tunnel Network
4. Branch LAN Networks
5. Point-to-Point WAN Links
6. Core Infrastructure
7. Distribution Layer
8. Edge Layer
9. Hub Routers
10. Branch Routers
11. Address Summary

---

# 1. Overview

This document defines the IPv4 addressing scheme used throughout the Enterprise Multi-Site Network Infrastructure project.

The addressing plan was designed to provide consistency, simplify troubleshooting, and support future expansion while following enterprise addressing best practices.

Private IPv4 addressing (RFC 1918) is used throughout the enterprise.

---

# 2. Addressing Strategy

The network uses separate address ranges for:

- Branch LANs
- Point-to-point WAN links
- DMVPN Tunnel Network
- Infrastructure interfaces
- Loopback interfaces

This separation improves readability and simplifies operational management.

---

# 3. DMVPN Tunnel Network

| Device | Tunnel Interface | IP Address |
|---------|------------------|------------|
| HUB-1 | Tunnel0 | 172.16.0.1/24 |
| HUB-2 | Tunnel0 | 172.16.0.2/24 |
| BR-LONDON | Tunnel0 | 172.16.0.11/24 |
| BR-DUBLIN | Tunnel0 | 172.16.0.12/24 |
| BR-AMSTERDAM | Tunnel0 | 172.16.0.13/24 |
| BR-FRANKFURT | Tunnel0 | 172.16.0.14/24 |

---

# 4. Branch LAN Networks

| Branch | Network | Default Gateway |
|---------|---------|-----------------|
| London | 192.168.10.0/24 | 192.168.10.1 |
| Dublin | 192.168.20.0/24 | 192.168.20.1 |
| Amsterdam | 192.168.30.0/24 | 192.168.30.1 |
| Frankfurt | 192.168.40.0/24 | 192.168.40.1 |

---

# 5. Point-to-Point WAN Links

| Link | Network |
|------|---------|
| EDGE-1 ↔ HUB-1 | 172.16.100.0/30 |
| HUB-1 ↔ LONDON | 172.16.100.8/30 |
| HUB-1 ↔ DUBLIN | 172.16.100.12/30 |
| HUB-2 ↔ AMSTERDAM | 172.16.100.16/30 |
| HUB-2 ↔ FRANKFURT | 172.16.100.20/30 |
| HUB-2 ↔ LONDON | 172.16.100.24/30 |
| HUB-2 ↔ DUBLIN | 172.16.100.28/30 |
| HUB-1 ↔ AMSTERDAM | 172.16.100.32/30 |
| HUB-1 ↔ FRANKFURT | 172.16.100.36/30 |
| EDGE-2 ↔ HUB-2 | 172.16.100.4/30 |

---

# 6. Core Infrastructure

The Core Layer provides high-speed Layer 3 transport between the Distribution Layer and WAN Edge.

Core Devices:

- CORE-1
- CORE-2

Refer to the device configuration files for complete interface assignments.

---

# 7. Distribution Layer

Distribution Devices:

- DIST-1
- DIST-2

Responsibilities:

- Inter-VLAN Routing
- HSRP
- EtherChannel
- VRF-Lite

---

# 8. Edge Layer

Edge Devices:

- EDGE-1
- EDGE-2

Responsibilities:

- eBGP
- iBGP
- MP-BGP
- BFD

---

# 9. Hub Routers

| Device | WAN Interface | Address |
|---------|--------------|---------|
| HUB-1 | Ethernet0/0 | 172.16.100.2/30 |
| HUB-2 | Ethernet0/0 | 172.16.100.6/30 |

---

# 10. Branch Routers

| Router | Primary WAN | Secondary WAN | LAN |
|---------|-------------|---------------|-----|
| BR-LONDON | 172.16.100.10 | 172.16.100.26 | 192.168.10.1 |
| BR-DUBLIN | 172.16.100.14 | 172.16.100.30 | 192.168.20.1 |
| BR-AMSTERDAM | 172.16.100.34 | 172.16.100.18 | 192.168.30.1 |
| BR-FRANKFURT | 172.16.100.38 | 172.16.100.22 | 192.168.40.1 |

---

# 11. Address Summary

| Address Range | Purpose |
|--------------|---------|
| 172.16.0.0/24 | DMVPN Tunnel Network |
| 172.16.100.0/30 – 172.16.100.39/30 | Point-to-Point WAN Links |
| 192.168.10.0/24 | London LAN |
| 192.168.20.0/24 | Dublin LAN |
| 192.168.30.0/24 | Amsterdam LAN |
| 192.168.40.0/24 | Frankfurt LAN |

---

# Conclusion

The addressing plan provides a structured and scalable IPv4 allocation for the simulated enterprise environment.

By separating infrastructure links, tunnel interfaces, and branch LANs into dedicated address ranges, the design simplifies network operations, improves readability, and supports future expansion with minimal readdressing.
