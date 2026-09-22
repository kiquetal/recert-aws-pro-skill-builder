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

- **Resolver Rule Precedence:** When evaluating DNS queries, **the most specific rule wins**.
- **System Rules:** AWS-managed rules (System rules) take precedence over custom rules.
- **Mental Model: Managed vs. DIY:** Always prefer managed AWS services (VGW/TGW) for HA and scale over DIY EC2 VPN appliances.
- **Mental Model: TGW Segmentation:** **Association = Isolation.**
- **Mental Model: Routing Plane:** **Most specific route always wins** (Longest Prefix Match).
- **Mental Model: DNS is just Traffic:** Route 53 Resolver Endpoints are just ENIs with private IPs.
