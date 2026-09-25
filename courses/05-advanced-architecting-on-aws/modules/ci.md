# CI/CD & Databases

- **CI/CD as an Architectural Fail-Safe:** CI/CD pipelines are not just for code deployment; they are the orchestrators of your **Failover and Rollback strategy**.
    - **Blue/Green Deployment:** The fundamental pattern for mitigating deployment risk. It allows testing in a "Green" environment before switching traffic, providing an instant rollback path (switching traffic back to "Blue") if the deployment fails.
    - **Automation of Failure:** Modern pipelines (CodePipeline) are configured to detect deployment failures (via CloudWatch Alarms or health checks) and automatically trigger a rollback to the last known good configuration.

- **Source Control:** AWS recommends using third-party Git providers (GitHub, GitLab, Bitbucket) which integrate natively with CodePipeline. 
    - *Legacy:* **AWS CodeCommit** is a managed source control service, but is no longer open to new customers.

- **AWS CodeBuild:** Fully managed build service that compiles source code, runs tests, and produces software packages that are ready to deploy.
- **AWS CodeDeploy:** Fully managed deployment service that automates software deployments to a variety of compute services such as Amazon EC2, AWS Fargate, AWS Lambda, and your on-premises servers.
- **AWS CodePipeline:** Fully managed continuous delivery service that helps you automate your release pipelines for fast and reliable application and infrastructure updates. It integrates natively with third-party source providers.
- **AWS CodeArtifact:** Fully managed artifact repository service that makes it easy for organizations of any size to securely store, publish, and share software packages.

- **Amazon RDS Blue/Green Deployments:** A feature where AWS manages the replication, but the *strategy* of when and how to perform the switchover is an **architectural decision**.
    - **Not a "Magic Button":** While AWS manages the replication, the architect must decide:
        - **Maintenance Window:** When to trigger the cutover (during low traffic is mandatory to minimize session drops).
        - **Schema Compatibility:** Ensuring changes on Green don't break Blue during replication.
        - **Application Resiliency:** The application *must* have retry logic to handle the brief connection reset during the DNS switchover.
    - **Use Case:** Managed major version upgrades, parameter group changes, or OS patching with minimized downtime.

### Managed Service Failover (Blue/Green)
```text
    [Application]
          | (Read/Write)
          v
    +--------------------------+
    | Blue (Production DB)     | <--- (Logical Replication) --- [Green (Staging DB)]
    +--------------------------+                                (Target Version)
          |
    (During Switchover)
          |
    [Application] --> [Green (Becomes Production)]
```
