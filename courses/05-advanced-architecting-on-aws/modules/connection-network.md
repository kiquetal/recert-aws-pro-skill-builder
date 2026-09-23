# VPC Design & New Capabilities

- **VPC Design Fundamentals:**
    - Subnets, Route Tables, Internet Gateways (IGW), NAT Gateways.
    - Security Groups (stateful) vs Network ACLs (stateless).

- **Advanced VPC Capabilities:**
    - **Gateway Load Balancer (GWLB):** Deploys, scales, and manages virtual appliances (firewalls, IDS/IPS).
        - **Core Technology:** Powered by **AWS Hyperplane**, which enables the service to scale across multiple availability zones and maintain high throughput.
        - **Capabilities:** Combines a transparent network **Layer 3 Gateway** (which routes traffic) with **Layer 4 Load Balancing** (which distributes traffic across appliances).
        - **Gateway Load Balancer Endpoint (GWLBE):** Traffic is routed to the virtual appliances via a GWLBE (a VPC endpoint specifically for GWLB).
        - **Protocol:** Uses the **GENEVE** protocol (port 6081) to encapsulate traffic between the GWLB and the virtual appliance. This allows metadata to be passed with the packets to the appliance.
        - **Use Case:** Transparently inspect and filter traffic flowing into/out of your VPC, or between VPCs.

    - **AWS Network Firewall:** A managed service for deploying essential network protections for all your VPCs.
        - **Stateful Rules:** 
            - Inspects packets in the context of traffic flow. 
            - Filters traffic based on 5-tuple (source/destination IP, port, protocol) **and** domain lists (e.g., allow/deny access to `*.example.com`).
            - *Use Case:* Advanced filtering, domain-level filtering, and intrusion prevention (IPS).
        - **Stateless Rules:**
            - Inspects each packet in isolation, without context of the connection flow.
            - Filters traffic strictly based on the 5-tuple (IP, Port, Protocol).
            - *Use Case:* High-speed, simple packet filtering (e.g., dropping all traffic from a known malicious IP).
        - **Architecture (Centralized Inspection):**
        - For production, use the **Inspection VPC** pattern.
        - All traffic from VPCs is routed to the **Transit Gateway**, which redirects it to the **Inspection VPC**.
        - Inside the Inspection VPC, a **Gateway Load Balancer** distributes the traffic to the **Network Firewall** nodes for inspection before forwarding it to its final destination.
    - **Pro Tip (Asymmetric Routing):** When designing this, you **must** ensure traffic symmetry. If the request goes through the firewall, the response must also go through the firewall; otherwise, the connection will be dropped (as the firewall will detect a state mismatch).

```text
       [Internet]
            |
    [VPC: Inspection] 
    (1) Firewall Endpoint <--- [Gateway Load Balancer]
            |
    [Transit Gateway] (The routing hub)
            |
    +-------+-------+
    |               |
[VPC: App1]   [VPC: App2]
```

    - **VPC Lattice:** Simplifies service-to-service communication with built-in service discovery, connectivity, and security (mTLS) across VPCs and accounts without TGW or Peering.
    - **IP Address Management (IPAM):** Automates the discovery, planning, and monitoring of IP address space across your AWS organization.

- **AWS Transit Gateway (TGW)** — regional hub for connecting VPCs, VPNs, and Direct Connect; supports routing domains (Route Tables) for traffic segmentation (Association/Propagation).
    - **TGW Attachments (What can it connect to?):**
        - **VPC Attachments:** Connects VPCs to the TGW.
        - **VPN Attachments:** Connects Site-to-Site VPNs to the TGW.
        - **Direct Connect Gateway Attachments:** Connects Direct Connect to the TGW via a Direct Connect Gateway.
        - **Transit Gateway Peering Attachments:** Connects two separate TGWs (intra-region or inter-region).
        - **Connect Attachments (SD-WAN):** Uses GRE tunnels to connect SD-WAN appliances directly to the TGW.
    - **Logical Components:** Attachments (pipes), Associations (mapping traffic to a route table), and Propagations (dynamic route population).

![VPC Design and Networking — showing key components like IPAM, VPC Endpoints, and connectivity architecture.](../assets/vpc-design-network.png)


# AWS PrivateLink

- **Interface Endpoints:** Secure, private connectivity to AWS services and SaaS applications powered by PrivateLink.
    - **Mechanism:** Powered by **Elastic Network Interfaces (ENIs)**.
    - **Routing:** No route table entry is required because the traffic is routed directly to the ENI's private IP address, behaving like any other resource in the VPC.
    - **Security:** Managed via **Security Groups** attached to the ENI. Traffic is restricted by the attached Security Group (inbound access from the subnet) and the VPC Endpoint Policy.
    - **Use Case:** Accessing services across VPC/Account boundaries (via Interface Endpoints) without traversing the internet.

![AWS PrivateLink Diagram — showing the ENI-based architecture and routing mechanism for Interface Endpoints.](../assets/privatelink.png)
