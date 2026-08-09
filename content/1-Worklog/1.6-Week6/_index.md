---
title: "Week 6 Worklog"
date: 2026-07-27
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

**Personal Tasks:** Set up a monitoring and log management system for the application's components on AWS, focusing on Amazon CloudWatch.

During Week 6, I worked on improving system observability through CloudWatch to monitor operational status, inspect application logs, and support the detection and analysis of issues that may occur during operation.

The main objectives for the week were:

* Check the operational status of the components deployed on AWS and identify the information that needs to be monitored.
* Learn about the operation of **Amazon CloudWatch**, particularly Metrics, Logs, Dashboards, and Logs Insights.
* Configure a **CloudWatch Dashboard** to centralize important information about the system's status and performance.
* Configure **CloudWatch Log Groups** and Log Streams for storing, categorizing, and monitoring logs.
* Check the ability to collect logs from Containers running on Amazon ECS.
* Use **CloudWatch Logs Insights** to query, filter, and analyze application logs.
* Test the system after configuring the monitoring components.
* Detect, analyze, and resolve issues related to log configuration, IAM permissions, or the log collection process if they occur.
* Complete the monitoring configuration documentation and procedures, providing a foundation for subsequent testing and operations.

### Tasks to Be Implemented During the Week:

| Day | Tasks                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Start Date | Completion Date | Reference Materials                                                                                                                                                  |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Receive the requirements and analyze the scope of work.<br>- Check the AWS components deployed from previous Sprints and identify the resources that need to be monitored.<br>- Identify the Metrics and Logs that need to be collected to monitor the operational status of the system.<br>- Learn about the operation of CloudWatch Dashboard, CloudWatch Logs, and CloudWatch Logs Insights.                                                                                                                                                                                   | 27/07/2026 | 27/07/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html                                                                                 |
| 3   | - Check the operating environment and status of the relevant AWS services.<br>- Check the status of the ECS Cluster, ECS Service, and ECS Task.<br>- Check the Metrics provided by AWS to determine the operational status of the system.<br>- Create and configure a **CloudWatch Dashboard**.<br>- Add the necessary charts and Metrics to the Dashboard to centralize system monitoring.<br>- Check whether the Dashboard can update data according to the actual status of the resources.                                                                                       | 28/07/2026 | 28/07/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Dashboards.html                                                                            |
| 4   | - Test system operation after configuring the Dashboard.<br>- Monitor Metrics to detect abnormal resource states.<br>- Confirm that all components requiring monitoring are properly displayed on the CloudWatch Dashboard.                                                                                                                                                                                                                                                                                                                                                         | 29/07/2026 | 29/07/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitoring-services.html                                                                              |
| 5   | - Create and configure **Amazon CloudWatch Log Groups** for the services that need to be monitored.<br>- Check the Log Streams created while the Containers are running.<br>- Check the `awslogs` configuration in the ECS Task Definition.<br>- Check the IAM permissions required for ECS Tasks to send logs to CloudWatch.<br>- Launch and test the Container to generate sample logs.<br>- Check that logs are successfully recorded and fully displayed in CloudWatch Logs.<br>- Use **CloudWatch Logs Insights** to query, filter, and search log records by time or content. | 30/07/2026 | 30/07/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html<br>https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html |
| 6   | - Check the CloudWatch Dashboard and confirm that the Metrics are displayed correctly.<br>- Check the logs of Containers and services in CloudWatch Logs.<br>- Use Logs Insights queries to verify the ability to search and analyze logs.<br>- Check the ability to detect errors through Metrics and Logs.<br>- Resolve issues related to Dashboard, Log Group, Log Stream, or IAM Permission configurations if any occur.<br>- Complete the configuration documentation and summarize the results.                                                                               | 31/07/2026 | 31/07/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html                                                                                 |

### Week 6 Results:

After completing the assigned tasks, I achieved the following results:

* Gained a better understanding of AWS resource monitoring through **Amazon CloudWatch**.
* Successfully configured a **CloudWatch Dashboard** to centralize monitoring of important system Metrics.
* Learned how to select and add appropriate Metrics to the Dashboard for monitoring the operational status of resources.
* Tested the Dashboard and confirmed that the data was updated according to the actual system status.
* Successfully implemented a log collection and management system using **Amazon CloudWatch Logs**.
* Created and configured **Log Groups** for categorizing and storing application logs.
* Checked **Log Streams** and confirmed that logs from Containers were successfully recorded.
* Checked the ECS Task Definition configuration and IAM Permissions related to sending logs to CloudWatch.
* Used **CloudWatch Logs Insights** to query and analyze application logs.
* Understood the differences and relationships between **CloudWatch Metrics, CloudWatch Dashboard, and CloudWatch Logs** in the system monitoring process.
* Ensured that the deployment environment was capable of **monitoring operational status, collecting logs, and supporting incident analysis**, providing a foundation for subsequent tasks related to Load Balancers, routing, and system completion.
