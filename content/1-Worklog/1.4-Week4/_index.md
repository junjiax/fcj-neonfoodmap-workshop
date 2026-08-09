---
title: "Week 4 Worklog"
date: 2026-07-13
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

**Personal Tasks:** Set up and configure Amazon S3 Buckets, S3 Objects, Lifecycle Rules, and IAM Policies/Roles related to S3 access permissions.

During Week 4, I focused on learning and deploying **Amazon Simple Storage Service (S3)** to support the storage and distribution of system resources. The activities included:

* Learn about the **Object Storage** mechanism of Amazon S3, the **Bucket – Object – Key** structure, and how data is organized in S3.
* Learn about S3 **Storage Classes** and the purpose of each class for different storage scenarios.
* Learn about **Lifecycle Rules** for automatically managing the lifecycle of Objects, including transitioning between Storage Classes or taking actions based on the storage duration.
* Learn about S3 access control through **IAM Users, IAM Policies, and IAM Roles**, while identifying the permissions required for each system component.
* Create and configure an S3 Bucket for storing system resources, particularly static resources used by the Frontend.
* Configure **Object Ownership** and Bucket security settings to prevent unauthorized access to resources.
* Test the process of uploading, storing, and retrieving Objects from S3 after completing the configuration.
* Compare the actual configuration with the system architecture to ensure that S3 can be integrated with other AWS components in subsequent tasks.
* Record the deployment results and issues encountered, and update the deployment documentation.

### Tasks to Be Implemented During the Week:

| Day | Tasks                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Start Date | Completion Date | Reference Materials                                                                                                                                                     |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Receive the tasks, requirements, and completion criteria from the supervising expert.<br>- Analyze the system architecture to determine the role of S3 and its position in the resource processing flow.<br>- Learn about the Bucket, Object, and Key structure and the basic concepts of Amazon S3.<br>- Identify the types of data that need to be stored in S3 and the access permission requirements for each type of resource.                                                                                                                                                     | 13/07/2026 | 13/07/2026      | https://aws.amazon.com/vi/s3/ <br> https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html                                                                   |
| 3   | - Create an S3 Bucket according to the task requirements.<br>- Configure the basic Bucket settings such as Region, Object Ownership, and appropriate Block Public Access settings based on the system architecture.<br>- Create and upload S3 Objects to verify data storage capabilities.<br>- Learn about and configure Lifecycle Rules to manage the lifecycle of Objects.<br>- Identify the IAM permissions required to perform operations on S3 Buckets and Objects.<br>- Verify access permissions through IAM Policies/Roles according to the system requirements.                 | 14/07/2026 | 14/07/2026      | https://docs.aws.amazon.com/AmazonS3/latest/userguide/create-bucket-overview.html <br> https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html |
| 4   | - Check the operation of the S3 Bucket after completing the configuration.<br>- Test the process of uploading, storing, and retrieving Objects.<br>- Check access permissions using IAM Roles/Policies and identify the operations that are permitted.<br>- Verify that the Lifecycle Configuration has been applied correctly according to the requirements.<br>- Analyze and troubleshoot issues related to IAM permissions or Bucket configuration if they occur.<br>- Adjust the configuration to ensure that the resources operate correctly according to the designed architecture. | 15/07/2026 | 15/07/2026      | https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html <br> https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html              |
| 5   | - Retest the entire S3 configuration after making adjustments.<br>- Verify the ability to store and retrieve Objects according to the granted permissions.<br>- Compare the actual configuration with the task requirements and completion criteria.<br>- Verify the ability to use S3 as a storage location for static resources used by the Frontend.<br>- Record the test results and confirm that the task requirements have been met.                                                                                                                                                | 16/07/2026 | 16/07/2026      | https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingObjects.html                                                                                                 |
| 6   | - Summarize the implementation results for the S3 Bucket, Object, Lifecycle, and IAM configurations.<br>- Complete the deployment, configuration, and testing documentation.<br>- Add illustrations for each implementation step.<br>- Record any errors or issues encountered during deployment and their solutions.<br>- Review the configuration to ensure consistency with the overall system architecture.<br>- Prepare the knowledge and environment for the next task.                                                                                                             | 17/07/2026 | 17/07/2026      | https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html                                                                                                      |

### Week 4 Results:

After completing the assigned tasks, I achieved the following results:

* Successfully **created and configured an S3 Bucket** according to the task requirements.
* Understood the **Object Storage** model of Amazon S3 and the relationship between Buckets, Objects, and Keys.
* Performed basic operations on S3 Objects, including uploading, checking, and retrieving data.
* Understood and configured **Object Ownership** to manage ownership of Objects stored in the Bucket.
* Understood the role of **Block Public Access** in preventing unintended public access to S3 resources.
* Learned about and configured **Lifecycle Rules** to manage the lifecycle of Objects according to storage requirements.
* Understood how to use **IAM Policies and IAM Roles** to grant permissions to components that need to interact with S3.
* Tested access permissions and confirmed that operations were performed correctly according to the configured policies.
* Successfully verified the storage of static resources on S3, establishing a foundation for integrating S3 with components supporting the Frontend and content distribution in subsequent deployment stages.
* Prepared to continue deploying the next AWS components in the system architecture.
