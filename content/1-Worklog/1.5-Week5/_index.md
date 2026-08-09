---
title: "Week 5 Worklog"
date: 2026-07-20
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

**Personal Tasks:** Deploy a Container runtime environment on Amazon ECS using AWS Fargate and prepare the Frontend for deployment on AWS.

During Week 5, I worked on deploying an ECS Cluster, configuring the Task Definition, building a Docker Image for the Frontend, storing the Image on Amazon ECR, and configuring CloudWatch Logs to monitor the application.

The main objectives for the week were:

- Learn about the architecture and operation of **Amazon ECS**, including **ECS Cluster**, **Task Definition**, **Task**, and **ECS Service**.
- Create an **ECS Cluster** using AWS Fargate as the Container runtime environment.
- Learn about and configure an **ECS Task Definition** for the Frontend.
- Configure Container parameters such as CPU, Memory, Container Port, Docker Image, and Environment Variables.
- Build a **Dockerfile** for the React Frontend application and test the build process and Container execution in a local environment.
- Build a Docker Image and push the Image to **Amazon Elastic Container Registry (ECR)**.
- Configure **CloudWatch Logs** to collect logs from Containers running on ECS.
- Verify the ability to use a Docker Image from ECR to launch an ECS Task.
- Test and troubleshoot issues related to Docker Images, Port Mapping, Environment Variables, and Log Configuration.

### Tasks to Be Implemented During the Week:

| Day | Tasks                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Start Date | Completion Date | Reference Materials                                                                                                                                                                                                                                 |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Receive the requirements and analyze the expected results of each task to identify the requirements that need to be completed.<br>- Identify the relationship between Frontend, Docker, ECR, and ECS in the deployment architecture.<br>- Learn about the components of Amazon ECS, including Cluster, Task Definition, Task, and Service.<br>- Identify the parameters that need to be configured for the Frontend Container, such as CPU, Memory, Port, and Environment Variables.                                                                                                  | 20/07/2026 | 20/07/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html                                                                                                                                                                            |
| 3   | - Create an **ECS Cluster** using AWS Fargate.<br>- Learn about the configuration required for ECS Tasks to run within the specified VPC and Subnets.<br>- Create a **Task Definition for the Frontend**.<br>- Define the Docker Image, CPU, Memory, and Container Port in the Task Definition.<br>- Configure the IAM Task Execution Role for pulling Images from ECR and sending logs to CloudWatch.<br>- Configure the CloudWatch Log Group and Log Configuration for the Container.                                                                                                 | 21/07/2026 | 21/07/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html<br>https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html<br>https://docs.aws.amazon.com/AmazonECS/latest/developerguide/using_awslogs.html |
| 4   | - Check the structure and development environment of the React application.<br>- Identify the Frontend application build process for running in a Container environment.<br>- Create a **Dockerfile** for the Frontend.<br>- Build a Docker Image from the React source code.<br>- Run the Container in a local environment to test the application before deploying it to AWS.<br>- Check Port Mapping and application accessibility through a web browser.<br>- Tag the Docker Image according to Amazon ECR conventions and push the Image to the ECR Repository.                    | 22/07/2026 | 22/07/2026      | https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html                                                                                                                                                                             |
| 5   | - Identify and configure the Environment Variables required by the Frontend.<br>- Check the API Endpoint configuration so that the Frontend can communicate with the Backend in the deployment environment.<br>- Update the Docker Image after completing configuration changes.<br>- Check the ECS Task using the Docker Image stored in ECR.<br>- Monitor the Task status on ECS and check whether the Container starts successfully.<br>- Check the Container logs recorded in Amazon CloudWatch Logs.<br>- Analyze and troubleshoot any issues that occur during Container startup. | 23/07/2026 | 23/07/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html<br>https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html                                                                   |
| 6   | - Check the ECS Cluster, Task Definition, and ECS Task status.<br>- Check the Docker Image on ECR and verify that ECS can successfully pull the Image.<br>- Check whether the Frontend Container can start and operate successfully.<br>- Check Port Mapping and Environment Variables.<br>- Check logs in CloudWatch Logs to confirm that the application is operating normally.<br>- Troubleshoot configuration issues that occur during testing.<br>- Compare the results, complete the deployment documentation, and summarize the implementation results.                          | 24/07/2026 | 24/07/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html<br>https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html                                                                                                 |

### Week 5 Results:

After completing the assigned tasks, I achieved the following results:

- Successfully created an **Amazon ECS Cluster** using **AWS Fargate**.
- Understood the role of an ECS Cluster in managing Container Tasks.
- Created and configured a **Task Definition for the Frontend**, including the following parameters:
  - Docker Image.
  - CPU.
  - Memory.
  - Container Port.
  - Environment Variables.
  - IAM Task Execution Role.
  - CloudWatch Log Configuration.

- Completed the **Dockerfile** for the Frontend and performed the Docker Image Build process.
- Tested the Docker Image in a local environment before deploying it to AWS.
- Created and used an **Amazon ECR Repository** to store the Frontend Docker Image.
- Successfully performed the **Build → Tag → Push Docker Image to ECR** process.
- Configured the ECS Task to use the Docker Image stored in ECR.
- Configured **Amazon CloudWatch Logs** to collect and monitor logs from the Frontend Container.
- Checked the ECS Task status and confirmed that the Container could start successfully with the configured settings.
- Checked and adjusted Environment Variables, Port Mapping, and Container parameters during the deployment process.
- Gained a better understanding of the relationship between **Docker → ECR → ECS Fargate → CloudWatch Logs** in the process of deploying Container applications on AWS.
- Completed the deployment documentation and established a foundation for further integration of the Frontend with the Backend, ECS Service, and networking components in subsequent tasks.
