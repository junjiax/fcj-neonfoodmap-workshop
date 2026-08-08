---
title : "NeonFoodMap Deployment on AWS"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

# 5.4. NeonFoodMap Deployment on AWS
---

### Objectives

In this phase, the NeonFoodMap project will be automatically deployed and containerized on AWS infrastructure through a clear, sequential, end-to-end workflow that can be verified at each stage.

### Overview

The implementation process consists of the following steps:

1. Prepare the source code and CI/CD workflow
2. Create the IAM stack using CloudFormation
3. Configure Secrets and Variables on GitHub
4. Create ECR repositories
5. Create the ECS cluster, task definitions, and services
6. Create the ALB and routing rules
7. Verify health checks and perform smoke tests
8. Clean up resources after completion

### Deployment Summary

After completing the above steps, the system is ready to operate on AWS following a production-like workflow:

* Code is tested through CI
* Images are built and pushed to ECR
* ECS services run on Fargate
* ALB distributes traffic to the frontend and backend through the correct routes
* Smoke tests confirm that the system can handle basic requests

---
