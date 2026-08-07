---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# NeonFoodMap - Deploying a Cloud-Native Application on AWS

#### Overview

This workshop walks you through the end-to-end process of building, deploying, and operating **NeonFoodMap** - a food and tourism map application - on Amazon Web Services (AWS). The project follows a modern Cloud & DevOps approach with a fully automated CI/CD pipeline, multi-AZ high availability, and comprehensive observability.

The workshop is divided into four main phases:

- **Infrastructure**: Set up the foundational AWS network and services (VPC, RDS, S3, IAM)
- **Deployment**: Build a CI/CD pipeline using GitHub Actions and deploy the application to ECS Fargate
- **Operations**: Configure auto-scaling, CDN distribution, monitoring, cost alerts, and end-to-end testing
- **Image Assets**: Reference list of all screenshots used throughout the workshop

#### Architecture Summary

The system is structured into five layers:

| Layer | Components |
|-------|------------|
| CI/CD | GitHub Actions, OIDC, AWS STS, Amazon ECR |
| Presentation | Amazon CloudFront, Amazon S3 (Frontend) |
| Application | Application Load Balancer, Amazon ECS Fargate |
| Data | Amazon RDS MySQL (Multi-AZ) |
| Monitoring | Amazon CloudWatch, Amazon SNS, AWS Budgets |

#### Contents

1. [Workshop Overview](5.1-Workshop-overview/)
2. [Prerequisites](5.2-Prerequiste/)
3. [Design and Build NeonFoodMap Infrastructure on AWS](5.3-Neon-Infrastructure/)
4. [NeonFoodMap Deployment on AWS](5.4-Neon-Deployment/)
5. [NeonFoodMap Operations and Monitoring](5.5-Neon-Operations/)
6. [Image Assets](5.6-Neon-Image/)