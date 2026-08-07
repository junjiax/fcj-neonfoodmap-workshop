---
title : "Tạo ECS cluster và service"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b> 5.4.8. </b> "
---

### 5.4.8. Tạo ECS Cluster và Service

Sau khi hoàn thành phần này, hệ thống sẽ đáp ứng các yêu cầu sau:

- Tạo thành công ECS Cluster sử dụng **AWS Fargate**
- Triển khai Cluster trên **2 Availability Zones (AZ1, AZ2)** nhằm tăng tính sẵn sàng
- Tạo Task Definition cho Backend và Frontend
- Cấu hình CloudWatch Logs cho các Container
- Thiết lập biến môi trường và Secrets cho ứng dụng
- Cấu hình IAM Task Execution Role có quyền truy cập Amazon ECR
- Kiểm tra Task khởi chạy và hoạt động bình thường

---

## Các bước thực hiện



![](/images/5-Workshop/5.4-Neon-Deployment/image039.png)
![](/images/5-Workshop/5.4-Neon-Deployment/image040.png)
![](/images/5-Workshop/5.4-Neon-Deployment/image041.png)
![](/images/5-Workshop/5.4-Neon-Deployment/image042.png)
![](/images/5-Workshop/5.4-Neon-Deployment/image043.png)
