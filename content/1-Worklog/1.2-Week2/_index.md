---
title: "Week 2 Worklog"
date: 2026-07-06
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

**Personal Tasks:** Build foundational knowledge of DevOps, CI/CD, Containers, and AWS services used for application deployment; at the same time, survey and finalize the deployment architecture for the NeonFoodMap project.

During Week 2, I focused on understanding the process of moving an application from the development environment to the Cloud environment through automation. The learning activities combined knowledge of the **AWS Well-Architected Framework, DevOps, CI/CD, Docker, Amazon ECR, Amazon ECS, GitHub Actions, and Amazon CloudWatch**.

The main objectives for the week were:

* Learn about the **AWS Well-Architected Framework** and its 6 architectural pillars:

  * Operational Excellence.
  * Security.
  * Reliability.
  * Performance Efficiency.
  * Cost Optimization.
  * Sustainability.

* Understand the role of the Well-Architected Framework in evaluating and designing Cloud architectures based on criteria such as operations, security, reliability, performance, and cost.

* Learn about the **DevOps** process and the collaboration between Development and Operations throughout software development, deployment, and operations.

* Distinguish between **Continuous Integration (CI), Continuous Delivery (CD), and Continuous Deployment**.

* Understand the role of **Monitoring** in tracking application status, performance, and errors after deployment.

* Learn about **Docker** and the Containerization model for packaging applications and their dependencies into a consistent deployment unit.

* Study the basic components of Docker:

  * Dockerfile.
  * Docker Image.
  * Docker Container.
  * Docker Registry.

* Practice building Docker Images and running Containers in a local environment.

* Learn about **Amazon ECR** for storing and managing Docker Images on AWS.

* Learn about **Amazon ECS** and how ECS can be used to run Containers on AWS.

* Learn the basic ECS concepts, including Cluster, Task Definition, Task, and Service.

* Learn about **GitHub Actions** and how to build automated Workflows for CI/CD.

* Study the components of GitHub Actions, including Workflow, Event, Job, Step, Runner, and Action.

* Learn how to combine GitHub Actions with Docker, ECR, and ECS to create an automated deployment pipeline.

* Learn about **Amazon CloudWatch** and the role of Monitoring/Logging systems in application operations.

* Survey potential projects and identify **NeonFoodMap** as a suitable project for practicing application deployment on AWS.

* Analyze the requirements of the NeonFoodMap system and identify the components that need to be deployed on AWS.

* Finalize the NeonFoodMap deployment architecture diagram, identifying the relationships between Frontend, Backend, Database, Storage, Containers, and AWS services.

* Build an overview diagram for the **Source Code → GitHub Actions → Docker Build → Amazon ECR → Amazon ECS** deployment process.

### Tasks to Be Implemented During the Week:

| Day | Tasks                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Start Date | Completion Date | Reference Materials                                                                                                                                                                                                                       |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Learn about the concept of DevOps and the role of DevOps throughout the software development lifecycle.<br>- Study **Continuous Integration (CI)**, Continuous Delivery, and Continuous Deployment.<br>- Analyze the differences between CI, Continuous Delivery, and Continuous Deployment.<br>- Learn about the role of Automation and Monitoring in the DevOps process.<br>- Study an overview of the **AWS Well-Architected Framework** and its 6 pillars.                          | 29/06/2026 | 29/06/2026      | https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html                                                                                                                                                                 |
| 3   | - Learn about **GitHub Actions** and its capabilities for automating the software development process.<br>- Study the structure of Workflows using YAML files.<br>- Learn about the Workflow, Event, Job, Step, Runner, and Action components.<br>- Learn how Workflows are triggered by events in a Repository, particularly Push/Pull Request events.<br>- Explore how GitHub Actions can be used to automate Build, Test, and Deploy steps.                                            | 30/06/2026 | 30/06/2026      | https://docs.github.com/en/actions                                                                                                                                                                                                        |
| 4   | - Study the Containerization model and the role of Docker in application deployment.<br>- Learn about **Dockerfile, Docker Image, and Docker Container**.<br>- Analyze the process from Dockerfile → Docker Image → Docker Container.<br>- Write a Dockerfile for a test application.<br>- Practice building a Docker Image.<br>- Run a Container in a local environment and verify application accessibility.<br>- Learn about Docker Registry and the process of storing Docker Images. | 01/07/2026 | 01/07/2026      | https://docs.docker.com/                                                                                                                                                                                                                  |
| 5   | - Learn about **Amazon ECR** and its role in storing Docker Images on AWS.<br>- Learn about **Amazon ECS** and the ECS architecture.<br>- Study ECS components including Cluster, Task Definition, Task, and Service.<br>- Analyze the differences between ECS running on EC2 and ECS using Fargate.<br>- Study the process of building a Docker Image, pushing it to ECR, and using it with ECS.<br>- Learn about the role of CloudWatch in collecting and monitoring Container logs.    | 02/07/2026 | 02/07/2026      | https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html<br>https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html<br>https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html |
| 6   | - Survey potential projects and select **NeonFoodMap** as the Cloud deployment practice project.<br>- Work with the team to define the architecture diagram and service components for deploying NeonFoodMap on AWS.<br>- Identify the **GitHub → GitHub Actions → Docker → ECR → ECS Fargate → CloudWatch** flow as the foundation for deployment tasks in the following weeks.                                                                                                          | 03/07/2026 | 03/07/2026      | https://github.com/HaoWasabi/NeonFoodmap<br>https://docs.github.com/en/actions<br>https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html                                                                                |

### Week 2 Results:

After completing the assigned tasks, I achieved the following results:

* Understand the overview of the **AWS Well-Architected Framework** and the role of its 6 pillars in designing and evaluating Cloud architectures.

* Understand the basic principles of **DevOps** and the relationship between Development, Operations, Automation, and Monitoring.

* Distinguish between:

  * **Continuous Integration (CI)** – automatically integrating and testing changes from multiple team members.
  * **Continuous Delivery** – keeping software in a deployable state at all times.
  * **Continuous Deployment** – automatically deploying changes that have passed the required checks to the deployment environment.

* Become familiar with **GitHub Actions** and understand the basic structure of a Workflow.

* Successfully build and run a Docker Container in a local environment.

* Understand the role of **Amazon ECR** in storing and managing Docker Images.

* Understand the basic architecture of **Amazon ECS**, including Cluster, Task Definition, Task, and Service.

* Understand the role of **AWS Fargate** in running Containers without directly managing EC2 servers, as well as the relationship between Docker, ECR, and ECS in the Container application deployment process.

* Understand the role of **Amazon CloudWatch** in collecting Metrics and Logs for Monitoring purposes.

* Survey and select **NeonFoodMap** as the project for practicing application deployment on AWS. Analyze the main components of NeonFoodMap, including the React Frontend, Django Backend, and Database.

* Complete the NeonFoodMap deployment architecture diagram on AWS as the foundation for the actual deployment process. Understand the overall deployment flow:

  **Developer → GitHub → GitHub Actions → Docker Build → Amazon ECR → Amazon ECS/Fargate → CloudWatch**

* Identify the tasks that need to be continued in the following weeks, including configuring IAM, VPC, ECR, ECS, CloudWatch, CI/CD, and the components required for Frontend/Backend connectivity.

* Develop foundational knowledge of the process of moving an application from **Source Code → Build → Containerize → Push Image → Deploy → Monitor** in an AWS environment.
