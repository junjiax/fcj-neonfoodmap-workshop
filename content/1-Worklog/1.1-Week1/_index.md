---
title: "Week 1 Worklog"
date: 2026-06-22
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

**Personal Tasks:** Become familiar with the internship environment, build foundational knowledge of cloud computing and AWS, and practice basic operations on the AWS Management Console and AWS CLI.

During the first week, I focused on learning the fundamental knowledge required before participating in system deployment on AWS. The learning and practical activities included:

- Learning an overview of **Cloud Computing**, its characteristics, and the benefits of using computing resources over the Internet.

- Learning about Cloud service delivery models:
  - **IaaS (Infrastructure as a Service):** Provides infrastructure such as servers, networking, and storage as a service.
  - **PaaS (Platform as a Service):** Provides an environment and platform for developing and deploying applications.
  - **SaaS (Software as a Service):** Provides complete software that users can access and use over the Internet.

- Learning about **AWS**, its main service categories, and the role of AWS in providing Cloud infrastructure.

- Learning about the organization, working environment, rules, and working procedures of the **FCAJ** internship program.

- Learning about the training program, learning roadmap, and task assignment process during the internship.

- Learning about **AWS Global Infrastructure**, including:
  - Region.
  - Availability Zone.
  - How AWS organizes and distributes its infrastructure globally.

- Learning the fundamental concepts of **AWS Foundation** and the relationships between groups of Core Services.

- Becoming familiar with the **AWS Management Console**, including how to select a Region and manage AWS resources within each Region.

- Learning about the **Pay-as-you-go** pricing model, in which costs are calculated based on the actual amount of resources used.

- Learning about the **AWS Shared Responsibility Model**, distinguishing between AWS's security responsibilities and the customer's security responsibilities.

- Learning the basics of **IAM**, including Users, Groups, Roles, Policies, and the principle of **Least Privilege**.

- Becoming familiar with the **AWS CLI**, including how to configure credentials and perform resource management operations through the command line.

- Learning an overview of **Amazon EC2**, Elastic IP, and EBS.

- Learning about **Amazon VPC** and its basic components, including VPC, Subnet, Route Table, Internet Gateway, and Security Group.

- Practicing the creation and connection of EC2 instances to reinforce knowledge of Compute, Networking, and Storage on AWS.

### Tasks to Be Implemented During the Week:

| Day | Tasks                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Start Date | Completion Date | Reference Materials                                                                                                                                                                |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Learn about the objectives, content, and plan of the FCAJ internship program.<br>- Become familiar with the working environment and program members, and learn about the rules, regulations, and working procedures at the internship organization.<br>- Study an overview of Cloud Computing and the IaaS, PaaS, and SaaS service delivery models. Learn about AWS's Pay-as-you-go pricing model and Shared Responsibility Model.                                                                                                            | 22/06/2026 | 22/06/2026      | https://aws.amazon.com/what-is-cloud-computing/ https://aws.amazon.com/types-of-cloud-computing/                                                                                   |
| 3   | - Learn an overview of AWS and common Cloud service categories.<br>- Study AWS Global Infrastructure, Regions, and Availability Zones.<br>- Learn about IAM Users, Policies, Roles, and the Least Privilege principle.<br>- Become familiar with managing resources by Region through the AWS Management Console.                                                                                                                                                                                                                               | 23/06/2026 | 23/06/2026      | https://aws.amazon.com/about-aws/global-infrastructure/ <br> https://aws.amazon.com/iam/ <br> https://aws.amazon.com/console/                                                      |
| 4   | - Set up an AWS environment for learning and practical exercises.<br>- Create and configure an AWS account according to the program's instructions.<br>- Become familiar with the AWS Management Console.<br>- Learn how to select a Region and check resources in each Region.<br>- Install AWS CLI on the computer.<br>- Configure AWS CLI with credentials, Region, and other necessary settings.<br>- Execute basic CLI commands to check account information and the AWS environment.                                                      | 24/06/2026 | 24/06/2026      | https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html <br> https://cloudjourney.awsstudygroup.com/                                                                |
| 5   | - Learn the architecture and basic components of Amazon EC2.<br>- Study Instance Types, AMIs, and EBS.<br>- Learn about methods of connecting to EC2, with a focus on SSH connections.<br>- Learn about Security Groups and their role in controlling traffic to EC2.<br>- Learn about Elastic IP and its use cases when a fixed IPv4 address is required for a resource.                                                                                                                                                                       | 25/06/2026 | 25/06/2026      | https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html <br> https://cloudjourney.awsstudygroup.com/ <br> https://docs.aws.amazon.com/vpc/latest/userguide/vpc-eips.html |
| 6   | - Practice creating an EC2 Instance through the AWS Management Console.<br>- Select an appropriate AMI and Instance Type for the practical environment.<br>- Configure the Network, Subnet, and Security Group for EC2.<br>- Establish an SSH connection to the EC2 Instance.<br>- Check the status and resources of the EC2 Instance after creation.<br>- Practice attaching an EBS Volume to EC2 and verify the use of storage resources.<br>- Consolidate the knowledge learned and document the practical results achieved during the week. | 26/06/2026 | 26/06/2026      | https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html <br> https://cloudjourney.awsstudygroup.com/                                                               |

### Week 1 Results:

After completing the assigned tasks, I achieved the following results:

- Understand the concept of **Cloud Computing**, its basic characteristics, and the benefits of using Cloud infrastructure.

- Distinguish between the three service delivery models:
  - **IaaS**.
  - **PaaS**.
  - **SaaS**.

- Understand the overall concept of **AWS** and common service categories such as Compute, Storage, Networking, and Database.

- Understand the structure of **AWS Global Infrastructure**, particularly the concepts of Regions and Availability Zones.

- Understand the role of Regions in determining where resources are deployed and the role of Availability Zones in building fault-tolerant architectures.

- Understand the **Pay-as-you-go** pricing principle and the basic factors affecting AWS service costs.

- Understand the **Shared Responsibility Model**, thereby distinguishing AWS's security responsibilities for the Cloud infrastructure from the customer's responsibilities for the resources, data, and configurations they use.

- Become familiar with the basic components of **IAM**, including Users, Roles, and Policies, while understanding the principle of granting permissions according to **Least Privilege**.

- Become familiar with the **AWS Management Console** and perform basic operations to search for, configure, and manage AWS resources.

- Successfully install and configure the **AWS CLI**, including settings related to credentials and Region.

- Perform basic operations using the AWS CLI to check account information and AWS resources.

- Understand the basic architecture of **Amazon EC2**, including Instances, AMIs, EBS, Security Groups, and Elastic IPs.

- Successfully practice creating and configuring an **EC2 Instance**.

- Establish an **SSH** connection to an EC2 Instance and verify its operation.

- Practice attaching an **EBS Volume** to EC2 and checking storage resources.

- Understand the basic components of **Amazon VPC** and the relationships between VPC, Subnet, Route Table, Internet Gateway, and Security Group.

- Begin developing an AWS deployment mindset based on the combination of **Compute, Networking, Storage, and Security**.

- Become familiar with the working environment, task assignment process, and learning methods of the FCAJ internship program.

- Build the foundational knowledge and practical skills necessary to continue working with more advanced AWS services in the following weeks.
