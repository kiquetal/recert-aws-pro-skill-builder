# Governance & Organization

- **AWS Organizations** — multi-account structure (OUs), SCPs, delegated admin, org-wide policies.
    - **Delegated Administrator:** Best practice to assign a dedicated member account (e.g., SecurityTooling) for security services (GuardDuty, Config, Security Hub) to avoid using the Management account for day-to-day operations.
    - **SCPs (Service Control Policies):** Guardrails that set the **maximum permissions** (permission boundary) for accounts in an OU/org. They **do not grant** access; they only **limit** it.
        - *Logic:* Intersection of SCP AND IAM Policy = Effective Permissions.
        - *Management Account:* **Not** restricted by SCPs.
    - **Backup Policies:** Centrally authored, policy-driven backup rules applied across OUs/accounts.

- **AWS IAM Identity Center** — Centralized workforce sign-in.
    - **ABAC (Attribute-Based Access Control):** Uses identity attributes (from IdP) as **session tags** to dynamically grant access to resources with matching tags. Scales significantly better than RBAC (no need for new roles for every team).

- **AWS Control Tower** — Landing zone / guardrails setup.
    - **Guardrails:** Pre-packaged rules (Detective and Preventive) for compliance (e.g., "Disallow public S3 buckets").

- **AWS CloudFormation / StackSets** — Multi-account/region IaC.
    - **Deployment Models:**
        - **Self-managed:** Requires manual creation of `AdministrationRole` (Admin Acct) and `ExecutionRole` (Member Acct).
        - **Service-managed:** Uses AWS Organizations to automatically create/manage roles and auto-deploy to new accounts in an OU.

- **AWS Service Catalog** — Governed self-service distribution of approved products (templates).
- **AWS Deployment Framework (ADF)** — CI/CD orchestration for multi-account/multi-region deployments.
- **AWS Resource Access Manager (AWS RAM)** — Share resources (VPCs, TGWs, Route 53 Resolver rules) across accounts/OUs without duplication.
- **AWS Backup** — Centralized, policy-driven backup across accounts (via Organizations); supports cross-account backup vaults and WORM (Vault Lock).
- Security services (org-wide): **GuardDuty, Macie, IAM Access Analyzer, Firewall Manager, Config**.

## Diagrams

### StackSets: Enablement and Deployment
![StackSets member enablement + deploy sequence — one-time setup (create Administration role in mgmt; create Execution role in member with trust to mgmt + resource permissions), then deploy (CloudFormation assumes Administration role, which assumes the member's Execution role across the boundary to create resources).](../assets/stacksets-enablement.png)

### StackSets: Conceptual
![AWS StackSets conceptual diagram — an administrator account's stack set deploys stacks into Target account A and B across two regions.](../assets/aws-stacksets-conceptual.png)

### Security Services Org-wide
![Enable security services for the organization — activating a service org-wide activates it across all member accounts (GuardDuty, Macie, IAM Access Analyzer, Firewall Manager, Config, and more).](../assets/enable-security-services.png)

### Delegated Admin
![Delegate administration for security services — the management account delegates security-tooling ownership to a SecurityToolingProd account, which manages org-wide security services across member accounts.](../assets/delegated-admin-security.png)
