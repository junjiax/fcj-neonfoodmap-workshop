---
title: "Worklog Tuần 3"
date: 2026-07-13
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

**Nhiệm vụ cá nhân:** Phân tích yêu cầu và hoàn thiện phương án triển khai dự án NeonFoodMap trên AWS, đồng thời tìm hiểu các dịch vụ AWS cần thiết cho lưu trữ, cơ sở dữ liệu, Container, Networking và phân phối lưu lượng.

Trong tuần 3, em tập trung phân tích kiến trúc NeonFoodMap, lựa chọn các dịch vụ AWS phù hợp và chuẩn bị ứng dụng cho quá trình triển khai.

Các mục tiêu chính trong tuần:

- Tìm hiểu **Amazon RDS** và mô hình triển khai cơ sở dữ liệu quan hệ trên AWS.
- Tìm hiểu **Amazon ECR** và **Amazon ECS/Fargate** phục vụ triển khai Container.
- Tìm hiểu **Application Load Balancer (ALB)** và vai trò phân phối lưu lượng đến Backend Container.
- Tìm hiểu **Amazon S3** để lưu trữ Object và tài nguyên tĩnh.
- Tìm hiểu vai trò của **CloudFront** và **API Gateway** trong kiến trúc hệ thống.
- Phân tích kiến trúc NeonFoodMap gồm **React Frontend, Django Backend và Database**.
- Kiểm tra **Environment Variables, API Endpoint, Database Connection và CORS**.
- Xác định các thành phần AWS cần thiết và mối quan hệ giữa chúng.
- Chuẩn bị luồng triển khai **CI/CD**: **GitHub → GitHub Actions → Docker → ECR → ECS/Fargate**.

### Các công việc cần triển khai trong tuần:

| Thứ | Công việc                                                                                                                                                                                                                                                 | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                                                                                                                                    |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Lựa chọn **NeonFoodMap** làm dự án triển khai trên AWS.<br>- Xác định phạm vi và yêu cầu triển khai.<br>- Phân tích kiến trúc hiện tại và xác định các thành phần Frontend, Backend, Database, Storage và Networking.                                   | 06/07/2026   | 06/07/2026      |                                                                                                                                                                                                                       |
| 3   | - Phân tích chức năng và kiến trúc chính của NeonFoodMap.<br>- Rà soát **React Frontend, Django Backend và Database**.<br>- Kiểm tra Environment Variables, API Endpoint, Database Configuration và CORS trước khi triển khai.                            | 07/07/2026   | 07/07/2026      |                                                                                                                                                                                                                       |
| 4   | - Thiết kế kiến trúc triển khai trên AWS.<br>- Lựa chọn **Amazon VPC, ECS/Fargate, ECR, RDS, S3, CloudFront và Application Load Balancer**.<br>- Nghiên cứu khả năng sử dụng API Gateway.                                                                 | 08/07/2026   | 08/07/2026      | https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html<br>https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html<br>https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html |
| 5   | - Xây dựng phương án triển khai **CI/CD**.<br>- Chuẩn bị GitHub Repository và phương án quản lý Source Code.<br>- Xác định luồng GitHub Actions, Docker, ECR và ECS/Fargate.<br>- Xây dựng phương án quản lý Environment Variables và thông tin nhạy cảm. | 09/07/2026   | 09/07/2026      | https://docs.github.com/en/actions<br>https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html                                                                                                         |
| 6   | - Rà soát các dịch vụ AWS và mối quan hệ giữa các thành phần.<br>- Chuẩn bị Repository, Docker configuration và môi trường phát triển cho các nhiệm vụ tiếp theo.                                                                                         | 10/07/2026   | 10/07/2026      |                                                                                                                                                                                                                       |

### Kết quả đạt được tuần 3:

Sau khi hoàn thành các nhiệm vụ được giao, em đạt được các kết quả sau:

- Xác định **NeonFoodMap** là dự án phù hợp để thực hành triển khai Cloud trên AWS.

- Phân tích được các thành phần chính gồm **React Frontend, Django Backend và Database**.

- Hiểu vai trò của **Amazon RDS, Amazon S3, Amazon ECR, ECS/Fargate và Application Load Balancer**.

- Hoàn thiện kiến trúc AWS tổng thể gồm:
  - **Amazon VPC** cho Networking.
  - **Amazon ECS/Fargate** cho triển khai Container.
  - **Amazon ECR** cho lưu trữ Docker Image.
  - **Amazon RDS** cho Database.
  - **Amazon S3** cho lưu trữ Object và tài nguyên tĩnh.
  - **Amazon CloudFront** cho phân phối tài nguyên Frontend.
  - **Application Load Balancer** cho phân phối lưu lượng đến Backend.
  - **Amazon CloudWatch** cho Monitoring và Logging.

- Xác định các cấu hình quan trọng như API Endpoint, Database Connection, CORS và Environment Variables.

- Xây dựng luồng triển khai CI/CD:

  **Source Code → GitHub → GitHub Actions → Docker Build → Amazon ECR → ECS/Fargate**

- Chuẩn bị môi trường phát triển, Source Code và các cấu hình cần thiết để triển khai AWS trong các tuần tiếp theo.
