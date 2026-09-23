# VPC Design & New Capabilities

- **VPC Design Fundamentals:**
    - Subnets, Route Tables, Internet Gateways (IGW), NAT Gateways.
    - Security Groups (stateful) vs Network ACLs (stateless).

- **Advanced VPC Capabilities:**
    - **Gateway Load Balancer (GWLB):** Deploys, scales, and manages virtual appliances (firewalls, IDS/IPS).
    - **VPC Lattice:** Simplifies service-to-service communication with built-in service discovery, connectivity, and security (mTLS) across VPCs and accounts without TGW or Peering.
    - **VPC Endpoints (PrivateLink):** Secure, private connectivity to AWS services and SaaS applications powered by PrivateLink.
        - **Interface Endpoints (PrivateLink):** Powered by **Elastic Network Interfaces (ENIs)**. 
            - *Routing:* No route table entry is required because the traffic is routed directly to the ENI's private IP address like any other resource in the VPC.
            - *Security:* Managed via **Security Groups** attached to the ENI.
        - **Gateway Endpoints:** Powered by **Route Tables**.
            - *Routing:* Requires an explicit route table entry (via a prefix list) to direct traffic to the Gateway.
            - *Scope:* Only supported for Amazon S3 and Amazon DynamoDB.
    - **IP Address Management (IPAM):** Automates the discovery, planning, and monitoring of IP address space across your AWS organization.

![VPC Design and Networking — showing key components like IPAM, VPC Endpoints, and connectivity architecture.](../assets/vpc-design-network.png)


# AWS PrivateLink

- **Interface Endpoints:** Secure, private connectivity to AWS services and SaaS applications powered by PrivateLink.
    - **Mechanism:** Powered by **Elastic Network Interfaces (ENIs)**.
    - **Routing:** No route table entry is required because the traffic is routed directly to the ENI's private IP address, behaving like any other resource in the VPC.
    - **Security:** Managed via **Security Groups** attached to the ENI. Traffic is restricted by the attached Security Group (inbound access from the subnet) and the VPC Endpoint Policy.
    - **Use Case:** Accessing services across VPC/Account boundaries (via Interface Endpoints) without traversing the internet.

![AWS PrivateLink Diagram — showing the ENI-based architecture and routing mechanism for Interface Endpoints.](../assets/privatelink.png)
