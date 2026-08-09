---
title: "Worklog Tuần 2"
date: 2026-06-29
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

---

### Mục tiêu tuần 2:

**Nhiệm vụ cá nhân:** Xây dựng kiến thức nền tảng về DevOps, CI/CD, Container và các dịch vụ AWS phục vụ quá trình triển khai ứng dụng; đồng thời khảo sát và hoàn thiện kiến trúc triển khai cho dự án NeonFoodMap.

Trong tuần 2, em tập trung tìm hiểu quy trình đưa một ứng dụng từ môi trường phát triển lên môi trường Cloud theo hướng tự động hóa. Nội dung học tập kết hợp giữa kiến thức về **AWS Well-Architected Framework, DevOps, CI/CD, Docker, Amazon ECR, Amazon ECS, GitHub Actions và Amazon CloudWatch**.

Các mục tiêu chính trong tuần:

- Tìm hiểu **AWS Well-Architected Framework** và 6 trụ cột định hình kiến trúc AWS:
  - Operational Excellence.
  - Security.
  - Reliability.
  - Performance Efficiency.
  - Cost Optimization.
  - Sustainability.

- Hiểu vai trò của Well-Architected Framework trong việc đánh giá và thiết kế kiến trúc Cloud theo các tiêu chí về vận hành, bảo mật, độ tin cậy, hiệu năng và chi phí.
- Tìm hiểu quy trình **DevOps** và sự phối hợp giữa Development và Operations trong quá trình phát triển, triển khai và vận hành phần mềm.
- Phân biệt **Continuous Integration (CI), Continuous Delivery (CD) và Continuous Deployment**.
- Tìm hiểu vai trò của **Monitoring** trong việc theo dõi trạng thái, hiệu năng và lỗi của ứng dụng sau khi triển khai.
- Tìm hiểu **Docker** và mô hình Containerization nhằm đóng gói ứng dụng cùng các thành phần phụ thuộc thành một đơn vị triển khai nhất quán.
- Nghiên cứu các thành phần cơ bản của Docker:
  - Dockerfile.
  - Docker Image.
  - Docker Container.
  - Docker Registry.

- Thực hành build Docker Image và chạy Container trên môi trường local.
- Tìm hiểu **Amazon ECR** trong việc lưu trữ và quản lý Docker Image trên AWS.
- Tìm hiểu **Amazon ECS** và cách sử dụng ECS để chạy Container trên AWS.
- Tìm hiểu các khái niệm cơ bản của ECS như Cluster, Task Definition, Task và Service.
- Tìm hiểu **GitHub Actions** và cách xây dựng Workflow tự động phục vụ CI/CD.
- Nghiên cứu các thành phần của GitHub Actions như Workflow, Event, Job, Step, Runner và Action.
- Tìm hiểu cách kết hợp GitHub Actions với Docker, ECR và ECS để hình thành quy trình triển khai tự động.
- Tìm hiểu **Amazon CloudWatch** và vai trò của hệ thống Monitoring/Logging trong quá trình vận hành ứng dụng.
- Khảo sát đề tài và xác định **NeonFoodMap** là dự án phù hợp để thực hành quy trình triển khai ứng dụng trên AWS.
- Phân tích yêu cầu của hệ thống NeonFoodMap và xác định các thành phần cần triển khai trên AWS.
- Hoàn thiện sơ đồ kiến trúc triển khai NeonFoodMap, xác định mối quan hệ giữa Frontend, Backend, Database, Storage, Container và các dịch vụ AWS.
- Xây dựng sơ đồ tổng quan cho quy trình **Source Code → GitHub Actions → Docker Build → Amazon ECR → Amazon ECS**.

