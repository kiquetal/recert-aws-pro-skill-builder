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

## Key Takeaways

- **Resolver Rule Precedence:** When evaluating DNS queries, **the most specific rule wins**.
- **System Rules:** AWS-managed rules (System rules) take precedence over custom rules.
- **Mental Model: Managed vs. DIY:** Always prefer managed AWS services (VGW/TGW) for HA and scale over DIY EC2 VPN appliances.
- **Mental Model: TGW Segmentation:** **Association = Isolation.** Use separate route tables for environments that must not communicate (e.g., Prod vs. Dev).
- **Mental Model: Routing Plane:** **Most specific route always wins** (Longest Prefix Match). BGP is the "steering wheel" (AS-Path/Local Pref) for hybrid traffic.
- **Mental Model: DNS is just Traffic:** Route 53 Resolver Endpoints are just ENIs with private IPs. They obey the same routing rules (VPN/DX paths) as application traffic.
- **Direct Connect:** It is not encrypted by default; layer a VPN or use MACsec if required.
- **Cross-Account Governance:** Use Organizations, SCPs, and Delegated Administrators to enforce security guardrails centrally without using the management account.
- **ABAC vs. RBAC:** Attribute-Based Access Control (ABAC) scales better in large multi-account orgs via session tags; RBAC requires a new role/policy per team.

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

