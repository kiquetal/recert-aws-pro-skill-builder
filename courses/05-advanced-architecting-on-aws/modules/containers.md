# Containers on AWS

- **Amazon ECS (Elastic Container Service):** Highly scalable, high-performance container management service.
    - **Control Plane:** AWS managed; you only manage the data plane (compute).
    - **Integration:** Deeply integrated with AWS native services (IAM, ALB/NLB, CloudWatch, Secrets Manager).

![Amazon ECS Architecture — illustrating ECS cluster, services, task definitions, and Fargate integration.](../assets/ecs-details.png)
    - **Architecture Description:** The image shows how the ECS Cluster organizes tasks and services. It highlights the use of Task Definitions to declare the container images, CPU/Memory requirements, and IAM Task Roles, and how services maintain the desired number of tasks (pods) across the cluster, optionally using Fargate for serverless compute.

- **Amazon EKS (Elastic Kubernetes Service):** Managed Kubernetes service.
    - **Control Plane:** AWS manages the Kubernetes control plane across multiple AZs.
    - **Use Case:** When portability (standard Kubernetes APIs) and complex service-to-service orchestration are required.

- **Launch Types:**
    - **Fargate (Serverless):** No need to provision or manage servers. AWS manages the underlying infrastructure.
    - **EC2:** You manage the underlying instances, allowing deep control over OS, networking, and instance sizing.

- **Advanced Architectural Considerations:**
    - **IAM Task Roles:** Assign permissions to the *container/task* itself (not the underlying host), allowing the application to securely access AWS services (S3, DynamoDB) via IAM.
    - **Networking (`awsvpc` mode):** Every ECS task receives its own Elastic Network Interface (ENI) and private IP within the VPC, allowing security groups to be applied directly to the container/task.
    - **Service Discovery:** Use Route 53 Service Discovery (AWS Cloud Map) to automatically register and discover services within your VPC.
    - **Scalability:** **Service Auto Scaling** allows scaling tasks based on CPU/Memory utilization or custom metrics (e.g., SQS queue depth).
