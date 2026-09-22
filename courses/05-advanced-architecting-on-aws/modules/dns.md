# Route 53 & DNS

- **AWS Route 53 Routing Policies:**
    - **Simple:** Standard DNS resolution; returns a single value.
    - **Weighted:** Distribute traffic across multiple resources (e.g., 80% to A, 20% to B).
    - **Latency:** Routes to the region with the lowest network latency.
    - **Geolocation:** Routes based on user's location (country, state, continent).
    - **Failover:** Active/Passive routing using health checks.
    - **Health Checks & Traffic Flow:** Monitor endpoint health and chain complex routing policies (e.g., Latency as primary, Failover as backup).

![Route 53 Health Check configuration](./assets/route53-health-check.png)

- **AWS Route 53 Resolver (Hybrid DNS):**
    - **Problem Solved:** Bridges siloed on-premises and AWS DNS environments.
    - **Inbound Endpoints:** Allow on-premises DNS to forward queries for an AWS domain (e.g., `*.internal.aws`) to AWS.
        - *Creation:* Provisioned via Route 53 Resolver console. Creates ENIs in selected subnets as "listeners."
        - *Security:* Requires Security Group allowing inbound UDP/TCP port 53 from on-premises DNS.
        - *Logic:* Listener IPs serve as target for Conditional Forwarders on-premises.
    - **Outbound Endpoints + Resolver Rules (Forwarding):** Allow AWS to resolve on-premises DNS domains (e.g., `corp.local`) via forwarding rules.
        - *Setup:* Create an **AWS Route 53 Resolver Rule** (type: **Forward**) for the target domain pointing to on-premises DNS server IPs.

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
![On-Premises to AWS Private Hosted Zone DNS Flow](./assets/onprem-to-aws-dns.png)

- **Private Hosted Zones (PHZ):** DNS domains configured *only* for specific VPCs. Not internet-resolvable.
    - **Cross-VPC DNS Resolution:** A single PHZ can be associated with multiple VPCs by explicitly adding the **VPC ID** in the Route 53 console.
    - **Split-Horizon DNS:** Use same domain name (e.g., `example.com`) for public internet and internal VPC queries.
    - **Prerequisites:**
        - `enableDnsSupport` = `true`
        - `enableDnsHostnames` = `true`
        - Network connectivity to Route 53 Resolver IP (`169.254.169.253`).

![PHZ Association Logic](./assets/phz-association-logic.png)

## Implementation Matrix

| Scenario | Objective | AWS Component | On-Premises Config |
| :--- | :--- | :--- | :--- |
| **AWS → On-Prem** | VPC instance resolves `corp.local` | **Outbound Endpoint** + **Resolver Rule** (Forward) | None (Server listens on specified IP) |
| **On-Prem → AWS** | On-Prem server resolves `internal.aws` | **Inbound Endpoint** | **Conditional Forwarder** (points to Inbound IP) |
| **VPC → VPC** | VPC A resolves PHZ record in VPC B | **PHZ VPC Association** | N/A |
