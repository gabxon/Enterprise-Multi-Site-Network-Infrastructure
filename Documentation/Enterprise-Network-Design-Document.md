# Enterprise Multi-Site Network Infrastructure

## Network Design Document

---

**Project Name:** Enterprise Multi-Site Network Infrastructure

**Project Author:** Gabriel Tobi Idowu

**Version:** 1.0

**Date:** July 2026

---

## Project Overview

This document presents the design, implementation, and validation of a production-inspired enterprise network developed within an EVE-NG simulation environment.

The project simulates the network infrastructure of a fictional Tier-1 financial enterprise operating across multiple geographic locations, including a headquarters, dual WAN edge, dual DMVPN hubs, and four international branch offices.

The primary objective was to design a scalable, resilient, and highly available network using enterprise networking technologies commonly deployed in modern organizations.

The implementation emphasizes redundancy, dynamic routing, secure remote management, and resilient WAN connectivity while following enterprise networking best practices.

---

# Table of Contents

1. Executive Summary
2. Business Requirements
3. Project Objectives
4. Enterprise Network Overview
5. Network Architecture
6. Physical Topology
7. Logical Topology
8. Core Network Design
9. Distribution Layer Design
10. Edge Network Design
11. Branch Network Design
12. WAN Design
13. DMVPN Phase 3 Design
14. OSPF Design
15. BGP Design
16. VRF-Lite Design
17. High Availability Design
18. Security Design
19. IP Addressing Strategy
20. Validation Results
21. Future Enhancements
22. Conclusion

---

# 1. Executive Summary

This project demonstrates the design and implementation of a resilient enterprise network for a fictional Tier-1 financial organization.

The network interconnects a headquarters, core infrastructure, dual WAN edge routers, dual DMVPN hub routers, and four branch offices located in London, Dublin, Amsterdam, and Frankfurt.

The infrastructure was designed with the following objectives:

- High availability
- Redundant WAN connectivity
- Fast routing convergence
- Dynamic routing
- Secure remote management
- Scalability
- Fault tolerance

To achieve these objectives, several enterprise networking technologies were implemented, including:

- Multi-Area OSPF
- eBGP
- iBGP
- MP-BGP
- DMVPN Phase 3
- NHRP
- VRF-Lite
- HSRP
- EtherChannel (LACP)
- BFD
- SSH

The completed implementation demonstrates enterprise design principles while providing resilient connectivity between all network locations.

---

# 2. Business Requirements

The fictional organization requires a network infrastructure capable of supporting business-critical financial services across multiple locations.

The solution must satisfy the following requirements:

- Continuous connectivity between headquarters and branch offices
- Redundant WAN connectivity
- High network availability
- Dynamic routing with rapid convergence
- Secure administrative access
- Scalable architecture for future branch expansion
- Logical separation of network traffic
- Simplified network administration
- Resilient failover during WAN outages

---

# 3. Project Objectives

The objectives of this implementation are to:

- Design an enterprise-grade network architecture.
- Provide redundant WAN connectivity.
- Implement scalable dynamic routing.
- Deliver high availability throughout the network.
- Deploy secure device management.
- Simulate a production-inspired enterprise environment.
- Validate network functionality through operational testing.
- Produce professional implementation documentation suitable for engineering reference and portfolio presentation.

---

# 4. Enterprise Network Overview

## Overview

The Enterprise Multi-Site Network Infrastructure was designed to simulate the network of a multinational financial organization operating from a centralized headquarters with multiple geographically distributed branch offices.

The architecture emphasizes resiliency, scalability, high availability, and efficient routing while following a hierarchical enterprise network design model.

The simulated enterprise consists of:

- Dual WAN Edge Routers
- Dual Core Routers
- Dual Distribution Switches
- Dual DMVPN Hub Routers
- Four Branch Routers
- Multiple Access Networks
- Simulated ISP Connectivity

Branch offices are located in:

- London
- Dublin
- Amsterdam
- Frankfurt

Each branch is connected to both DMVPN hub routers using redundant WAN links, ensuring continuous connectivity in the event of a single WAN failure.

