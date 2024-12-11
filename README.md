# The National Retirer Corporate Offices

The National Retirer is the nation’s premier tabloid magazine for upper-middle-aged office workers. It provides an inside scoop into the latest and greatest scandals in office culture across the nation. It’s a real who’s who magazine for the corporate elite. The corporate offices of TNR consist of three buildings on a small campus.


## Executive Overview

We have developed a comprehensive network design proposal for the National Retirer Corporate Offices (TNR), tailored to support their operations across three interconnected buildings. The design addresses TNR’s critical need for a high-performance network capable of managing significant bandwidth demands, particularly for intensive media activities like live video streaming, which are essential to their business as a leading tabloid magazine.

Key requirements include a scalable network for over 1,300 users, specialized provisions for the data center, VoIP phones, and isolated VLANs for printers and disk servers. A major challenge involves ensuring seamless connectivity and adequate bandwidth during peak usage, especially for live video streaming, while adhering to management's directive to limit this service at present.

Our solution employs a multi-layered topology featuring high-performance switches such as the FC-SW-48T-LA for user access and MOD-SW-6 chassis with redundant supervisors for robust network management and failover support. Advanced techniques like link aggregation and dedicated VLAN segmentation optimize traffic flow, enhance security, and mitigate congestion risks.

The design integrates a balanced combination of cost-efficient and high-end equipment to align with TNR's operational needs and budget constraints. By prioritizing modularity and scalability, the proposed solution not only addresses the company’s current demands but also ensures adaptability for future growth and technological advancements.


This document outlines the detailed proposal for designing a robust and scalable network infrastructure for the National Retirer Corporate Offices (TNR). The proposed network supports over 1,300 users across three interconnected buildings, addressing their unique requirements with high-performance equipment, advanced segmentation techniques, and cost-efficient solutions.

The proposal is structured as follows:

1. **Problem Analysis**: Understanding the requirements and challenges.
2. **Problem Solution**: The systematic approach, assumptions, and solutions for each objective.
3. **Solution Analysis**: Evaluating the design's completeness, appropriateness, and potential risks.
4. **Summary**: A concise recap of the design, including total cost estimates.

---

## Section 1 – Problem Analysis

### **Given Information**

The National Retirer Corporate Offices (TNR) comprises three buildings, each with unique network requirements:

1. **Building 1**: Houses reporters, photographers, editors, and cameramen with 400 users across two floors. Bandwidth demand averages 300 Mbps per user with a peak of 450 Mbps during live video streaming. Video streaming is prioritized at a limited level per management’s directive.

2. **Building 2**: Hosts the IT, HR, finance, legal departments, and a data center. Floors 2-4 accommodate 750 users with an average bandwidth of 320 Mbps and a peak of 450 Mbps. The data center on the first floor contains 25 file/database servers and 12 disk servers requiring isolated, high-bandwidth connectivity (80 Gbps per disk server for backups).

3. **Building 3**: Includes a lobby (10 users), conference rooms (16 rooms with 8 network drops each), and executive suites (56 offices requiring 1 Gbps connections).

Other key requirements include:

- **VoIP Phones**: All desks are equipped with VoIP phones using a dedicated VLAN.
- **Printers**: Printers are isolated on a VLAN, with a minimum of 1 per 25 users and a dedicated printer for each executive.
- **Wi-Fi Access Points**: Used exclusively as a guest network and must remain completely segregated.
- **Video Teleconferencing**: Conference rooms and executive offices require 1 Gbps peak bandwidth, isolated on a VLAN.
- **ISP Router/Firewall**: Supports 8x10 Gbps and 4x40 Gbps connections and performs NAT and inter-VLAN routing.

### **Problems to Solve**

1. **Bandwidth Management**: Ensure sufficient bandwidth for high-demand activities like live streaming and backups while preventing bottlenecks.
2. **Network Segmentation**: Implement VLANs for security and traffic isolation.
3. **Scalability and Redundancy**: Design a scalable network that ensures high availability and supports future growth.
4. **Cost Optimization**: Balance high performance with budget constraints.
5. **Device Interconnection**: Ensure appropriate connectivity between devices using UTP Cat6 and fiber optic cables.

### **Objectives**

1. Provide seamless connectivity for over 1,300 users.
2. Segregate traffic using VLANs for critical services like SAN, VoIP, printers, and guest Wi-Fi.
3. Use modular chassis and redundant supervisors for scalability and failover.
4. Adhere to the 500-device limit per broadcast domain.
5. Provide a detailed IP addressing scheme.

---

## Section 2 – Problem Solution

### **Building 1: Reporters and Content Creators**

Building 1 serves as the operational hub for reporters, photographers, editors, and cameramen. This building has two floors and hosts 400 users in total.

#### Objectives and Solutions:

1. **Bandwidth Management**:
   - Allocate sufficient bandwidth to handle peak demands during live video streaming (450 Mbps per user).
   - Install FC-SW-48T-LA switches, each with 48 x 1 Gbps ports and 4 x 10 Gbps fiber optic interfaces, to ensure high-performance connectivity.
   - Deploy Quality of Service (QoS) to prioritize video streaming while limiting non-critical bandwidth usage.
   - Calculate total bandwidth requirements: 
     - Floor 1: 300 Mbps x 200 users = 60 Gbps (average usage).
     - Floor 2: 300 Mbps x 200 users = 60 Gbps (average usage).

