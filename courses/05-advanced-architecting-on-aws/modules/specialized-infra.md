# Specialized Infrastructure

- **AWS Storage Gateway** — A hybrid cloud storage service that gives you on-premises access to virtually unlimited cloud storage.
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
        - **FSx File Gateway:**
            - **Protocols:** SMB.
            - **Use Case:** Low-latency, on-premises access to Amazon FSx for Windows File Server.
        - **Volume Gateway:**
            - **Protocols:** iSCSI.
            - **Use Case:** Providing block storage volumes (backed by EBS snapshots) to on-premises applications, integrated with AWS Backup.

![AWS Volume Gateway — showing the provisioning of iSCSI block storage volumes for on-premises applications.](../assets/volume-gateway.png)
        - **Tape Gateway:**
            - **Protocols:** iSCSI-VTL (Virtual Tape Library).
            - **Use Case:** Replacing physical tape infrastructure for archival backups, integrated with S3 Glacier.

![AWS Tape Gateway — illustrating the setup of a virtual tape library for on-premises archival backups.](../assets/tape-gateway.png)
