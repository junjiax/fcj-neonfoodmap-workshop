---
title: "Week 7 Worklog"
date: 2026-07-06
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

**Personal Tasks:** Test and review the entire NeonFoodMap system after deployment on AWS, monitor its operational status, analyze logs, review costs, and complete the deployment documentation.

During Week 7, I focused on post-deployment testing and standardizing the documentation for the NeonFoodMap system. The work included:

* Continue checking the stable operation of **ECS Services** and ECS Tasks after deployment.
* Check the mechanism for maintaining the number of Tasks according to the ECS Service configuration.
* Monitor the operational status of the Backend and Frontend through the **CloudWatch Dashboard**.
* Monitor CPU, Memory, and other Metrics related to ECS Tasks/Services.
* Check Container logs through **CloudWatch Logs**.
* Use **CloudWatch Logs Insights** to query, filter, and analyze logs generated during system operation.
* Check for application errors, Container errors, or connection errors through logs and Metrics.
* Monitor the cost of AWS services during the deployment process.
* Learn about and check **Cost Monitoring & Alerts** mechanisms to detect potential unexpected costs.
* Review the entire deployment process from **Source Code → GitHub Actions → Docker Build → ECR → ECS → CloudWatch**.
* Support the team in completing and standardizing the **NeonFoodMap** deployment documentation by adding illustrations, configurations, test results, and necessary notes for each step.
* Review presentation errors, operation sequences, and configuration information in the documentation.
* Summarize the implementation results and record the items that need further improvement.

### Tasks to Be Implemented During the Week:

| Day | Tasks                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Start Date | Completion Date | Reference Materials                                                                                                                                                           |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Receive the requirements and scope of work for the week.<br>- Review the current deployment status of NeonFoodMap.<br>- Check the **ECS Cluster, ECS Service, ECS Task, and Task Definition** of the Frontend and Backend.<br>- Check the Desired Count and Running Count of the ECS Services.<br>- Check the Container status and confirm that the Tasks can start successfully and operate stably.<br>- Review the deployment process from ECR to ECS after the Docker Image has been updated.                                                    | 03/08/2026 | 03/08/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_services.html                                                                                                 |
| 3   | - Learn about the Service Auto Scaling mechanism and the components related to adjusting the number of Tasks.<br>- Check the ability to maintain the number of Tasks according to the Desired Count configuration.<br>- Monitor the CPU and Memory usage of ECS Tasks through CloudWatch Metrics.<br>- Check the CloudWatch Dashboard and add the necessary Metrics for system monitoring.<br>- Check the system status when Tasks are restarted or their status changes.                                                                             | 04/08/2026 | 04/08/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-auto-scaling.html<br>https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html |
| 4   | - Check **CloudWatch Logs** for the Frontend and Backend Containers.<br>- Check the Log Groups and Log Streams created for the corresponding ECS Tasks.<br>- Use **CloudWatch Logs Insights** to query and analyze logs.<br>- Filter logs by time range and content requiring investigation.<br>- Identify logs related to application errors, connection errors, or Container errors if any occur.                                                                                                                                                   | 05/08/2026 | 05/08/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html<br>https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html          |
| 5   | - Review the costs of AWS resources used during the NeonFoodMap deployment.<br>- Review services that may incur costs, such as ECS Fargate, RDS, NAT Gateway, Load Balancer, CloudWatch, and related services.<br>- Learn about **AWS Cost Management** and cost monitoring mechanisms.<br>- Check Cost Monitoring & Alerts notifications if they have been configured.<br>- Review unnecessary resources or resources that may generate unexpected costs.<br>- Summarize the review results and record notes related to cost management.             | 06/08/2026 | 06/08/2026      | https://docs.aws.amazon.com/cost-management/latest/userguide/what-is-costmanagement.html                                                                                      |
| 6   | - Review the entire NeonFoodMap deployment process from Source Code to the AWS environment.<br>- Check the **GitHub → GitHub Actions → Docker → ECR → ECS/Fargate → CloudWatch** workflow.<br>- Review the order of the instructions and adjust any inaccurate or inconsistent content.<br>- Add illustrations for deployment steps that are still missing.<br>- Add configuration information, test results, and notes from the implementation process.<br>- Complete the NeonFoodMap deployment documentation and summarize the internship results. | 07/08/2026 | 07/08/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html                                                                                                      |

### Week 7 Results:

After completing the assigned tasks, I achieved the following results:

* Checked and confirmed the operational status of the **ECS Cluster, ECS Service, and ECS Task** after deployment.

* Reviewed the entire NeonFoodMap deployment process following the workflow:

  **Source Code → GitHub → GitHub Actions → Docker Build → Amazon ECR → Amazon ECS/Fargate → CloudWatch**

* Practiced the post-deployment testing process following the approach of **checking status → monitoring Metrics → analyzing Logs → identifying issues → adjusting configurations → testing again**.

* Gained a more comprehensive understanding of the process of deploying a real-world application in the Cloud, from **development, containerization, CI/CD, deployment, and monitoring to cost control and documentation**.