The network was developed entirely within an EVE-NG simulation environment using Cisco IOS devices.

---

# 5. Network Architecture

## Hierarchical Design

The network follows the Cisco Hierarchical Enterprise Campus Model.

The architecture is divided into distinct functional layers:

### Core Layer

The Core Layer provides high-speed transport between the distribution layer and WAN edge while maintaining minimal processing and low latency.

Responsibilities include:

- High-speed packet forwarding
- Layer-3 backbone connectivity
- OSPF backbone participation
- Redundant connectivity
- Fast convergence

Core Devices:

- CORE-1
- CORE-2

---

### Distribution Layer

The Distribution Layer provides policy enforcement and Layer-3 gateway services for enterprise VLANs.

Responsibilities include:

- Inter-VLAN Routing
- HSRP Default Gateway Redundancy
- VRF-Lite
- EtherChannel
- Route summarization
- Traffic aggregation

Distribution Devices:

- DIST-1
- DIST-2

---

### WAN Edge

The WAN Edge provides connectivity between the enterprise network and external autonomous systems.

Responsibilities include:

- eBGP
- iBGP
- MP-BGP
- BFD
- WAN route advertisement
- Internet edge connectivity

Edge Devices:

- EDGE-1
- EDGE-2

---

### DMVPN Hub Layer

The WAN core uses Dynamic Multipoint VPN (DMVPN) to provide scalable and resilient branch connectivity.

Responsibilities include:

- DMVPN Phase 3
- NHRP
- Dynamic tunnel establishment
- OSPF over GRE
- Redundant hub connectivity

Hub Devices:

- HUB-1
- HUB-2

---

### Branch Layer

Each branch office provides local LAN connectivity while participating in the enterprise WAN.

Each branch contains:

- Branch Router
- Branch LAN
- Redundant WAN links
- DMVPN Tunnel
- OSPF Routing

Branch Routers:

- BR-LONDON
- BR-DUBLIN
- BR-AMSTERDAM
- BR-FRANKFURT

---

# 6. Physical Topology

The physical topology consists of twelve Cisco IOS devices interconnected using point-to-point Ethernet links to simulate an enterprise WAN.

The design includes:

- Two Core Routers
- Two Distribution Switches
- Two WAN Edge Routers
- Two DMVPN Hub Routers
- Four Branch Routers

The branch offices are geographically separated but interconnected through the DMVPN overlay network.

The physical design provides redundant connectivity between the branch offices and the enterprise WAN, allowing traffic to continue flowing during individual link failures.

The topology was implemented within EVE-NG and validated using routing, failover, and redundancy testing.

> **Figure 1:** Enterprise Multi-Site Network Topology


![Enterprise Network Topology](../Topology/topology.png)


---

# 7. Logical Topology

## Overview

The logical topology illustrates how routing domains, overlay networks, and enterprise services communicate independently of the underlying physical connections.

The enterprise network is logically divided into the following functional domains:

- Core Routing Infrastructure
- Distribution Layer
- WAN Edge
- DMVPN Overlay Network
- Branch Office Networks
- Local Area Networks (LANs)

OSPF provides internal dynamic routing throughout the enterprise, while BGP is implemented at the WAN edge to simulate communication with external autonomous systems. DMVPN Phase 3 provides the overlay network used for secure and scalable branch connectivity.

The logical separation of these functions improves scalability, simplifies troubleshooting, and supports future expansion.

---

# 8. Core Network Design

## Design Overview

The Core Layer forms the backbone of the enterprise infrastructure.

Its primary purpose is to provide high-speed Layer 3 transport between the distribution layer and the WAN edge while minimizing latency and avoiding unnecessary policy enforcement.

The core was designed using two routers to eliminate a single point of failure and provide resilient connectivity.

### Core Devices

- CORE-1
- CORE-2

### Core Layer Responsibilities

- High-speed Layer 3 forwarding
- OSPF backbone connectivity
- Redundant routing paths
- Traffic transport between network layers
- Fast convergence

### Design Considerations

