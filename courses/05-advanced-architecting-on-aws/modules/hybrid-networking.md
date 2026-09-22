# Hybrid Networking

- **AWS Transit Gateway (TGW)** — regional hub for connecting VPCs, VPNs, and Direct Connect; supports routing domains (Route Tables) for traffic segmentation (Association/Propagation).
- **AWS Site-to-Site VPN** — Establishes encrypted IPsec tunnels between your on-premises network and AWS.
    - **Components:**
        - **Customer Gateway (CGW):** The on-premises device/firewall (the VPN endpoint on your side).
        - **AWS Termination Points (Managed Service):**
            - **Virtual Private Gateway (VGW):** The *standard* AWS-side VPN endpoint for connecting to a **single VPC**.
            - **Transit Gateway (TGW):** An *optional, advanced* hub for connecting **multiple VPCs** and on-premises networks.
    - **High Availability:** Always provisions two tunnels; both must be configured on your CGW.
    - **Routing:** Supports Static or Dynamic (BGP) routing.
    - **NAT Traversal (NAT-T):** Essential if the CGW is behind a NAT device; encapsulates ESP in UDP/4500.

- **AWS Client VPN** — A managed, client-based remote-access VPN service.
    - **Use Case:** Individual remote access for employees/contractors to access private VPC resources.
    - **Components:** ENI association, Security Groups, Authorization Rules, Route Table.

![AWS Client VPN route table — showing the routing configuration for the Client VPN endpoint to reach VPC resources.](../assets/client-vpn-route-table.png)
![AWS Client VPN association — showing the Client VPN endpoint associated with target subnets in a VPC and governed by security groups.](../assets/client-vpn-association.png)

- **AWS Direct Connect (DX)** — A dedicated private network link from on-premises to AWS.
    - **Logical Endpoints (Virtual Interfaces - VIFs):** Private (VGW/DXGW), Public (AWS services), Transit (TGW).
    - **Direct Connect Gateway (DXGW):** Global construct for multi-region connectivity.
    - **Invalid Termination Points:** Do not terminate on EC2, ALB/NLB, IGW, or NAT Gateway.

## Diagrams

### TGW Logical Components
![Transit Gateway Logic — illustrating the separation between Attachments (pipes), Associations (mapping traffic to a route table), and Propagations (dynamic route population).](../assets/tgw-logic.png)

### Managed Service Failover (VGW)
```text
    [On-Premises Network]
              |
     +--------+--------+
     |  Dual IPsec     |
     |   Tunnels       |
     +--------+--------+
              |
    +---------v---------+
    |   AWS VGW/TGW     |
    +---------+---------+
              |
      [VPC Route Table]
```

### Site-to-Site VPN Architecture
![Site-to-Site VPN architecture — On-premises Customer Gateway connected via two tunnels over the Internet to an AWS Virtual Private Gateway.](../assets/site-to-site-vpn.png)

### Virtual Interface (VIF) Architecture
![Direct Connect Virtual Interface (VIF) architecture — showing Private VIF (to VGW/DXGW), Public VIF (to Public AWS Services), and Transit VIF (to TGW via DXGW).](../assets/vif-architecture.png)

- **AWS Global Accelerator** — Anycast-based network acceleration for TCP/UDP traffic.
![AWS Global Accelerator — showing the flow of user traffic to the nearest AWS edge location via Anycast IP addresses, then over the AWS global network to regional endpoints.](../assets/global-accelerator.png)
