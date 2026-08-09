---
title: "Worklog Tuần 5"
date: 2026-07-20
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

---

### Mục tiêu tuần 5:

**Nhiệm vụ cá nhân:** Triển khai môi trường chạy Container trên Amazon ECS sử dụng AWS Fargate và chuẩn bị Frontend để triển khai trên AWS.

Trong tuần 5, em thực hiện các công việc bao gồm triển khai ECS Cluster, cấu hình Task Definition, xây dựng Docker Image cho Frontend, lưu trữ Image trên Amazon ECR và cấu hình CloudWatch Logs để theo dõi ứng dụng.

Các mục tiêu chính trong tuần:

- Tìm hiểu kiến trúc và cách hoạt động của **Amazon ECS**, **ECS Cluster**, **Task Definition**, **Task** và **ECS Service**.
- Tạo **ECS Cluster** sử dụng AWS Fargate làm môi trường chạy Container.
- Tìm hiểu và cấu hình **ECS Task Definition** cho Frontend.
- Cấu hình các thông số của Container như CPU, Memory, Container Port, Docker Image và Environment Variables.
- Xây dựng **Dockerfile** cho ứng dụng React Frontend và kiểm thử quá trình build, chạy Container trên môi trường local.
- Build Docker Image và push Image lên **Amazon Elastic Container Registry (ECR)**.
- Cấu hình **CloudWatch Logs** để thu thập log từ Container chạy trên ECS.
- Kiểm tra khả năng sử dụng Docker Image từ ECR để khởi chạy ECS Task.
- Kiểm thử và xử lý các lỗi liên quan đến Docker Image, Port Mapping, Environment Variables và Log Configuration.

### Các công việc cần triển khai trong tuần:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                                                                                                                                                                  |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Tiếp nhận yêu cầu, phân tích kết quả mong đợi của từng task để xác định các yêu cầu cần hoàn thành.<br>- Xác định mối liên hệ giữa Frontend, Docker, ECR và ECS trong kiến trúc triển khai.<br>- Tìm hiểu các thành phần của Amazon ECS gồm Cluster, Task Definition, Task và Service.<br>- Xác định các thông số cần cấu hình cho Frontend Container như CPU, Memory, Port và Environment Variables.                                                                                                                                                                         | 20/07/2026   | 20/07/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html                                                                                                                                                                            |
| 3   | - Tạo **ECS Cluster** sử dụng AWS Fargate.<br>- Tìm hiểu cấu hình cần thiết để ECS Task có thể chạy trong VPC và các Subnet được chỉ định.<br>- Khởi tạo **Task Definition cho Frontend**.<br>- Khai báo Docker Image, CPU, Memory và Container Port trong Task Definition.<br>- Cấu hình IAM Task Execution Role phục vụ quá trình pull Image từ ECR và gửi log đến CloudWatch.<br>- Cấu hình CloudWatch Log Group và Log Configuration cho Container.                                                                                                                         | 21/07/2026   | 21/07/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html<br>https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html<br>https://docs.aws.amazon.com/AmazonECS/latest/developerguide/using_awslogs.html |
| 4   | - Kiểm tra cấu trúc và môi trường phát triển của ứng dụng React.<br>- Xác định quy trình build ứng dụng Frontend để chạy trong môi trường Container.<br>- Xây dựng **Dockerfile** cho Frontend.<br>- Build Docker Image từ source code React.<br>- Chạy Container trên môi trường local để kiểm tra ứng dụng trước khi triển khai lên AWS.<br>- Kiểm tra Port Mapping và khả năng truy cập ứng dụng từ trình duyệt.<br>- Tag Docker Image theo quy ước của Amazon ECR và push Image lên ECR Repository.                                                                         | 22/07/2026   | 22/07/2026      | https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html                                                                                                                                                                             |
| 5   | - Xác định và cấu hình các Environment Variables cần thiết cho Frontend.<br>- Kiểm tra cấu hình API Endpoint để Frontend có thể sử dụng Backend trong môi trường triển khai.<br>- Cập nhật Docker Image sau khi hoàn tất thay đổi cấu hình.<br>- Kiểm tra ECS Task sử dụng Docker Image được lưu trữ trên ECR.<br>- Theo dõi trạng thái Task trên ECS và kiểm tra Container có khởi động thành công hay không.<br>- Kiểm tra log của Container được ghi nhận trên Amazon CloudWatch Logs.<br>- Phân tích và xử lý các lỗi phát sinh trong quá trình khởi chạy Container nếu có. | 23/07/2026   | 23/07/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html<br>https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html                                                                   |
| 6   | - Kiểm tra ECS Cluster, Task Definition và trạng thái ECS Task.<br>- Kiểm tra Docker Image trên ECR và khả năng ECS pull Image thành công.<br>- Kiểm tra khả năng khởi động và hoạt động của Frontend Container.<br>- Kiểm tra Port Mapping và Environment Variables.<br>- Kiểm tra log trên CloudWatch Logs để xác nhận ứng dụng hoạt động bình thường.<br>- Khắc phục các lỗi cấu hình phát sinh trong quá trình kiểm thử.<br>- Đối chiếu kết quả, hoàn thiện tài liệu triển khai và tổng hợp kết quả thực hiện                                                               | 24/07/2026   | 24/07/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html<br>https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html                                                                                                 |

### Kết quả đạt được tuần 5:

Sau khi hoàn thành các nhiệm vụ được giao, em đạt được các kết quả sau:

- Tạo thành công **Amazon ECS Cluster** sử dụng **AWS Fargate**.
- Hiểu được vai trò của ECS Cluster trong việc quản lý các Task chạy Container.
- Tạo và cấu hình **Task Definition cho Frontend**, bao gồm các thông số:
  - Docker Image.
  - CPU.
  - Memory.
  - Container Port.
  - Environment Variables.
  - IAM Task Execution Role.
  - CloudWatch Log Configuration.
- Hoàn thành bổ sung cho **Dockerfile** cho phía Frontend và thực hiện Docker Image Build.
- Kiểm thử Docker Image trên môi trường local trước khi triển khai lên AWS.
- Tạo và sử dụng **Amazon ECR Repository** để lưu trữ Docker Image của Frontend.
- Thực hiện thành công quy trình **Build → Tag → Push Docker Image lên ECR**.
- Cấu hình ECS Task sử dụng Docker Image được lưu trữ trên ECR.
- Cấu hình **Amazon CloudWatch Logs** để thu thập và theo dõi log của Frontend Container.
- Kiểm tra được trạng thái ECS Task và xác nhận Container có thể khởi chạy với cấu hình đã thiết lập.
- Kiểm tra và điều chỉnh Environment Variables, Port Mapping và các thông số Container trong quá trình triển khai.
- Hiểu rõ hơn mối quan hệ giữa **Docker → ECR → ECS Fargate → CloudWatch Logs** trong quy trình triển khai ứng dụng Container trên AWS.
- Hoàn thiện tài liệu triển khai và tạo nền tảng để tiếp tục tích hợp Frontend với Backend, ECS Service và các thành phần mạng trong các nhiệm vụ tiếp theo.
