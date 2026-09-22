## Gateway Decision Matrix

| Gateway Type | Decision Point | Professional Architect Insight |
| :--- | :--- | :--- |
| **Volume Gateway** | Cached vs. Stored | Choose **Stored** for 100% local residency/performance. Choose **Cached** for cloud-based scalability. |
| **S3 File Gateway** | Local Cache Size | Performance is directly tied to the cache size. Size cache to cover the "working set" of files. |
| **Tape Gateway** | Archival Class | Choose **Glacier Deep Archive** for lowest cost, but account for longer retrieval times (hours). |

---
    - **Benefits:**
        - **Low-Latency Access:** Provides local cached access to data stored in the cloud.
        - **Seamless Integration:** Works with existing on-premises applications/file systems using standard storage protocols (NFS, SMB, iSCSI).
        - **Security:**
        - **Data in Transit:** All traffic encrypted via **TLS** between the appliance and AWS.
        - **Data at Rest:** Encrypted via **KMS** (AWS-managed or Customer Managed Keys).
        - **Network:** Use **VPC Endpoints (PrivateLink)** to keep traffic off the public internet.
        - **Access Control:** Use **Least Privilege IAM Roles** for the gateway's access to S3/EBS; ensure S3 buckets have **Block Public Access** enabled.
        - **Simplified Management:** Replaces expensive, complex on-premises backup and storage infrastructure with a simple virtual appliance.
        - **Cost-Effective:** Reduces on-premises storage footprint by tiered caching, keeping active data local and cold data in S3.
    - **Types & Supported Protocols:**
        - **S3 File Gateway:** 
            - **Protocols:** NFS (v3, v4.1) and SMB (v2, v3). Both protocols are supported for access.
            - **Use Case:** Storing files in S3 while maintaining a local cache for low-latency access.

![AWS S3 File Gateway — showing the integration of on-premises file storage with S3 via NFS/SMB protocols.](../assets/storage-file-gateway.png)
        - **Volume Gateway:**
            - **Protocols:** iSCSI.
            - **Modes:**
                - **Cached Volumes:** Primary data is stored in S3, while frequently accessed data is cached locally on-premises for low latency. Ideal for offloading on-premises storage costs while maintaining performance.
                - **Stored Volumes:** Entire dataset is stored on-premises (local disk) for maximum performance, with asynchronous backups to S3 as EBS snapshots. Ideal for legacy applications requiring local data residency.
            - **Use Case:** Providing block storage volumes (backed by EBS snapshots) to on-premises applications, integrated with AWS Backup.

![AWS Volume Gateway — showing the provisioning of iSCSI block storage volumes for on-premises applications.](../assets/volume-gateway.png)
        - **Tape Gateway:**
            - **Protocols:** iSCSI-VTL (Virtual Tape Library).
            - **Use Case:** Replacing physical tape infrastructure for archival backups, integrated with S3 Glacier.

![AWS Tape Gateway — illustrating the setup of a virtual tape library for on-premises archival backups.](../assets/tape-gateway.png)
