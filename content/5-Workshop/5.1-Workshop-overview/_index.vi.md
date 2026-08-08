---

title: "Introduction"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
----------------------

# 5.1. Overview

# Cloud & DevOps Problem: Deploying the System to AWS Cloud and Building an Automated CI/CD Pipeline

#### To meet the requirements for flexible deployment, software release process automation, and improved system availability, this project deploys the application on the Amazon Web Services (AWS) platform and builds a fully automated CI/CD (Continuous Integration/Continuous Deployment) pipeline. The Cloud & DevOps architecture of the system is organized into three main processing flows, including: the CI/CD flow, the user request flow, and the monitoring and cost management flow.

## 5.1.1. CI/CD Flow (Pipeline Flow)

The continuous integration and deployment process is designed to automate the entire workflow from the moment a developer updates the source code until the new version of the application is deployed to the production environment. Specifically, when a Developer pushes code to the GitHub repository, GitHub Actions is triggered to start the pipeline. The pipeline uses OIDC (OpenID Connect) authentication to establish a connection with AWS Security Token Service (STS) and obtain temporary credentials, replacing the use of static Access Key/Secret Key credentials in order to enhance security. After successful authentication, the pipeline builds the application's Docker image and pushes the image to Amazon Elastic Container Registry (ECR). Next, Amazon ECS Fargate automatically pulls the latest image from ECR and deploys the new version of the application without manual intervention.

* Processing flow:
  Developer → GitHub → GitHub Actions → OIDC Authentication → AWS STS → Amazon ECR → Amazon ECS Fargate.

## 5.1.2. User Flow (Request Flow)

The request processing flow is designed based on a content distribution and load balancing model to ensure system access performance and fault tolerance.
When a user sends an access request, the request is first received by Amazon CloudFront – AWS's Content Delivery Network (CDN). For static frontend resources, CloudFront retrieves the content directly from the Amazon S3 Frontend Bucket. For dynamic requests, CloudFront forwards the requests to the Application Load Balancer (ALB). The ALB distributes incoming traffic to ECS Fargate tasks running across two different Availability Zones (AZs) to ensure High Availability. The application containers connect to the Amazon RDS Primary instance located in Zone A to perform data read/write operations. At the same time, data is continuously replicated to the RDS Standby instance in Zone B using the Multi-AZ mechanism, allowing the system to perform failover in the event of a failure.
In addition, ECS containers access the S3 Media Bucket through a VPC Endpoint, allowing data to be transmitted internally within the AWS network without going through the public Internet, thereby enhancing security and optimizing data transfer costs.

* Processing flow:
  User → CloudFront → (S3 Frontend or ALB) → ECS Fargate (2 AZ) → RDS Primary (Zone A) → RDS Standby (Zone B)

## 5.1.3. Monitoring & Cost Flow (Observability & Billing)

To ensure stable system operation and effectively control cloud resource usage costs, the project implements an automated monitoring and alerting mechanism based on AWS management services. All system logs, including VPC Flow Logs and Application Logs, are collected and centralized in Amazon CloudWatch for monitoring, analysis, and troubleshooting. The system is also configured with Auto Scaling for the ECS service, allowing the number of tasks to be automatically increased when CPU or Memory utilization exceeds 70%, thereby maintaining performance under increased workloads.
For cost management, the system uses AWS Budgets with a budget set at USD 15/month. Alert thresholds are configured at 50%, 70%, and 90% of the budget. When costs reach these thresholds or abnormal cost increases are detected, AWS Budgets automatically triggers Amazon SNS (Simple Notification Service) to send email alerts to administrators, supporting early risk detection and timely corrective actions.

* Monitoring and alerting flow:
  CloudWatch (Logs & Metrics) → Auto Scaling → AWS Budgets → Amazon SNS → Email Alert

## 5.1.4. System Architecture

### Overall Architecture

![](/images/2-Proposal/diagram1.png)

#### The system architecture is divided into five main layers:

#### CI/CD Layer

* GitHub Repository
* GitHub Actions
* Docker Build
* AWS STS
* Amazon ECR

This layer is responsible for automating the entire deployment process. After each push to the main branch:

1. The Source Code is Built.
2. A Docker Image is Created.
3. GitHub uses OIDC for authentication.
4. AWS STS issues Temporary Credentials.
5. The Image is Pushed to Amazon ECR.
6. The ECS Service performs a Rolling Deployment.

---

#### Presentation Layer

Includes:

* Amazon CloudFront
* Amazon S3 Static Website

The frontend is hosted on Amazon S3 and distributed through CloudFront in order to:

* Reduce latency
* Accelerate access
* Reduce Backend load

