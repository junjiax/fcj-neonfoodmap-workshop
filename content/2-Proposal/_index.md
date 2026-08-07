---
title: "Proposal"
date: 2026-07-01
weight: 2
chapter: false
pre: "<b>2.</b>"
---

# CI/CD Pipeline Automation for the Neon Food Map Application on AWS

## 2.1. Project Background

This proposal presents a solution for deploying the NeonFoodMap system on Amazon Web Services (AWS) using a Cloud-Native architecture, addressing requirements for scalability, high availability, security, and automated software release pipelines. The goal is to build a reusable, repeatable deployment infrastructure while standardizing operational workflows following DevOps practices in a Production environment.

NeonFoodMap is a food map website platform that allows users to search, explore, and review dining locations in real time. The system integrates features such as Point of Interest (POI) search, GPS positioning, route display, location reviews, and Text-to-Speech audio descriptions to enhance the user experience. Given its real-time data processing nature and the need to serve concurrent users, the system must be deployed on an infrastructure that supports flexible scaling, high availability, and ease of maintenance.

The proposal focuses on building a deployment architecture using Docker and Amazon ECS Fargate, managing source code with GitHub, automating the Build–Test–Deploy pipeline through GitHub Actions and OpenID Connect (OIDC), storing Docker Images on Amazon ECR, deploying Amazon RDS databases in a Private Subnet, managing static assets with Amazon S3, and monitoring the system with Amazon CloudWatch. The solution aims to establish a unified, secure, and scalable deployment pipeline for future development phases of the project.

---

## 2.2. Problem Statement
### Current State

Before implementing this proposal, the NeonFoodMap Website project existed only as standalone application source code (Frontend and Backend), without a standardized deployment process or cloud infrastructure integration. Specifically:

* **No automation infrastructure:** The build and deploy process is performed manually with no automated CI/CD pipeline established for the Production environment.
* **No containerization model:** The application has not been packaged as a standardized Docker Image to ensure consistent operation across environments.
* **No AWS infrastructure configured:** The VPC network, distributed database, optimized IAM security policies, and monitoring/logging mechanisms on AWS have not been built or configured in a synchronized manner.

---

## 2.3. Deployment Objectives

The proposal targets the following technical goals:

- Automate the Build, Test, and Deploy pipeline.
- Eliminate the use of AWS Access Keys in GitHub through OpenID Connect (OIDC).
- Standardize the application deployment process using the Container model.
- Ensure High Availability for the system.
- Support flexible resource scaling based on load demand.
- Establish centralized monitoring, logging, and alerting mechanisms.
- Standardize the deployment process following the DevOps model and improve reusability.

## 2.4. Solution

- Design AWS infrastructure architecture.
- Build the CI/CD pipeline.
- Deploy Backend and Frontend using Amazon ECS Fargate.
- Manage Docker Images.
- Configure the database.
- Manage Static Assets.
- Build a Logging and Monitoring system.
- Complete deployment documentation per Sprint.

---

## 2.6. Expected Outcomes

Upon completing the deployment, the system is expected to achieve the following results:

- A complete deployment architecture on AWS following the Cloud-Native model.
- An automated CI/CD pipeline operating end-to-end from Build to Deploy.
- Application deployed using Amazon ECS Fargate.
- Docker Images centrally managed on Amazon ECR.
- Database securely deployed within a Private Subnet.
- System monitored through Logging, Monitoring, and Alerting mechanisms.
- A standardized, scalable, and reusable deployment process for similar future projects.

## 2.7. Return on Investment

Standardizing and automating the system delivers tangible value:

- **Cost Efficiency:** The Serverless model (ECS Fargate) and Serverless Storage ensure payment only for actual resources used, minimizing idle infrastructure waste.

- **Time-to-Market:** The automated CI/CD pipeline reduces the time to release new features from hours/days down to just minutes.

- **High Availability:** Self-healing infrastructure and load balancing help the system achieve high uptime and minimize service downtime.

- **Better Security & Control:** AWS security standards combined with proactive monitoring protect customer data and enable early detection of potential vulnerabilities.

---

## 2.8. Solution Architecture

![](/images/2-Proposal/diagram1.png)

### List of AWS Services Used

The table below lists the AWS services used for the project:

| AWS Service                         | Service Type                   | Role & Function in the System                                                                                                                                          |
| ----------------------------------- | ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AWS IAM**                         | Identity & Access Management   | Manages users, groups, roles, and security policies; enforces Force MFA policy for all accounts.                                                                       |
| **VPC**                             | Networking                     | Provides a Virtual Private Cloud with CIDR blocks, public and private Subnets, Route Tables, Internet Gateway, and NAT Gateways.                                       |
| **Amazon RDS**                      | Relational Database            | Hosts the relational database (RDS MySQL Multi-AZ) to store and manage application data.                                                                               |
| **Amazon S3**                       | Object Storage                 | Stores files in dedicated buckets (frontend, media, audio, logs) with versioning, lifecycle policies, and encryption configurations.                                   |
| **Amazon ECR**                      | Container Registry             | Repository for Docker Container Images for both Frontend and Backend.                                                                                                  |
| **Amazon ECS**                      | Container Orchestration        | Manages the cluster running the application using the Fargate launch type.                                                                                             |
| **Application Load Balancer (ALB)** | Load Balancing                 | Distributes HTTP/HTTPS internet traffic to target groups and supports redirect configuration and health checks.                                                        |
| **Amazon CloudWatch**               | Monitoring & Observability     | Collects logs (CloudWatch Logs), tracks metrics, and sets up dashboards and alarms.                                                                                    |
| **Amazon SNS**                      | Push Notification Service      | Sends alert notifications (e.g., billing alerts for costs) to administrators.                                                                                          |
| **AWS CloudFront**                  | Content Delivery Network (CDN) | Distributes content globally, accelerates frontend access, and caches audio files.                                                                                     |

