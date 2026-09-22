# Hybrid Networking

- **AWS Transit Gateway (TGW)** — regional hub for connecting VPCs, VPNs, and Direct Connect; supports routing domains (Route Tables) for traffic segmentation (Association/Propagation).
- **AWS Site-to-Site VPN** — Establishes encrypted IPsec tunnels between your on-premises network and AWS.
    - **Components:** Customer Gateway (CGW), VGW (single VPC), TGW (multi-VPC hub).
    - **High Availability:** Always provisions two tunnels.
- **AWS Client VPN** — Managed, client-based remote-access VPN service.
- **AWS Direct Connect (DX)** — dedicated private network link; requires VIFs (Private, Public, Transit).
- **AWS Global Accelerator** — Anycast-based network acceleration for TCP/UDP traffic.

## Diagrams

### TGW Segmentation
```text
       [VPC-Prod]    [VPC-Dev]
           |             |
       [Att-Prod]    [Att-Dev]
           |             |
    +------v-------------v--------+
    |      Transit Gateway        |
    |                             |
    | [RTB-Prod]    [RTB-Dev]     |
    |  (No route     (No route    |
    |   to Dev)       to Prod)    |
    +-----------------------------+
```

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
![Site-to-Site VPN architecture — On-premises Customer Gateway connected via two tunnels over the Internet to an AWS Transit Gateway.](../assets/site-to-site-vpn.png)

### Virtual Interface (VIF) Architecture
![Direct Connect Virtual Interface (VIF) architecture — showing Private VIF (to VGW/DXGW), Public VIF (to Public AWS Services), and Transit VIF (to TGW via DXGW).](../assets/vif-architecture.png)
