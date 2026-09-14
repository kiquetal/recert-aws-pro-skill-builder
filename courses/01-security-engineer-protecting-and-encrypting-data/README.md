<!--
  Source of truth for this course. After editing the metadata below, mirror
  Type/Points/Status/Date into the tracker table in the root README.md and
  refresh the Progress Summary dashboard.
-->

# AWS Security Engineer: Protecting and Encrypting Data

## Metadata

| Field           | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| Name            | AWS Security Engineer: Protecting and Encrypting Data        |
| Type            | Course                                                       |
| Points          | 80 (≈1h)                                                     |
| Status          | In progress                                                  |
| Date completed  | —                                                            |
| Skill Builder   | <paste the course/lab URL>                                   |

> Reminder: Professional recert needs **700 points total** including **at least
> 2 practical activities (labs)**. "Type = Lab" counts toward the 2-lab minimum.

## Course Outline

- **Introduction** — How to Use This Course · Course Overview
- **Keys, Certificates and Encryption** — Preliminary concepts · Managing Keys
  and Certificates on AWS · Deployment Considerations
- **Protecting data at rest** — Data encryption at rest · Data Integrity ·
  Masking and redacting data · Retention and Lifecycle management · Data
  replication and backups
- **Protecting data in transit** — Requiring encryption at edge · Secure and
  Private Access to Compute Resources · Inter-resource encryption
- **Conclusion** — Knowledge Check · Recap and Resources · Contact Us

## Key Takeaways

- <Bullet the most important concepts you learned.>

## Services Covered

- <e.g., AWS KMS> — <how it was used>
- <e.g., Amazon S3 encryption / SSE-KMS> — <...>
- <e.g., AWS Certificate Manager, Secrets Manager> — <...>

## Diagrams

```mermaid
flowchart LR
    Client -->|TLS| App
    App -->|encrypt with CMK| KMS[AWS KMS]
    App --> S3[(S3 SSE-KMS)]
```

## Screenshots

Store images in `./assets/` and embed them here:

```md
![Description](./assets/example-screenshot.png)
```

## Notes / Scratchpad

- <Gotchas, follow-up reading, questions.>
