# AWS Certified Solutions Architect – Professional: Recertification Tracker

Documenting my recertification of the **AWS Certified Solutions Architect –
Professional (SAP-C02)** via the **AWS Skill Builder "Recertify / Maintain"
path** — completing curated courses and hands-on labs to extend the credential
by 1 year, instead of retaking the full exam.

---

## Progress Summary

| Metric                          | Value                          |
| ------------------------------- | ------------------------------ |
| Points earned                   | **280 / 700**                  |
| Practical activities (labs)     | **1 / 2** minimum              |
| Overall completion              | **40%**                        |
| Certification expiry            | **2026-12-13**                 |
| Days remaining                  | **~85** (as of 2026-09-19)     |
| Path                            | Maintain via Skill Builder (+1 year) |

> **How to update:** Edit the course's own `README.md` under `courses/` first
> (it is the source of truth), then mirror its Type/Points/Status/Date into the
> **Course & Lab Tracker** table below and recompute the numbers here:
> sum the confirmed Points (target 700), count rows with `Type = Lab` and
> `Status = Done` toward the 2-lab minimum, and recompute Days remaining
> against the 2026-12-13 expiry.

---

## Eligibility & Deadlines

| Field                       | Value                                             |
| --------------------------- | ------------------------------------------------- |
| Certification               | AWS Certified Solutions Architect – Professional  |
| Certification expiry        | 2026-12-13                                        |
| Eligibility window          | Within 90 days of expiry (must still be active)   |
| Eligible now?               | ✅ Yes — within the 90-day window                 |
| Skill Builder subscription  | ⬜ Confirm active paid subscription (Individual/Team) |
| Chosen path                 | Maintain via Skill Builder → **+1 year** extension |

---

## How Recertification Works

AWS certifications are valid for three years. You can keep the SA – Professional
credential current in two ways:

1. **Renew** — pass the latest version of the exam → **+3 years**.
2. **Maintain** — complete curated training + labs on AWS Skill Builder →
   **+1 year** (the path used in this repo).

Details of the Maintain path (verified from official AWS sources):

- **Eligibility:** available when your certification is **within 90 days of
  expiration** and still **active**. Expired certifications are **not** eligible.
- **Prerequisite:** an **active paid AWS Skill Builder subscription**
  (Individual monthly/annual, or Team).
- **Where:** in AWS Skill Builder, go to **Explore → Validate your skills →
  Recertify**, then select **Solutions Architect – Professional**.
- **Threshold (Professional):** earn **700 points**, including **at least 2
  practical activities (hands-on labs)**. (Associate-level requires 500 points
  and at least 1 practical activity.)
- **Pace:** self-paced; complete everything **before your certification
  expires**.
- **Result:** your certification is **extended by 1 year** from the completion
  date, reflected in your AWS Certification account.
- **Cascading extension:** maintaining SA – Professional also extends a still-
  active, related lower-level cert (e.g., SA – Associate) to match the new
  expiration date.
- **Status:** this maintenance experience is currently in **open Beta**.

---

## Course & Lab Tracker

The `courses/` folder holds one subfolder per course/lab (each with its own
`README.md` notes + `assets/` for diagrams and screenshots). This table mirrors
the key metadata from those folders.

| #  | Name                                                                                                         | Type | Points | Status      | Date started | Date completed |
| -- | ------------------------------------------------------------------------------------------------------------ | ---- | ------ | ----------- | ------------ | -------------- |
| 01 | [AWS Security Engineer: Protecting and Encrypting Data](./courses/01-security-engineer-protecting-and-encrypting-data/) | Course | 80     | Done        | 2026-09-14   | 2026-09-18     |
| 02 | [AWS Security Engineer: Edge Security](./courses/02-security-engineer-edge-security/) | Course | 100    | Done        | 2026-09-18   | 2026-09-19     |
| 03 | [AWS SimuLearn: Resolve VPC Routing Conflicts](./courses/03-simulearn-resolve-vpc-routing-conflicts/) | Lab | 100 | Done | 2026-09-19   | 2026-09-19     |
| 04 | [AWS SimuLearn: Inter-Region Peering](./courses/04-simulearn-inter-region-peering/) | Lab | 100 | In progress | 2026-09-19   | —              |

**Running totals:** 280 / 700 points confirmed (100 pending on completion of lab 04) · 1 / 2 labs.

### Adding a new course

1. Copy `courses/_TEMPLATE/` to `courses/NN-short-slug/` (next number `NN`).
2. Fill in the metadata block and notes in that folder's `README.md`.
3. Add a row to the tracker table above and update the Progress Summary.

---

## Available Courses (Skill Builder)

Digital courses offered on the recert path. Points/time as listed on Skill
Builder. Folders under `courses/` are scaffolded only when a course is started.

