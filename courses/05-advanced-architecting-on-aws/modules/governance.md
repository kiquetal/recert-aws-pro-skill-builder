# Governance & Organization

- **AWS CloudFormation / StackSets** — infrastructure as code; StackSets fans a template out across accounts and regions.
    - *How deployment works:* Management/Admin account (AdministrationRole) -> assumes -> Member account (ExecutionRole).

### Diagrams

#### StackSets: Enablement and Deployment
![StackSets member enablement + deploy sequence — one-time setup (create Administration role in mgmt; create Execution role in member with trust to mgmt + resource permissions), then deploy (CloudFormation assumes Administration role, which assumes the member's Execution role across the boundary to create resources).](../assets/stacksets-enablement.png)

#### StackSets: Conceptual
![AWS StackSets conceptual diagram — an administrator account's stack set deploys stacks into Target account A and B across two regions.](../assets/aws-stacksets-conceptual.png)

- **AWS Service Catalog** — governed, self-service distribution of approved products (templates).
- **AWS Deployment Framework (ADF)** — open-source CI/CD orchestration for multi-account/multi-region deployments.
- **AWS Organizations** — multi-account structure (OUs), SCPs, delegated admin, org-wide policies.

#### Security Services Org-wide
![Enable security services for the organization — activating a service org-wide activates it across all member accounts (GuardDuty, Macie, IAM Access Analyzer, Firewall Manager, Config, and more).](../assets/enable-security-services.png)

#### Delegated Admin
![Delegate administration for security services — the management account delegates security-tooling ownership to a SecurityToolingProd account, which manages org-wide security services across member accounts.](../assets/delegated-admin-security.png)

- **AWS IAM Identity Center** — centralized workforce sign-in and permission sets; federates to external IdPs and supplies identity attributes (session tags) for ABAC.
- **AWS Resource Access Manager (AWS RAM)** — share resources (VPCs, TGWs, Route 53 Resolver rules) across accounts/OUs without duplication.
- **AWS Control Tower** — landing zone / guardrails to set up and govern a secure multi-account environment.
- **AWS Backup** — centralized, policy-driven backup across accounts (via Organizations); supports cross-account backup vaults and WORM (Vault Lock).
- Security services (org-wide): **GuardDuty, Macie, IAM Access Analyzer, Firewall Manager, Config**.