The Core Layer was intentionally kept simple.

No filtering, NAT, or policy enforcement was configured at this layer. Instead, the focus was on reliability, redundancy, and rapid packet forwarding.

This approach aligns with Cisco's hierarchical network design principles, where the Core Layer is optimized for speed and availability.

---

# 9. Distribution Layer Design

## Design Overview

The Distribution Layer acts as the boundary between the Core Layer and the enterprise access networks.

It aggregates VLANs, performs Layer 3 routing, provides default gateway redundancy, and applies routing policies before forwarding traffic toward the Core.

### Distribution Devices

- DIST-1
- DIST-2

### Technologies Implemented

- Inter-VLAN Routing
- HSRP
- EtherChannel (LACP)
- VRF-Lite

### Design Objectives

The Distribution Layer was designed to:

- Aggregate access layer traffic
- Provide resilient default gateway services
- Support multiple VLANs
- Improve bandwidth through EtherChannel
- Separate traffic using VRF-Lite

HSRP ensures uninterrupted default gateway availability by allowing one distribution switch to assume gateway responsibilities if the other becomes unavailable.

EtherChannel combines multiple physical links into a single logical connection, increasing both bandwidth and resilience.

VRF-Lite enables logical separation of routing tables while sharing the same physical infrastructure.

---

# 10. Edge Network Design

## Design Overview

The Edge Layer provides connectivity between the enterprise network and external autonomous systems.

It is responsible for exchanging routing information with upstream providers while maintaining resilient WAN connectivity.

### Edge Devices

- EDGE-1
- EDGE-2

### Technologies Implemented

- eBGP
- iBGP
- MP-BGP
- BFD

### Design Objectives

The Edge Layer was designed to:

- Advertise enterprise routes
- Learn external routes
- Provide redundant WAN connectivity
- Improve routing convergence
- Support scalable route exchange

Border Gateway Protocol (BGP) was selected because it is the standard routing protocol for exchanging routes between autonomous systems.

Bidirectional Forwarding Detection (BFD) was implemented to accelerate failure detection, enabling routing protocols to react more quickly to link failures.

---

# 11. Branch Network Design

## Design Overview

Four branch offices were deployed to simulate geographically distributed enterprise locations.

Each branch operates as an independent LAN while remaining fully integrated into the enterprise WAN through the DMVPN overlay network.

### Branch Locations

- London
- Dublin
- Amsterdam
- Frankfurt

Each branch includes:

- One Cisco IOS router
- Local LAN segment
- Redundant WAN connections
- DMVPN tunnel interface
- Dynamic routing using OSPF

### Design Objectives

The branch architecture was designed to:

- Provide resilient WAN connectivity
- Enable centralized communication
- Minimize downtime during WAN failures
- Support scalable branch expansion
- Simplify routing through dynamic protocols

Each branch maintains connectivity to both DMVPN hub routers, ensuring that traffic can continue to flow if a single WAN path becomes unavailable.

Floating static routes provide an additional layer of resiliency by offering automatic backup paths when the preferred route becomes unavailable.

---

# 12. WAN Design

## Overview

The Wide Area Network (WAN) provides connectivity between the enterprise headquarters and all branch offices.

The WAN was designed with redundancy as a primary objective. Each branch router maintains two independent WAN connections, one to each DMVPN hub router, ensuring continuous communication if a single WAN path fails.

The WAN architecture consists of:

- Dual WAN Edge Routers
- Dual DMVPN Hub Routers
- Four Branch Routers
- Point-to-Point WAN Links
- DMVPN Overlay Network

### WAN Design Objectives

The WAN infrastructure was designed to achieve the following goals:

- High availability
- Redundant branch connectivity
- Scalable branch deployment
- Fast convergence
- Simplified routing
- Reduced operational complexity

Redundant point-to-point links provide physical resilience, while DMVPN creates a logical overlay network that simplifies communication between geographically distributed locations.

---

# 13. DMVPN Phase 3 Design

## Overview

