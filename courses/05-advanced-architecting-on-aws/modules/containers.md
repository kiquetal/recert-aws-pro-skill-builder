# Containers on AWS

- **Amazon ECS (Elastic Container Service):** Highly scalable, high-performance container management service that supports Docker containers. It is deeply integrated with other AWS services (IAM, Load Balancers, CloudWatch).
    - **Launch Types:** 
        - **Fargate:** Serverless; AWS manages the underlying infrastructure.
        - **EC2:** You manage the underlying EC2 instances for more control.

- **Amazon EKS (Elastic Kubernetes Service):** Managed Kubernetes service that makes it easy to deploy, manage, and scale containerized applications using Kubernetes on AWS.
    - **Fargate support:** EKS also supports Fargate for serverless pod execution.

- **Amazon ECR (Elastic Container Registry):** Fully managed container registry for storing, managing, sharing, and deploying container images.

- **Key Architectural Considerations:**
    - **Service Auto Scaling:** Automatically adjust the number of tasks/pods based on demand.
    - **Task/Pod Networking:** Understand VPC networking (awsvpc mode for ECS) to ensure secure, isolated container networking.
    - **CI/CD:** Integrate with AWS CodePipeline and CodeBuild for automated container deployment workflows.
