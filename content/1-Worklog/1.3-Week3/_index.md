---
title: "Week 3 Worklog"
date: 2026-07-13
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

**Personal Tasks:** Analyze the requirements and finalize the deployment plan for the NeonFoodMap project on AWS, while studying the AWS services required for storage, databases, Containers, Networking, and traffic distribution.

During Week 3, I focused on analyzing the NeonFoodMap architecture, selecting appropriate AWS services, and preparing the application for deployment.

The main objectives for the week were:

* Learn about **Amazon RDS** and relational database deployment on AWS.
* Learn about **Amazon ECR** and **Amazon ECS/Fargate** for Container deployment.
* Learn about **Application Load Balancer (ALB)** and its role in distributing traffic to Backend Containers.
* Learn about **Amazon S3** for storing Objects and static resources.
* Understand the roles of **CloudFront** and **API Gateway** in the system architecture.
* Analyze the NeonFoodMap architecture, including **React Frontend, Django Backend, and Database**.
* Check **Environment Variables, API Endpoint, Database Connection, and CORS**.
* Identify the required AWS components and their relationships.
* Prepare the **CI/CD** deployment flow: **GitHub → GitHub Actions → Docker → ECR → ECS/Fargate**.

### Tasks to Be Implemented During the Week:

| Day | Tasks                                                                                                                                                                                                                                                                     | Start Date | Completion Date | Reference Materials                                                                                                                                                                                                   |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Select **NeonFoodMap** as the project for AWS deployment.<br>- Define the deployment scope and requirements.<br>- Analyze the current architecture and identify the Frontend, Backend, Database, Storage, and Networking components.                                    | 06/07/2026 | 06/07/2026      |                                                                                                                                                                                                                       |
| 3   | - Analyze the main functions and architecture of NeonFoodMap.<br>- Review the **React Frontend, Django Backend, and Database**.<br>- Check Environment Variables, API Endpoint, Database Configuration, and CORS before deployment.                                       | 07/07/2026 | 07/07/2026      |                                                                                                                                                                                                                       |
| 4   | - Design the AWS deployment architecture.<br>- Select **Amazon VPC, ECS/Fargate, ECR, RDS, S3, CloudFront, and Application Load Balancer**.<br>- Evaluate the potential use of API Gateway.                                                                               | 08/07/2026 | 08/07/2026      | https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html<br>https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html<br>https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html |
| 5   | - Develop the **CI/CD** deployment plan.<br>- Prepare the GitHub Repository and Source Code management strategy.<br>- Define the GitHub Actions, Docker, ECR, and ECS/Fargate workflow.<br>- Develop a plan for managing Environment Variables and sensitive information. | 09/07/2026 | 09/07/2026      | https://docs.github.com/en/actions<br>https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html                                                                                                         |
| 6   | - Review the AWS services and the relationships between the components.<br>- Prepare the Repository, Docker configuration, and development environment for the following tasks.                                                                                           | 10/07/2026 | 10/07/2026      |                                                                                                                                                                                                                       |

### Week 3 Results:

After completing the assigned tasks, I achieved the following results:

* Identified **NeonFoodMap** as a suitable project for practicing Cloud deployment on AWS.

* Analyzed the main system components, including **React Frontend, Django Backend, and Database**.

* Understood the roles of **Amazon RDS, Amazon S3, Amazon ECR, ECS/Fargate, and Application Load Balancer**.

* Finalized the overall AWS architecture, including:

  * **Amazon VPC** for Networking.
  * **Amazon ECS/Fargate** for Container deployment.
  * **Amazon ECR** for Docker Image storage.
  * **Amazon RDS** for the Database.
  * **Amazon S3** for Object and static resource storage.
  * **Amazon CloudFront** for Frontend content distribution.
  * **Application Load Balancer** for Backend traffic distribution.
  * **Amazon CloudWatch** for Monitoring and Logging.

* Identified key configurations such as API Endpoint, Database Connection, CORS, and Environment Variables.

* Established the CI/CD deployment flow:

  **Source Code → GitHub → GitHub Actions → Docker Build → Amazon ECR → ECS/Fargate**

* Prepared the development environment, Source Code, and required configurations for AWS deployment in the following weeks.
