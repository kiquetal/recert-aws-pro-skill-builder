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
- **Direct Connect:** It is not encrypted by default; layer a VPN or use MACsec if required.

### DNS & Hybrid Resolution
- **DNS = Traffic:** Resolver Endpoints (Inbound/Outbound) are ENIs with private IPs. They obey the same routing rules (VPN/DX paths) as application traffic.
- **Rule Precedence:** **Most specific rule wins**. System rules (e.g., `amazonaws.com`) always take precedence for AWS native service endpoints.
- **Resolver Endpoints:** Inbound allows on-prem to resolve PHZs; Outbound + Resolver Rules allow VPC resources to resolve on-premises domains via forwarding.

### Governance & Security
- **Delegation:** Use Organizations and Delegated Administrators to manage security services (GuardDuty, Config, etc.) centrally, avoiding the use of the Management account for day-to-day tasks.
- **ABAC Scaling:** ABAC using session tags (from IAM Identity Center) is superior to RBAC for large-scale multi-account environments as it removes the need to update per-project policies.
