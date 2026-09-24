# CI/CD on AWS

- **Source Control:** AWS recommends using third-party Git providers (GitHub, GitLab, Bitbucket) which integrate natively with CodePipeline. 
    - *Legacy:* **AWS CodeCommit** is a managed source control service, but is no longer open to new customers.

- **AWS CodeBuild:** Fully managed build service that compiles source code, runs tests, and produces software packages that are ready to deploy.
- **AWS CodeDeploy:** Fully managed deployment service that automates software deployments to a variety of compute services such as Amazon EC2, AWS Fargate, AWS Lambda, and your on-premises servers.
- **AWS CodePipeline:** Fully managed continuous delivery service that helps you automate your release pipelines for fast and reliable application and infrastructure updates. It integrates natively with third-party source providers.
- **AWS CodeArtifact:** Fully managed artifact repository service that makes it easy for organizations of any size to securely store, publish, and share software packages.