---

## 2.9. System Deployment Flow

1. Developer pushes source code.
2. GitHub Actions triggers the workflow.
3. Build Docker Image.
4. Authenticate via AWS STS.
5. Push Image to Amazon ECR.
6. ECS pulls the Image.
7. ECS performs a Rolling Update.
8. ALB forwards the request.
9. Backend accesses RDS.
10. Media is uploaded to Amazon S3.
11. CloudWatch collects Logs.
12. SNS sends an email when an incident occurs.

---

## 2.10. Timeline & Milestones

| Phase                                             | Timeline                | Key Deliverables                                                                                                                                                                                                                                                                                                                                     |
| :------------------------------------------------ | :---------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Week 1: Research & Design**                     | 22/06/2026 - 26/06/2026 | - Study AWS Foundation (Global Infrastructure, IAM, VPC, EC2, S3).<br><br>- Design system architecture (Application, Database, Storage, Networking) and data flow diagrams.                                                                                                                                                                          |
| **Week 2: Service Research & Detailed Design**    | 29/06/2026 - 03/07/2026 | - Study RDS and the database migration process.<br><br>- Study ECS/ECR, CloudWatch, SQS, Athena, QuickSight, API Gateway, and Load Balancer.<br><br>- Finalize the deployment architecture diagram.                                                                                                                                                   |
| **Week 3: Frontend & Backend Development**        | 06/07/2026 - 10/07/2026 | - Frontend development (UI building, API integration, Responsive UI).<br><br>- Backend development (Database Schema, RESTful API, Authentication/Authorization).<br><br>- Create IAM User, security policies, and configure Billing Alerts.                                                                                                           |
| **Week 4: Foundation & Infrastructure**           | 13/07/2026 - 17/07/2026 | - Set up Multi-AZ VPC.<br><br>- Provision RDS MySQL.<br><br>- S3 Buckets + Lifecycle + IAM.<br><br>- Configure IAM (CloudFormation).<br><br>- Set up ECR + Docker.                                                                                                                                                                                   |
| **Week 5: CI/CD Pipeline & Deployment**           | 20/07/2026 - 24/07/2026 | - Build CI/CD pipeline with GitHub Actions.<br><br>- Configure ECS cluster + task definitions.<br><br>- Configure ALB + Target Groups + Health Checks.<br><br>- Configure Django on AWS.<br><br>- Configure React on AWS.                                                                                                                            |
| **Week 6-7: Scaling, Monitoring & Go-Live**       | 27/07/2026 - 07/08/2026 | - Configure ECS Services + Auto-Scaling.<br><br>- Set up CloudFront + CDN.<br><br>- Deploy CloudWatch dashboard.<br><br>- Cost Monitoring & Alerts setup.<br><br>- CloudWatch Logs + Log Insights.<br><br>- End-to-End Testing.<br><br>- Complete deployment documentation.                                                                          |

---

## 2.11. Estimated Budget

The system leverages the **AWS Free Tier** and **Serverless Pay-As-You-Go** model (paying only for actual resources used) to minimize operational costs.

| AWS Service                         | Actual Usage / Phase                                                     | Estimated Actual Cost (USD)       | Role & Function in the System                                                                                                                                      |
| ----------------------------------- | ------------------------------------------------------------------------ | --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon RDS**                      | RDS MySQL Multi-AZ (running continuously, with scaling/version migration) | **$10.00 - $15.00**               | Hosts the relational database to store and manage application data.                                                                                                |
| **Amazon S3 & ECR**                 | File storage (media, logs) and Docker Container Images                   | **$2.00 - $5.00**                 | Dedicated file storage and Docker Container Image repository for Frontend/Backend.                                                                                 |
| **Amazon ECS & NAT Gateway**        | Running container cluster (Fargate) with continuously active NAT Gateways | **$10.00 - $20.00**               | Manages the container cluster running the application and handles network routing.                                                                                 |
| **Application Load Balancer (ALB)** | Distributing HTTP/HTTPS internet traffic                                 | **$3.00 - $6.00**                 | Distributes traffic to target groups and supports health checks.                                                                                                   |
| **Amazon CloudWatch & SNS**         | Collecting logs, metrics, dashboards, and alarms                         | **$1.00 - $3.00**                 | Monitors the system, tracks metrics, and sends alert notifications via SNS.                                                                                        |
| **AWS CloudFront**                  | CDN content distribution and caching                                     | **$0.00 - $2.00**                 | Accelerates frontend access and caches audio files.                                                                                                                |
| **TOTAL ESTIMATED COST**            | **System operation & Testing**                                           | **~$26.00 - +$51.00 USD / month** | _Based on actual cost logs incurred during testing and resource configuration (actual recorded cost was approximately **$31.52 on 25/07/2026**)._ |
