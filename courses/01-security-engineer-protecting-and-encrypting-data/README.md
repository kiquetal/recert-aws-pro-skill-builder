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

- **Symmetric vs. asymmetric encryption** — Symmetric encryption uses the *same*
  key to encrypt and decrypt. Asymmetric encryption uses a *key pair*: one key
  encrypts and a different (mathematically related) key decrypts.
- **Hashing is one-way** — Hashing applies an algorithm to a message to produce
  a fixed, randomized string of bits (a hash). Unlike encryption, it is a
  one-way operation: the hash cannot be reversed back to the original plaintext.
  Useful for integrity checks, not confidentiality.
- **Digital certificates prove identity** — A digital certificate is an
  electronic credential that proves the authenticity of a user, device, server,
  or website. It relies on public-key cryptography to validate identities of
  parties communicating over a network.

## Services Covered

- **AWS KMS** — Create and manage encryption keys (symmetric CMKs, asymmetric
  key pairs); envelope encryption for data at rest.
- **AWS Certificate Manager (ACM)** — Provision, manage, and deploy digital
  certificates (public-key) for TLS/HTTPS on AWS resources.
- **Amazon S3 encryption (SSE-KMS / SSE-S3)** — Encrypt objects at rest; enforce
  encryption in transit via bucket policies (`aws:SecureTransport`).
- **AWS Secrets Manager** — Store, rotate, and protect secrets used by
  applications and services.
- **Amazon Macie** — Discover, classify, mask/redact sensitive data (PII) at
  scale for data protection and integrity.

## Diagrams

**Symmetric vs. asymmetric encryption**

```mermaid
flowchart LR
    subgraph Symmetric["Symmetric (same key)"]
        P1[Plaintext] -->|encrypt with Key K| C1[Ciphertext]
        C1 -->|decrypt with Key K| P1b[Plaintext]
    end
    subgraph Asymmetric["Asymmetric (key pair)"]
        P2[Plaintext] -->|encrypt with Public key| C2[Ciphertext]
        C2 -->|decrypt with Private key| P2b[Plaintext]
    end
```

**Hashing is one-way**

```mermaid
flowchart LR
    M[Message] -->|hash algorithm| H[Fixed-length hash]
    H -.->|cannot reverse| M
```

**Digital certificate proves identity (TLS handshake)**

```mermaid
sequenceDiagram
    participant Client
    participant Server
    Server->>Client: Certificate (server public key + CA signature)
    Client->>Client: Validate cert against trusted CA
    Client->>Server: Encrypt session secret with server public key
    Server->>Server: Decrypt with private key -> secure channel
```

**Protecting data at rest & in transit on AWS**

```mermaid
flowchart LR
    Client -->|TLS via ACM| App
    App -->|encrypt with CMK| KMS[AWS KMS]
    App --> S3[(S3 SSE-KMS)]
```

## Screenshots

Store images in `./assets/` and embed them here:

```md
![Description](./assets/example-screenshot.png)
```

## Notes / Scratchpad

- **Symmetric vs Asymmetric**

  Symmetric encryption uses the same key to encrypt and to decrypt. Asymmetric
  encryption uses one key to encrypt and another to decrypt.

- **Hash**

  Hashing is another application of cryptography in which an algorithm is applied
  to a message to generate a randomized string of bits — this time a hash.
  However, unlike encryption, hashing is a one-way operation: the hash material
  cannot be converted back to plaintext.

- **Digital certificate**

  A digital certificate is an electronic credential that proves the authenticity
  of a user, device, server, or website. This form of authentication uses
  public-key encryption to validate identities communicating over networks.
