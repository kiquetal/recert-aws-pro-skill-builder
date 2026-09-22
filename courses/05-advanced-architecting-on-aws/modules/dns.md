# Route 53 & DNS

- **Routing Policies:** Simple, Weighted, Latency, Geolocation, Failover, Multivalue Answer.
- **Health Checks & Traffic Flow:** Monitor health, automated failover, and visual routing chaining.
- **Route 53 Resolver (Hybrid DNS):** Bridges DNS resolution across hybrid environments via endpoints.
    - **Inbound Endpoints:** Allow on-premises DNS to forward to AWS.
    - **Outbound Endpoints + Rules:** Allow AWS to forward to on-premises DNS.
- **Private Hosted Zones (PHZ):** VPC-specific DNS. Requires manual VPC ID association.

## Diagrams

### DNS Flow: Hybrid
```text
       [ VPC Instance ]
              | Query (db.corp.local)
              v
       [ Route 53 Resolver ]
              | Rule: "corp.local" -> Forward
              v
       [ Outbound Endpoint (ENI) ]
              |
      (Private Link: VPN/DX)
              |
       [ On-Prem DNS Server ]
              | Resolve (db.corp.local)
              v
       [ Result returned to VPC ]
```

![AWS to On-Premises DNS Flow](./assets/outbound-dns-flow.png)
![On-Premises to AWS PHZ DNS Flow](./assets/onprem-to-aws-dns.png)
![Route 53 Health Check](./assets/route53-health-check.png)
![Route 53 Resolver Configuration](./assets/route53-resolver-dns.png)
![Private Hosted Zone Hybrid DNS Architecture](./assets/phz-hybrid-dns.png)
![PHZ Association Logic](./assets/phz-association-logic.png)

## Implementation Matrix

| Scenario | Objective | AWS Component | On-Premises Config |
| :--- | :--- | :--- | :--- |
| **AWS → On-Prem** | VPC instance resolves `corp.local` | **Outbound Endpoint** + **Resolver Rule** (Forward) | None (Server listens on specified IP) |
| **On-Prem → AWS** | On-Prem server resolves `internal.aws` | **Inbound Endpoint** | **Conditional Forwarder** (points to Inbound IP) |
| **VPC → VPC** | VPC A resolves PHZ record in VPC B | **PHZ VPC Association** | N/A |
