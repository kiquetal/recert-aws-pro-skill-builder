<!--
  PER-COURSE NOTES TEMPLATE
-->

# Advanced Architecting on AWS – Online Course Supplement

## Metadata

| Field           | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| Name            | Advanced Architecting on AWS – Online Course Supplement      |
| Type            | Course                                                       |
| Points          | 160 (≈2h)                                                    |
| Status          | In progress                                                  |
| Date completed  | —                                                            |
| Skill Builder   | https://skillbuilder.aws/learn/DCVNQSAWWN/advanced-architecting-on-aws-online-course-supplement/64TDHJKPZY |

## Modules

- [Governance & Organization](modules/governance.md)
- [Hybrid Networking](modules/hybrid-networking.md)
- [Route 53 & DNS](modules/dns.md)
- [Specialized Infrastructure](modules/specialized-infra.md)

## Key Takeaways

### Hybrid Networking
- **Managed > DIY:** Always use AWS managed services (TGW, DX, VGW) over DIY EC2 appliances for HA and operational ease.
- **TGW Segmentation:** **Association = Isolation.** Use separate Route Tables to isolate environments (e.g., Prod/Dev).
- **Most Specific Wins:** Routing follows the "Longest Prefix Match" principle. BGP attributes (AS-Path/Local Pref) are used to steer hybrid traffic.
- **Direct Connect:** Not encrypted by default; must use VPN or MACsec.

### DNS & Hybrid Resolution
- **DNS = Traffic:** Resolver Endpoints (Inbound/Outbound) are ENIs with private IPs. They follow the same private network paths (VPN/DX) as application traffic.
- **Rule Precedence:** **Most specific rule wins**. System rules (e.g., `amazonaws.com`) always take precedence for AWS native service endpoints.
- **Resolver Endpoints:** Inbound allows on-prem to resolve PHZs; Outbound + Resolver Rules allow VPC resources to resolve on-premises domains via forwarding.

### Governance & Security
- **Delegation:** Use Organizations and Delegated Administrators to manage security services (GuardDuty, Config, etc.) centrally, avoiding the use of the Management account for day-to-day tasks.
- **ABAC Scaling:** ABAC using session tags (from IAM Identity Center) is superior to RBAC for large-scale multi-account environments as it removes the need to update per-project policies.


### Mental Model: TGW Network Segmentation

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

### Mental Model: Hybrid DNS Flow

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
```

### Mental Model: Managed Service Failover (VGW)

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