Dynamic Multipoint Virtual Private Network (DMVPN) Phase 3 was selected to provide scalable and resilient communication between the enterprise headquarters and remote branch offices.

Unlike traditional GRE tunnels that require a separate tunnel for every remote site, DMVPN allows multiple branch routers to communicate dynamically through a shared tunnel interface.

### DMVPN Components

The deployment consists of:

- Two DMVPN Hub Routers
  - HUB-1
  - HUB-2

- Four DMVPN Spoke Routers
  - BR-LONDON
  - BR-DUBLIN
  - BR-AMSTERDAM
  - BR-FRANKFURT

### Technologies Used

- GRE Multipoint Tunnels
- NHRP (Next Hop Resolution Protocol)
- OSPF over GRE
- Dual Hub Redundancy

### Design Benefits

Implementing DMVPN Phase 3 provides several advantages:

- Reduced tunnel configuration
- Simplified branch deployment
- Dynamic tunnel establishment
- Scalable overlay architecture
- Resilient branch connectivity
- Efficient routing between locations

Each spoke maintains connectivity to both DMVPN hubs, providing redundancy in the event that one hub becomes unavailable.

---

# 14. OSPF Design

## Overview

Open Shortest Path First (OSPF) was selected as the enterprise Interior Gateway Protocol (IGP).

OSPF dynamically exchanges routes between routers, allowing the enterprise network to adapt automatically to topology changes without requiring manual route updates.

### OSPF Areas

The implementation uses multiple OSPF areas to improve scalability.

Area 0 functions as the backbone area.

Additional areas are used to connect WAN links and branch networks.

### OSPF Responsibilities

Within this implementation, OSPF is responsible for:

- Internal route exchange
- Dynamic path selection
- Automatic convergence
- Redundant route calculation
- Branch reachability

### Design Benefits

Using OSPF provides:

- Fast convergence
- Hierarchical routing
- Reduced administrative effort
- Scalable enterprise routing
- Efficient use of bandwidth

The DMVPN tunnel interfaces participate in OSPF, allowing branch routes to be exchanged dynamically across the WAN overlay.

---

# 15. BGP Design

## Overview

Border Gateway Protocol (BGP) was implemented at the WAN Edge to simulate communication between the enterprise autonomous system and external service providers.

The design includes both External BGP (eBGP) and Internal BGP (iBGP).

### eBGP

External BGP exchanges routing information between the enterprise network and simulated Internet Service Providers.

Responsibilities include:

- External route advertisement
- External route learning
- WAN connectivity
- Autonomous System communication

### iBGP

Internal BGP exchanges routes between the enterprise edge routers.

Responsibilities include:

- Internal route propagation
- Route consistency
- Redundant WAN routing

### MP-BGP

Multiprotocol BGP was implemented to support route exchange across multiple routing contexts.

### BFD Integration

Bidirectional Forwarding Detection (BFD) was integrated with BGP to accelerate failure detection.

Instead of waiting for standard BGP timers to expire, BFD detects link failures within milliseconds, allowing routing to reconverge much more quickly.

### Design Benefits

The BGP implementation provides:

- Enterprise-grade WAN routing
- Scalable route advertisement
- Fast convergence through BFD
- Redundant external connectivity
- High availability

---

# 16. VRF-Lite Design

## Overview

Virtual Routing and Forwarding Lite (VRF-Lite) was implemented to provide logical separation of network traffic without requiring separate physical infrastructure.

VRF-Lite allows multiple independent routing tables to coexist on the same network devices, enabling traffic isolation while sharing the same switching and routing hardware.

### Design Objectives

The VRF-Lite implementation was designed to:

- Logically separate network traffic
- Improve network scalability
- Simplify future service expansion
- Reduce infrastructure costs
- Support enterprise segmentation

### Benefits

Implementing VRF-Lite provides the following advantages:

- Independent routing tables
- Traffic isolation
- Improved scalability
- Efficient use of network infrastructure
- Simplified service deployment

The use of VRF-Lite demonstrates enterprise segmentation techniques commonly used in large organizations to separate business services while maintaining a shared physical infrastructure.

