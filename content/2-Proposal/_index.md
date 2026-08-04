---
title: "Proposal"
date: 2026-07-01
weight: 2
chapter: false
pre: "<b>2.</b>"
---

# Automating the CI/CD Pipeline for the Neon Food Map Application on AWS
## 2.1 Project Background

This proposal presents a solution for deploying the **NeonFoodMap** system on **Amazon Web Services (AWS)** using a **Cloud-Native** architecture to satisfy the requirements for scalability, high availability, security, and deployment automation. The primary objective is to establish a reusable deployment infrastructure that supports repeatable deployments while standardizing operational processes according to DevOps best practices in a production environment.

NeonFoodMap is a web-based food mapping platform that enables users to search for, discover, and review dining locations in real time. The system integrates multiple features, including Point of Interest (POI) search, GPS-based geolocation, route visualization, user reviews, and Text-to-Speech functionality to enhance the overall user experience. Due to its real-time data processing requirements and the need to support concurrent users, the application requires a cloud infrastructure capable of elastic scaling, high availability, and simplified maintenance.

This proposal focuses on designing a deployment architecture based on Docker and Amazon ECS Fargate, managing source code with GitHub, automating the Build–Test–Deploy pipeline using GitHub Actions and OpenID Connect (OIDC), storing container images in Amazon Elastic Container Registry (Amazon ECR), deploying the database on Amazon RDS within private subnets, managing static assets with Amazon S3, and monitoring the system through Amazon CloudWatch. The proposed solution aims to establish a secure, standardized, and scalable deployment workflow that can support future development and operational requirements.

---

## 2.2 Current State Assessment

Based on the current assessment, the project has not yet completed several infrastructure components and deployment processes required for running the application on AWS. The following areas remain to be implemented:

* Design the AWS infrastructure architecture.
* Build the CI/CD pipeline.
* Deploy backend and frontend services using Amazon ECS Fargate.
* Manage Docker container images.
* Configure the database.
* Manage static assets.
* Implement logging and monitoring.
* Prepare deployment documentation for each sprint.

---

## 2.3 Proposed Solution and Scope

The scope of this proposal covers the design and implementation of a complete Cloud-Native infrastructure on AWS, including:

* AWS infrastructure architecture design.
* CI/CD pipeline implementation.
* Deployment of backend and frontend services using Amazon ECS Fargate.
* Docker image management with Amazon Elastic Container Registry (Amazon ECR).
* Amazon RDS database configuration.
* Static asset management using Amazon S3.
* Logging and monitoring implementation.
* Standardization of deployment procedures and sprint documentation.

---

# 2.5 Deployment Objectives

The proposed solution aims to achieve the following technical objectives:

* Automate the Build, Test, and Deploy processes.
* Eliminate the use of long-term AWS Access Keys in GitHub by adopting OpenID Connect (OIDC).
* Standardize application deployment using container-based architecture.
* Ensure high availability of the system.
* Support elastic resource scaling based on workload demands.
* Establish centralized logging, monitoring, and alerting mechanisms.
* Standardize the deployment workflow according to DevOps practices while improving reusability.

---

# 2.6 Expected Outcomes

Upon completion of the implementation, the project is expected to achieve the following outcomes:

* A fully implemented Cloud-Native deployment architecture on AWS.
* A fully automated CI/CD pipeline from Build to Deploy.
* Successful deployment of the application using Amazon ECS Fargate.
* Centralized Docker image management through Amazon Elastic Container Registry (Amazon ECR).
* Secure database deployment within private subnets using Amazon RDS.
* Comprehensive system observability through centralized logging, monitoring, and alerting.
* A standardized, scalable, and reusable deployment process applicable to future cloud-native projects.