| Course                                                                   | Points | Time  | Recommendation      |
| ------------------------------------------------------------------------ | ------ | ----- | ------------------- |
| AWS Security Engineer - Protecting and Encrypting Data *(course 01)*      | 80     | 1h    | ⭐ Start (finish it) |
| AWS Security Engineer - Edge Security                                    | 100    | 1h15m | ⭐ Start            |
| AWS Security Engineer - Centralized Account Management                    | 80     | 1h    | Next               |
| AWS Security Engineer - Network Security and Secure Hybrid Connectivity   | 100    | 1h15m | ⭐ Start            |
| Well-Architected For Enterprises                                         | 80     | 1h    | ⭐ Start            |
| Automating Cloud Security Posture Management on AWS                       | 80     | 50m   | Next               |
| Selecting your Data Migration Strategy with AWS                          | 40     | 30m   | Next               |
| Deploying Serverless Applications                                        | 120    | 1h30m | Optional           |
| Security and Observability for Serverless Applications                   | 120    | 1h30m | Optional           |
| Advanced Architecting on AWS - Online Course Supplement                  | 160    | 2h    | ⭐ Start (top pick) |
| Building Your Agentic Applications the Well-Architected Way               | 160    | 2h    | Optional           |
| Security, Compliance, and Governance for AI Solutions                    | 80     | 1h    | Optional           |
| Automate Generative AI workflows using Amazon Bedrock Flows              | 40     | 30m   | Optional           |

**Legend:** ⭐ Start = highest SA-Professional learning value, begin here ·
Next = solid secondary picks · Optional = valuable but less central to SAP-C02.

### Recommended path to 700

A mix weighted toward SA-Professional exam domains (architecture, networking,
hybrid connectivity, security), satisfying the 2-lab minimum:

| Item                                                                     | Type | Points |
| ------------------------------------------------------------------------ | ---- | ------ |
| AWS SimuLearn: Resolve VPC Routing Conflicts                             | Lab  | 100    |
| AWS SimuLearn: Inter-Region Peering                                      | Lab  | 100    |
| Advanced Architecting on AWS - Online Course Supplement                  | Course | 160  |
| AWS Security Engineer - Network Security and Secure Hybrid Connectivity   | Course | 100  |
| AWS Security Engineer - Edge Security                                    | Course | 100  |
| AWS Security Engineer - Protecting and Encrypting Data *(course 01)*      | Course | 80   |
| Well-Architected For Enterprises                                         | Course | 80   |
| **Total**                                                                |      | **720** |

720 ≥ 700 with the 2-lab minimum met (~9h of content). Swap items freely — the
700-point total is the binding constraint, not the lab count.

---

## Candidate Labs (AWS SimuLearn)

Available practical activities on Skill Builder. Each is a **Practical** lab worth
**+100 pts** (~1h) and counts toward the **2-lab minimum**. Not yet started; folders
are scaffolded under `courses/` only when a lab is committed to.

| Lab                                                          | Points | Recommended |
| ------------------------------------------------------------ | ------ | ----------- |
| AWS SimuLearn: Resolve VPC Routing Conflicts                 | 100    | ⭐          |
| AWS SimuLearn: Inter-Region Peering                          | 100    | ⭐          |
| AWS SimuLearn: Securing Hybrid Access                        | 100    | ⭐          |
| AWS SimuLearn: Securing a Banking Data Lake                  | 100    | ⭐          |
| AWS SimuLearn: Hybrid Storage Solution for PACS              | 100    |             |
| AWS SimuLearn: Content Acceleration on the Edge              | 100    |             |
| AWS SimuLearn: Edge to Cloud Architecture for Digital Twins  | 100    |             |
| AWS SimuLearn: Provision SageMaker in a Secure Environment   | 100    |             |

**Recommended for SA-Professional learning value** (⭐): these give the broadest
coverage of Pro-level exam domains — complex networking, hybrid connectivity,
multi-region, and data security:

- **Resolve VPC Routing Conflicts** — core VPC networking troubleshooting.
- **Inter-Region Peering** — multi-region / DR networking patterns.
- **Securing Hybrid Access** — hybrid connectivity plus security controls.
- **Securing a Banking Data Lake** — data security and governance at scale.

Doing these four = 400 pts; with course 01 (80) that's **480 / 700**. The 2-lab
minimum is easily met; the 700-point total is the binding constraint, so plan a
mix of labs and courses to close the gap.

---

## References

- AWS Certification Renewal (official): <https://aws.amazon.com/certification/recertification/>
- "A new way to keep your AWS Certification current" (announcement): <https://aws.amazon.com/blogs/training-and-certification/a-new-way-to-keep-your-aws-certification-current/>
- Recertify on AWS Skill Builder: <https://skillbuilder.aws/certification/recertification>