2. **Network Segmentation**:
   - Use VLANs to isolate traffic for different device types:
     - **User VLANs** for personal computers and workstations.
     - **VoIP VLANs** for telephones.
     - **Printer VLANs** to isolate print services.
     - **Wi-Fi VLANs** for guest networks.

3. **Scalability and Redundancy**:
   - Deploy nine FC-SW-48T-LA switches (48 ports each) to accommodate 432 connections (400 users + 16 printers + 16 Wi-Fi access points).
   - Use a MOD-SW-6 modular chassis with two redundant MOD-SW-SUP supervisor cards for centralized management and failover capabilities.

4. **Interconnection and Bandwidth Aggregation**:
   - Install three MOD-LC-8F-10G cards with 8-port 10 Gbps fiber interfaces for uplink aggregation.
   - Use a MOD-LC-4F-40G card with 4-port 40 Gbps fiber interfaces for backplane connectivity.
   - Aggregate switch outputs to the modular chassis for efficient bandwidth utilization and redundancy.

#### Diagram Placement:
**Figure 1**: Logical topology diagram for Building 1.

---

### **Building 2: IT, HR, Finance, Legal, and Data Center**

Building 2 is critical, housing 750 users and a data center. It spans four floors, with the data center on the first floor and offices above.

#### Objectives and Solutions:

1. **Bandwidth Management**:
   - Calculate bandwidth needs for users: 
     - Floors 2-4: 320 Mbps x 250 users per floor = 80 Gbps per floor (average usage).
   - Allocate 80 Gbps per disk server for backups, ensuring isolated bandwidth for the SAN VLAN.

2. **Network Segmentation**:
   - Create VLANs for specific use cases:
     - **SAN VLAN** for servers and storage.
     - **User VLANs** for each floor.
     - **VoIP VLAN** for telephony services.
     - **Wi-Fi VLAN** for guest networks.

3. **Scalability and Redundancy**:
   - Deploy FC-SW-48T-LA switches to support 750 connections, requiring 16 switches (750 users + 30 printers + 24 Wi-Fi access points = 804 connections).
   - Use a MOD-SW-8 chassis with two redundant MOD-SW-SUP supervisor cards for centralized control and high availability.

4. **Interconnection and Bandwidth Aggregation**:
   - Install four MOD-LC-8F-10G cards to aggregate uplinks.
   - Use two MOD-LC-4F-40G cards for high-speed backplane connectivity, supporting 640 Gbps total bandwidth.

#### Diagram Placement:
**Figure 2**: Logical topology diagram for Building 2.

---

### **Building 3: Lobby, Conference Rooms, and Executive Suites**

Building 3 focuses on user experience, hosting executives and guests. It includes a lobby, 16 conference rooms, and 56 executive offices.

#### Objectives and Solutions:

1. **Bandwidth Management**:
   - Allocate 1 Gbps per executive office and conference room for peak performance.
   - Calculate bandwidth requirements:
     - Lobby: 10 users x 300 Mbps = 3 Gbps (average usage).
     - Conference Rooms: 16 rooms x 1 Gbps = 16 Gbps (peak usage).
     - Executive Suites: 56 offices x 1 Gbps = 56 Gbps (peak usage).

2. **Network Segmentation**:
   - Use VLANs for traffic isolation:
     - **Executive VLAN** for office connections.
     - **Conference VLAN** for video conferencing.
     - **Wi-Fi VLAN** for guest access.

3. **Scalability and Redundancy**:
   - Deploy six FC-SW-48T-LA switches to support 144 connections (10 lobby users + 128 conference and executive users).
   - Use a MOD-SW-4 chassis with two redundant MOD-SW-SUP supervisor cards.

4. **Interconnection and Bandwidth Aggregation**:
   - Install two MOD-LC-8F-10G cards for uplink aggregation.
   - Use one MOD-LC-4F-40G card for high-speed backplane connectivity.

#### Diagram Placement:
**Figure 3**: Logical topology diagram for Building 3.

---

## Section 3 – Solution Analysis

The design meets all requirements by providing:

- Sufficient bandwidth through link aggregation and dedicated VLANs.
- Segmentation for security and efficiency.
- Scalability via modular chassis and redundant supervisors.

### Appropriateness

- The use of high-performance switches and fiber optic cables ensures reliability and future-proofing.
- VLANs and IP addressing comply with the 500-device broadcast domain limit.

### Potential Risks and Mitigations

1. Bandwidth Bottlenecks:
   - Mitigation: Oversubscription ratios and aggregated links.
2. Device Failures:
   - Mitigation: Redundant supervisors and failover configurations.

---

## Summary

The proposed network design for TNR supports over 1,300 users across three buildings, addressing their unique requirements with:

- High-performance switches and modular chassis for scalability.
- VLANs and IP addressing for traffic segmentation.
- Fiber and UTP cabling for optimal connectivity.

Total Estimated Cost: \$2,535,400, accounting for modularity and scalability adjustments.



