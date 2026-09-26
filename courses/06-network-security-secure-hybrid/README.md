# Network Security & Secure Hybrid Connectivity

- **Core Principles:**
    - Zero-Trust Architecture: Never trust, always verify.
    - Defense-in-Depth: Multiple layers of security (Edge, Network, Application).
    - Principle of Least Privilege (PoLP): Access limited to what is strictly necessary.

- **Edge Security:**
    - **AWS WAF:** Protects against common web exploits (SQLi, XSS) on ALB/CloudFront/AppSync.
    - **AWS Shield:** DDoS protection.
    - **AWS Network Firewall:** Stateful/stateless traffic filtering at the network boundary.

- **Network Segmentation & Connectivity:**
    - **Transit Gateway (TGW) Segmentation:** Use separate route tables to isolate VPC traffic.
    - **Network ACLs (NACLs):** Stateless filtering at the subnet level.
    - **Security Groups (SGs):** Stateful filtering at the instance/ENI level.

- **Secure Hybrid Access:**
    - **Encrypted Connectivity:** Direct Connect + VPN (IPsec) or MACsec.
    - **Client VPN:** Managed remote access with MFA.

## Diagrams
*(Reference architectural diagrams for secure hybrid traffic flow)*
EOF
