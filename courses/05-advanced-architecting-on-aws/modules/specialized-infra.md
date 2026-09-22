# Specialized Infrastructure

- **AWS Storage Gateway** — A hybrid cloud storage service that gives you on-premises access to virtually unlimited cloud storage.
    - **Benefits:**
        - **Low-Latency Access:** Provides local cached access to data stored in the cloud.
        - **Seamless Integration:** Works with existing on-premises applications/file systems using standard storage protocols (NFS, SMB, iSCSI).
        - **Data Security:** Data is encrypted in transit (TLS) and at rest (AWS-managed keys).
        - **Simplified Management:** Replaces expensive, complex on-premises backup and storage infrastructure with a simple virtual appliance.
        - **Cost-Effective:** Reduces on-premises storage footprint by tiered caching, keeping active data local and cold data in S3.
    - **Types:** File Gateway (S3), Volume Gateway (EBS snapshots), Tape Gateway (Archival).

![Specialized Infrastructure Overview — showing architectural context for Storage Gateway and related edge services.](../assets/specialized-infra.png)

- File Gateway
nfs, smb
store and access object in S3.
- Tape Gateway
drop-in replacemente for phsucial tape infraestructure backed by cloud storage with local caching

- Volume Gateway
block storage on premsised by cloud storage with lcoal caching, amazon ebs, snapt shot, integrated with aws backup