### Các công việc cần triển khai trong tuần:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                                                                                                                                                        |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Tìm hiểu khái niệm DevOps và vai trò của DevOps trong vòng đời phát triển phần mềm.<br>- Nghiên cứu **Continuous Integration (CI)**, Continuous Delivery và Continuous Deployment.<br>- Phân tích sự khác nhau giữa CI, Continuous Delivery và Continuous Deployment.<br>- Tìm hiểu vai trò của Automation và Monitoring trong quy trình DevOps.<br>- Nghiên cứu tổng quan về **AWS Well-Architected Framework** và 6 trụ cột của Framework.                             | 29/06/2026   | 29/06/2026      | https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html                                                                                                                                                                 |
| 3   | - Tìm hiểu **GitHub Actions** và khả năng tự động hóa quy trình phát triển phần mềm.<br>- Nghiên cứu cấu trúc Workflow sử dụng file YAML.<br>- Tìm hiểu các thành phần Workflow, Event, Job, Step, Runner và Action.<br>- Tìm hiểu cách Workflow được kích hoạt khi có sự kiện trên Repository, đặc biệt là sự kiện Push/Pull Request.<br>- Khảo sát cách sử dụng GitHub Actions để tự động hóa các bước Build, Test và Deploy.                                            | 30/06/2026   | 30/06/2026      | https://docs.github.com/en/actions                                                                                                                                                                                                        |
| 4   | - Nghiên cứu mô hình Containerization và vai trò của Docker trong triển khai ứng dụng.<br>- Tìm hiểu **Dockerfile, Docker Image và Docker Container**.<br>- Phân tích quy trình từ Dockerfile → Docker Image → Docker Container.<br>- Viết Dockerfile cho ứng dụng thử nghiệm.<br>- Thực hành build Docker Image.<br>- Chạy Container trên môi trường local và kiểm tra khả năng truy cập ứng dụng.<br>- Tìm hiểu Docker Registry và quy trình lưu trữ Docker Image.       | 01/07/2026   | 01/07/2026      | https://docs.docker.com/                                                                                                                                                                                                                  |
| 5   | - Tìm hiểu **Amazon ECR** và vai trò của ECR trong việc lưu trữ Docker Image trên AWS.<br>- Tìm hiểu **Amazon ECS** và kiến trúc ECS.<br>- Nghiên cứu các thành phần ECS gồm Cluster, Task Definition, Task và Service.<br>- Phân tích sự khác nhau giữa ECS chạy trên EC2 và ECS sử dụng Fargate.<br>- Nghiên cứu quy trình Docker Image được build, push lên ECR và sử dụng bởi ECS.<br>- Tìm hiểu vai trò của CloudWatch trong việc thu thập và theo dõi log Container. | 02/07/2026   | 02/07/2026      | https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html<br>https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html<br>https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html |
| 6   | - Khảo sát các đề tài và lựa chọn **NeonFoodMap** làm dự án thực hành triển khai Cloud.<br>- Cùng team xác định sơ đồ kiến trúc, thành phần dịch vụ triển khai NeonFoodMap trên AWS.<br>- Xác định luồng **GitHub → GitHub Actions → Docker → ECR → ECS Fargate → CloudWatch** làm cơ sở cho các nhiệm vụ triển khai trong các tuần tiếp theo.                                                                                                                             | 03/07/2026   | 03/07/2026      | https://github.com/HaoWasabi/NeonFoodmap<br>https://docs.github.com/en/actions<br>https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html                                                                                |

### Kết quả đạt được tuần 2:

Sau khi hoàn thành các nhiệm vụ được giao, em đạt được các kết quả sau:

- Hiểu được tổng quan về **AWS Well-Architected Framework** và vai trò của 6 trụ cột trong quá trình thiết kế, đánh giá kiến trúc Cloud.

- Nắm được các nguyên tắc cơ bản của **DevOps** và mối liên hệ giữa Development, Operations, Automation và Monitoring.

- Phân biệt được:
  - **Continuous Integration (CI)** – tự động tích hợp và kiểm thử thay đổi từ nhiều thành viên.
  - **Continuous Delivery** – duy trì phần mềm ở trạng thái sẵn sàng để triển khai.
  - **Continuous Deployment** – tự động đưa thay đổi đã vượt qua các bước kiểm tra vào môi trường triển khai.

- Làm quen với **GitHub Actions** và hiểu cấu trúc cơ bản của một Workflow.

- Build và chạy thành công Docker Container trên môi trường local.

- Hiểu được vai trò của **Amazon ECR** trong việc lưu trữ và quản lý Docker Image.

- Nắm được kiến trúc cơ bản của **Amazon ECS**, bao gồm Cluster, Task Definition, Task và Service.

- Hiểu được vai trò của **AWS Fargate** trong việc chạy Container mà không cần trực tiếp quản lý máy chủ EC2. Mối quan hệ giữa Docker, ECR và ECS trong quy trình triển khai ứng dụng Container.

- Nắm được vai trò của **Amazon CloudWatch** trong việc thu thập Metrics và Logs phục vụ Monitoring.

- Khảo sát và lựa chọn **NeonFoodMap** làm dự án thực hành triển khai ứng dụng trên AWS. Phân tích được các thành phần chính của NeonFoodMap gồm React Frontend, Django Backend và Database.

- Hoàn thiện sơ đồ kiến trúc triển khai NeonFoodMap trên AWS làm cơ sở cho quá trình triển khai thực tế. Nắm được luồng triển khai tổng quan:

  **Developer → GitHub → GitHub Actions → Docker Build → Amazon ECR → Amazon ECS/Fargate → CloudWatch**

- Xác định được các nội dung cần tiếp tục triển khai trong các tuần tiếp theo, bao gồm cấu hình IAM, VPC, ECR, ECS, CloudWatch, CI/CD và các thành phần phục vụ kết nối Frontend/Backend.

- Hình thành được kiến thức nền tảng về quy trình đưa một ứng dụng từ **Source Code → Build → Containerize → Push Image → Deploy → Monitor** trên môi trường AWS.