---

# 17. High Availability Design

## Overview

High availability was a fundamental design objective throughout the enterprise network.

Redundancy was incorporated at multiple layers of the infrastructure to minimize service interruption and eliminate single points of failure.

The following technologies contribute to network resiliency:

- HSRP
- EtherChannel (LACP)
- Dual Core Routers
- Dual Edge Routers
- Dual DMVPN Hub Routers
- Floating Static Routes
- OSPF Dynamic Routing
- BFD Fast Failure Detection

Together, these technologies ensure continuous connectivity during device, interface, or WAN link failures.

---

## HSRP

Hot Standby Router Protocol (HSRP) provides default gateway redundancy at the Distribution Layer.

Two distribution devices share a virtual gateway address.

One device operates as the Active gateway while the second remains in the Standby state.

If the Active device becomes unavailable, the Standby device automatically assumes responsibility for the virtual gateway, minimizing disruption to end-user traffic.

### Benefits

- Default gateway redundancy
- Automatic failover
- Minimal downtime
- Improved network availability

---

## EtherChannel (LACP)

EtherChannel combines multiple physical interfaces into a single logical link using the Link Aggregation Control Protocol (LACP).

### Design Benefits

- Increased bandwidth
- Link redundancy
- Load balancing
- Simplified management

If a single physical member link fails, traffic continues to flow across the remaining links without interrupting communication.

---

## Floating Static Routes

Floating static routes were implemented on branch routers to provide backup connectivity.

Each branch maintains a preferred static route and a secondary floating static route with a higher administrative distance.

If the preferred path becomes unavailable, the floating route is automatically installed into the routing table, maintaining WAN connectivity.

### Benefits

- Automatic backup routing
- WAN resiliency
- Reduced downtime
- Simple failover mechanism

---

# 18. BFD Design

## Overview

Bidirectional Forwarding Detection (BFD) provides rapid failure detection between neighboring routers.

Rather than relying solely on routing protocol timers, BFD continuously monitors forwarding paths and immediately detects failures.

### Design Objectives

- Accelerate failure detection
- Improve routing convergence
- Increase network availability
- Reduce service interruption

### Integration

Within this project, BFD is integrated with BGP at the WAN Edge.

When a link failure occurs, BFD quickly notifies BGP, allowing routing information to be updated significantly faster than with default BGP timers.

### Benefits

- Fast convergence
- Improved resiliency
- Reduced downtime
- Enhanced WAN reliability

---

# 19. Security Design

## Overview

Although this project focuses primarily on routing and high availability, several security best practices were incorporated into the implementation.

### Implemented Security Measures

- SSH Version 2 for secure remote management
- Local user authentication
- Encrypted enable secret
- Encrypted local user passwords
- Message of the Day (MOTD) warning banner
- Disabled HTTP server
- Disabled HTTPS server
- Disabled DNS lookup to prevent command delays
- Administrative console timeout

### Design Considerations

The security implementation provides a baseline level of device hardening suitable for a production-inspired enterprise environment.

Additional security technologies such as AAA, TACACS+, RADIUS, ACLs, Zone-Based Firewall, Control Plane Policing (CoPP), and PKI-based authentication could be incorporated in future versions of the project.

---

# 20. IP Addressing Strategy

## Overview

A structured IP addressing scheme was implemented throughout the enterprise network to ensure consistency, simplify troubleshooting, and support future expansion.

Private IPv4 addressing (RFC 1918) was used for all internal networks.

The addressing plan separates infrastructure links, WAN links, tunnel interfaces, and branch LANs into distinct subnets to improve organization and operational clarity.

## Addressing Principles

The following design principles were adopted:

- Consistent subnet allocation
- Dedicated addressing for point-to-point links
- Separate addressing for branch LANs
- Dedicated DMVPN tunnel network
- Unique loopback addresses for router identification
- Efficient use of IPv4 address space

## Branch LAN Networks

| Branch | LAN Network |
|---------|-------------|
| London | 192.168.10.0/24 |
| Dublin | 192.168.20.0/24 |
| Amsterdam | 192.168.30.0/24 |
| Frankfurt | 192.168.40.0/24 |

