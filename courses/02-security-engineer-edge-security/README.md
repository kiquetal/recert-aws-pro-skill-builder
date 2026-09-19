<!--
  PER-COURSE NOTES TEMPLATE
  Copy this whole folder (_TEMPLATE/) to courses/NN-short-slug/ for each new
  course or lab, then fill in the metadata block and sections below.
  This file is the SOURCE OF TRUTH for the course. After editing it, mirror the
  key metadata (Type, Points, Status, Date completed) into the tracker table in
  the root README.md and refresh the Progress Summary dashboard.
-->

# AWS Security Engineer: Edge Security

## Metadata

| Field           | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| Name            | AWS Security Engineer: Edge Security                         |
| Type            | Course                                                       |
| Points          | 100 (≈1h15m)                                                 |
| Status          | In progress                                                  |
| Date completed  | —                                                            |
| Skill Builder   | https://skillbuilder.aws/learn/Q8QC4V4BMF/aws-security-engineer-edge-security/M3ZVNJGPX7 |

> Reminder: Professional recert needs **700 points total** including **at least
> 2 practical activities (labs)**. "Type = Lab" counts toward the 2-lab minimum.

## Key Takeaways

- **Edge vs. network controls** — edge controls (CloudFront, WAF, Shield) sit at
  the *perimeter* and filter internet traffic before it reaches the VPC; network
  controls (security groups, NACLs, Network Firewall, Transit Gateway) are
  *internal* checkpoints between resources.
- **Shield Standard vs. Advanced** — Standard is free/automatic and covers
  **L3/L4** DDoS; Advanced is a paid subscription adding **L7** protection, the
  DDoS Response Team, cost protection, and WAF integration.
- **WAF = L7 request filtering** — inspects HTTP/HTTPS requests and blocks OWASP
  Top 10 patterns (SQL injection, XSS) and malicious bots.
- **CloudFront is both CDN and edge security** — low-latency delivery plus HTTPS,
  field-level encryption, and geo access controls at AWS's points of presence.

## Services Covered

- **AWS Shield (Standard & Advanced)** — managed DDoS protection at the edge
  (L3/L4 always-on; L7 + DRT/cost protection with Advanced).
- **AWS WAF** — L7 web application firewall filtering HTTP/HTTPS requests
  (SQLi, XSS, bots, OWASP Top 10).
- **Amazon CloudFront** — global CDN with edge security (HTTPS, field-level
  encryption, geo restrictions).
- **Amazon Route 53 / AWS Global Accelerator** — edge-facing services protected
  by Shield.

## Diagrams

Prefer inline Mermaid for architecture/flow (version-control friendly). Example:

```mermaid
flowchart LR
    User -->|request| Service
    Service --> Store[(Data store)]
```

## Screenshots

**Network controls vs. edge controls** — network controls operate *inside* the
VPC (security groups, network ACLs, AWS Network Firewall, Transit Gateway),
acting as internal barriers for east-west and north-south traffic within your
VPC boundaries.

![Network controls operate within the AWS VPC — internal barriers (security groups, NACLs, Network Firewall, Transit Gateway) for traffic that has already entered the cloud environment.](./assets/network-controls.png)

**Edge controls** operate at the *perimeter*, where the public internet meets
your AWS environment — the first line of defense, inspecting and filtering
traffic before it reaches your VPC. Edge services like **CloudFront**, **AWS
WAF**, and **AWS Shield** protect applications from internet-based threats at
global scale via AWS's points of presence (think "border security"), while
network controls act as internal checkpoints between resources.

![Edge controls operate at the perimeter (Internet Gateway boundary) — CloudFront, AWS WAF, and Shield inspect and filter traffic before it reaches the VPC.](./assets/edge-controls.png)

## Notes / Scratchpad

- <Anything else: gotchas, follow-up reading, questions.>
