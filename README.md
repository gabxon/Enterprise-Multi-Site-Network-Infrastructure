# Enterprise Multi-Site Network Infrastructure

## Project Overview

This project demonstrates the design, implementation, and validation of a resilient multi-site enterprise network built in **EVE-NG** using Cisco enterprise technologies.

The solution follows a hierarchical campus architecture with a redundant Internet edge, dual DMVPN hubs, dynamic routing, gateway redundancy, and departmental segmentation using VRF-Lite.

The environment simulates a headquarters campus connected to four international branch offices through a highly available WAN infrastructure.

---
<h2 align="center">Network Topology</h2>

<p align="center">
  <img src="Topology/topology.png" alt="Enterprise Multi-Site Network Infrastructure" width="100%">
</p>

## 📑 Table of Contents

- [Project Overview](#project-overview)
- [Network Topology](#network-topology)
- [Architecture Overview](#architecture-overview)
- [Technologies Implemented](#technologies-implemented)
- [Network Components](#network-components)
- [High Availability](#high-availability)
- [Validation](#validation)
- [Repository Structure](#repository-structure)
- [Future Enhancements](#future-enhancements)
- [Author](#author)

### Architecture Overview

The enterprise network consists of:

- Dual ISP Internet Edge
- Dual Edge Routers (eBGP & iBGP)
- Redundant Core Backbone (OSPF + BFD)
- Redundant Distribution Layer (HSRP + VRF-Lite)
- Layer 2 Access Network
- Dedicated Server Farm
- Dual DMVPN Hub Architecture
- Four International Branch Offices


---

## Architecture Highlights

- Hierarchical Campus Design
- Dual ISP Internet Edge
- Core / Distribution / Access Layers
- Dual DMVPN Hub Architecture
- Four International Branch Offices
- Server Farm
- Departmental Segmentation using VRF-Lite
- High Availability using HSRP and BFD

---

## Technologies Implemented

| Technology | Role | Status |
|------------|------|:------:|
| VRF-Lite | Layer 3 Network Segmentation | ✅ |
| VLAN Segmentation | Department Isolation | ✅ |
| Inter-VLAN Routing | Communication Between VLANs | ✅ |
| Multi-Area OSPF | Internal Dynamic Routing | ✅ |
| eBGP | ISP Connectivity | ✅ |
| iBGP | Internal Route Exchange | ✅ |
| MP-BGP | VPNv4 Route Distribution | ✅ |
| DMVPN Phase 3 | Branch WAN Connectivity | ✅ |
| NHRP | Tunnel Resolution | ✅ |
| HSRP | Default Gateway Redundancy | ✅ |
| EtherChannel (LACP) | Link Aggregation | ✅ |
| BFD | Fast Failure Detection | ✅ |
| SSH | Secure Device Management | ✅ |
## Network Components

## Project Statistics

| Item | Value |
|------|------:|
| Headquarters | 1 |
| Branch Offices | 4 |
| Internet Service Providers | 2 |
| DMVPN Hubs | 2 |
| Core Routers | 2 |
| Distribution Switches | 2 |
| Access Switches | 6 |
| Server Farm | 6 Servers |
| VRFs | 5 |
| VLANs | 5 |

### Headquarters

- EDGE-1
- EDGE-2
- CORE-1
- CORE-2
- DIST-1
- DIST-2
- ACCESS Switches
- Server Farm

### WAN

- HUB-1
- HUB-2

### Branch Offices

- London
- Dublin
- Amsterdam
- Frankfurt

---

## High Availability

The enterprise network incorporates multiple redundancy mechanisms:

- Dual ISP Connectivity
- HSRP Gateway Redundancy
- EtherChannel (LACP)
- BFD Fast Convergence
- Redundant Distribution Layer

---

## Validation

The following technologies were successfully validated:

- ✅ OSPF Neighbor Adjacencies
- ✅ BGP Peer Establishment
- ✅ DMVPN Tunnel Registration
- ✅ NHRP Resolution
- ✅ HSRP Active / Standby Operation
- ✅ VRF-Lite Deployment
- ✅ EtherChannel Operation
- ✅ BFD Sessions

---

## Repository Structure


Enterprise-Multi-Site-Network-Infrastructure/
│
├── Configurations/
├── Documentation/
├── Screenshots/
├── Topology/
├── Videos/
├── LICENSE
└── README.md

---

## Future Enhancements

Future versions of this project may include:

- Cisco SD-WAN
- IPv6
- MPLS L3VPN
- Network Automation with Python & Ansible
- Model-Driven Telemetry

---

## Author

**Gabriel Tobi Idowu**

Enterprise Network Engineering Portfolio