## WAN Infrastructure

Point-to-point WAN links use /30 subnets to conserve address space while providing dedicated connectivity between enterprise devices.

The DMVPN overlay network uses the 172.16.0.0/24 network, with each hub and spoke assigned a unique tunnel IP address.

A complete interface-by-interface addressing table is provided in the accompanying **IP Addressing Plan** document.

---

# 21. Validation Results

## Overview

Following implementation, the enterprise network underwent functional validation to verify routing, redundancy, high availability, and end-to-end connectivity.

Testing confirmed that the implemented technologies operated as expected within the simulated environment.

## Validation Areas

The following features were successfully validated:

### OSPF

Validation included:

- Neighbor establishment
- Route propagation
- Multi-area operation
- Dynamic convergence

**Evidence:**

- `show ip ospf neighbor`
- `show ip route ospf`

---

### BGP

Validation included:

- eBGP neighbor establishment
- iBGP route exchange
- MP-BGP operation
- Route advertisement

**Evidence:**

- `show ip bgp summary`
- `show ip bgp`

---

### DMVPN

Validation confirmed:

- Tunnel establishment
- NHRP registration
- Hub-and-spoke communication
- Overlay connectivity

**Evidence:**

- `show dmvpn`
- `show ip nhrp`

---

### HSRP

Validation confirmed:

- Active/Standby operation
- Virtual gateway functionality
- Automatic failover

**Evidence:**

- `show standby brief`

---

### EtherChannel

Validation confirmed:

- Successful LACP negotiation
- Logical Port-Channel formation
- Link redundancy

**Evidence:**

- `show etherchannel summary`

---

### VRF-Lite

Validation confirmed:

- VRF creation
- Route separation
- Independent routing tables

**Evidence:**

- `show vrf`
- `show ip route vrf`

---

### BFD

Validation confirmed:

- Neighbor establishment
- Rapid failure detection
- Integration with BGP

**Evidence:**

- `show bfd neighbors`

---

### End-to-End Connectivity

End-to-end connectivity testing verified successful communication between:

- Headquarters
- Distribution Layer
- Core Layer
- WAN Edge
- DMVPN Hubs
- London Branch
- Dublin Branch
- Amsterdam Branch
- Frankfurt Branch

Ping and traceroute testing confirmed complete connectivity across the enterprise network.

---

# 22. Future Enhancements

Although the current implementation demonstrates a resilient enterprise architecture, several enhancements could be incorporated in future iterations.

Potential improvements include:

- Cisco AAA using TACACS+
- RADIUS authentication
- Dynamic Host Configuration Protocol (DHCP)
- Network Time Protocol (NTP)
- Syslog Server
- SNMP Monitoring
- NetFlow
- IP SLA
- Policy-Based Routing (PBR)
- Quality of Service (QoS)
- NAT and Internet Edge Services
- Cisco Zone-Based Firewall
- IPv6 deployment
- MPLS WAN integration
- SD-WAN implementation
- Infrastructure automation using Python or Ansible

These enhancements would further increase scalability, automation, visibility, and operational efficiency.

---

# 23. Conclusion

This project demonstrates the successful design and implementation of a production-inspired enterprise network using Cisco enterprise technologies within an EVE-NG simulation environment.

The completed solution provides resilient connectivity between headquarters and four geographically distributed branch offices through a redundant WAN architecture.

Key technologies implemented include:

- Multi-Area OSPF
- eBGP
- iBGP
- MP-BGP
- DMVPN Phase 3
- NHRP
- VRF-Lite
- HSRP
- EtherChannel (LACP)
- BFD
- SSH

The network was designed with scalability, redundancy, high availability, and operational simplicity as primary objectives.

Validation testing confirmed successful implementation of dynamic routing, resilient WAN connectivity, gateway redundancy, and enterprise routing functionality.

This project serves as a practical demonstration of enterprise network engineering principles and reflects the design considerations commonly encountered in modern production environments.
- 
