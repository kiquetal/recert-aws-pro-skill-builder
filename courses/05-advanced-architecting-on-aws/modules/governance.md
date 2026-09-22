# Governance & Organization

- **AWS Organizations** — multi-account structure (OUs), SCPs, delegated admin, org-wide policies.
- **AWS Control Tower** — landing zone / guardrails to set up and govern a secure multi-account environment.
- **AWS Service Catalog** — governed, self-service distribution of approved products (templates).
- **AWS Deployment Framework (ADF)** — open-source CI/CD orchestration for multi-account/multi-region deployments.
- **AWS IAM Identity Center** — centralized workforce sign-in and permission sets; federates to external IdPs and supplies identity attributes (session tags) for ABAC.
- **AWS Resource Access Manager (AWS RAM)** — share resources (VPCs, TGWs, Route 53 Resolver rules) across accounts/OUs without duplication.
- **AWS Backup** — centralized, policy-driven backup across accounts (via Organizations); supports cross-account backup vaults and WORM (Vault Lock).
- **AWS CloudFormation / StackSets** — infrastructure as code; StackSets fans a template out across accounts and regions.