---

#### Application Layer

Includes:

* Application Load Balancer
* Amazon ECS Cluster
* Backend Service
* Frontend Service

The application is deployed on ECS Fargate, eliminating the need to manage EC2 instances. Services operate independently, allowing:

* Independent scaling of each component
* Rolling Updates
* Automatic restart in case of failure

---

#### Data Layer

Includes:

* Amazon RDS MySQL
* Multi-AZ Deployment

The database is deployed in a Private Database Subnet.

Using Multi-AZ provides:

* Increased fault tolerance
* Automatic Failover
* Reduced service interruption time

---

#### Monitoring Layer

Includes:

* Amazon CloudWatch
* Amazon SNS

CloudWatch collects:

* ECS Logs
* Container Logs
* Metrics
* Application Logs

SNS is responsible for sending Email Alerts when anomalies are detected.

---

### ECS Deployment Architecture

![](/images/2-Proposal/diagram2.png)

The system uses one ECS Cluster consisting of two services:

#### Backend Service

Deployed using:

* Django REST API
* Docker Container
* ECS Fargate

The Backend is responsible for:

* Authentication
* Business Logic
* Database Access
* Media Upload

---

#### Frontend Service

Deployed using:

* React Application
* Docker Container
* ECS Fargate

The Frontend communicates with the Backend through the ALB.

---

#### Service Discovery

AWS Cloud Map is used to manage Service Discovery between Containers within the ECS Cluster.

---

#### Load Balancing

The Application Load Balancer receives HTTP Requests/HTTPS Requests and then routes them to the Backend Service.

---

## 5.1.5. AWS Services Used

| Service                 | Purpose                                                                                                                                                                                                                                                        |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| IAM                     | Manages identities and access permissions for AWS resources. Creates Users, Groups, Roles, and Policies to control which users or services are allowed to perform specific operations according to the **Least Privilege** principle.                          |
| STS                     | Provides **Temporary Security Credentials** (Access Key, Secret Key, Session Token) with a short validity period for users or applications. Used in GitHub Actions (OIDC), Assume Role, and secure AWS access scenarios without storing long-term access keys. |
| VPC                     | Builds a virtual private network on AWS, allowing the definition of IP address ranges, routing tables, ACLs, and Security Groups to isolate and protect the application deployment infrastructure.                                                             |
| Public / Private Subnet | Divides the infrastructure into network zones with different levels of access. Public Subnets contain resources that require Internet access (ALB, NAT Gateway), while Private Subnets contain internal resources (ECS, RDS) to enhance security.              |
| NAT Gateway             | Allows resources in Private Subnets to access the Internet for outbound traffic in order to download packages, update systems, or pull Docker Images, while preventing direct inbound connections from the Internet.                                           |
| Internet Gateway        | Connects the VPC to the Internet, allowing resources in Public Subnets to send and receive network traffic from external sources for website access and public services.                                                                                       |
| ECS Fargate             | A serverless container runtime platform that eliminates the need to manage servers. It automatically provisions infrastructure, deploys, and scales Docker-based container applications, reducing operational and management overhead.                         |
| ECR                     | A private Docker Image repository on AWS. Stores and manages image versions and provides Images to ECS during application deployment or updates through the CI/CD process.                                                                                     |
| RDS MySQL               | A fully managed relational database service. Stores application data and supports automated backups, Multi-AZ, monitoring, and scalability to ensure system availability and reliability.                                                                      |
| S3                      | An object storage service used to store static websites (React), images, user files, system logs, backup files, and other static resources with high durability and scalability.                                                                               |
| CloudFront              | A Content Delivery Network (CDN) that distributes content from S3 or ALB through Edge Locations worldwide, reducing latency, improving loading speed, and supporting HTTPS, caching, and application protection.                                               |
| ALB                     | Provides HTTP/HTTPS load balancing for multiple containers or servers. Routes requests based on URL, Host Header, or Path to the corresponding ECS Services, while also supporting Health Checks and SSL/TLS.                                                  |
| CloudWatch              | Monitors AWS resources and applications through Metrics, Logs, Dashboards, and Alarms. Collects logs from ECS, monitors system performance, detects issues, and supports troubleshooting and error analysis.                                                   |
| SNS                     | A notification service based on the Publish/Subscribe model. Automatically sends Email, SMS, or triggers other services when CloudWatch Alarms or AWS events are activated.                                                                                    |
| Secrets Manager         | Securely stores and manages sensitive information such as database passwords, API Keys, and Access Tokens. Supports KMS encryption, access control, and automatic Secret Rotation to enhance security.                                                         |

---
