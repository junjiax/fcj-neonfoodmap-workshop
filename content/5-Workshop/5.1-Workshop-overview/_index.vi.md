---

title : "Giới thiệu"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
-----------------------

# 5.1. Tổng quan

# Thử thách Cloud & DevOps: Triển khai hệ thống lên AWS Cloud và xây dựng quy trình CI/CD tự động

Nhằm đáp ứng yêu cầu về khả năng triển khai linh hoạt, tự động hóa quá trình phát hành phần mềm và nâng cao tính sẵn sàng của hệ thống, dự án thực hiện triển khai ứng dụng trên nền tảng Amazon Web Services (AWS) và xây dựng quy trình CI/CD (Continuous Integration/Continuous Deployment) hoàn toàn tự động. Kiến trúc Cloud & DevOps của hệ thống được tổ chức thành ba luồng xử lý chính: **luồng CI/CD, luồng xử lý yêu cầu người dùng và luồng giám sát & quản lý chi phí**.

## 5.1.1. Luồng CI/CD

Quy trình tích hợp và triển khai liên tục được thiết kế nhằm tự động hóa toàn bộ quy trình, từ thời điểm lập trình viên cập nhật mã nguồn cho đến khi phiên bản ứng dụng mới được triển khai lên môi trường production.

Cụ thể, khi lập trình viên push mã nguồn lên repository GitHub, GitHub Actions sẽ được kích hoạt để khởi chạy pipeline. Pipeline sử dụng cơ chế xác thực OIDC (OpenID Connect) để kết nối với AWS Security Token Service (STS) và nhận các thông tin xác thực tạm thời, thay thế cho việc sử dụng Access Key/Secret Key cố định, từ đó nâng cao tính bảo mật.

Sau khi xác thực thành công, pipeline tiến hành build Docker image của ứng dụng và push image lên Amazon Elastic Container Registry (ECR). Tiếp theo, dịch vụ Amazon ECS Fargate sẽ tự động pull image mới nhất từ ECR và triển khai phiên bản ứng dụng mới mà không cần thực hiện thủ công.

Quy trình được mô tả như sau:

**Developer → GitHub → GitHub Actions → Xác thực OIDC → AWS STS → Amazon ECR → Amazon ECS Fargate**

## 5.1.2. Luồng xử lý yêu cầu người dùng

Luồng xử lý yêu cầu được thiết kế dựa trên mô hình phân phối nội dung và cân bằng tải nhằm đảm bảo hiệu năng truy cập và khả năng chịu lỗi của hệ thống.

Khi người dùng gửi một yêu cầu truy cập, yêu cầu trước tiên được tiếp nhận bởi Amazon CloudFront — dịch vụ Content Delivery Network (CDN) của AWS.

Đối với các tài nguyên giao diện tĩnh, CloudFront lấy dữ liệu trực tiếp từ Amazon S3 Frontend Bucket. Đối với các yêu cầu động, CloudFront chuyển tiếp yêu cầu đến Application Load Balancer (ALB).

ALB phân phối lưu lượng truy cập đến các ECS Fargate task đang chạy trên hai Availability Zone (AZ) khác nhau nhằm đảm bảo **High Availability**. Các container của ứng dụng kết nối đến Amazon RDS Primary instance được đặt tại Zone A để thực hiện các thao tác đọc/ghi dữ liệu.

Đồng thời, dữ liệu được đồng bộ liên tục đến RDS Standby instance tại Zone B thông qua cơ chế Multi-AZ, cho phép hệ thống thực hiện chuyển đổi dự phòng (failover) khi xảy ra sự cố.

Ngoài ra, các ECS container truy cập S3 Media Bucket thông qua VPC Endpoint, cho phép dữ liệu được truyền tải nội bộ trong mạng AWS mà không cần đi qua Internet công cộng. Điều này giúp tăng cường bảo mật và tối ưu chi phí truyền dữ liệu.

Luồng xử lý được mô tả như sau:

**User → CloudFront → (S3 Frontend hoặc ALB) → ECS Fargate (2 AZs) → RDS Primary (Zone A) → RDS Standby (Zone B)**

## 5.1.3. Giám sát hệ thống & Quản lý chi phí

Nhằm đảm bảo hệ thống hoạt động ổn định và kiểm soát hiệu quả chi phí sử dụng tài nguyên Cloud, dự án triển khai cơ chế giám sát và cảnh báo tự động dựa trên các dịch vụ quản lý của AWS.

Toàn bộ log của hệ thống, bao gồm **VPC Flow Logs** và **Application Logs**, được thu thập và tập trung tại Amazon CloudWatch nhằm phục vụ việc giám sát, phân tích và xử lý sự cố.

Hệ thống được cấu hình **Auto Scaling** cho ECS service, cho phép tự động điều chỉnh số lượng task khi mức sử dụng CPU hoặc bộ nhớ vượt quá 70%, qua đó duy trì hiệu năng hệ thống trong các thời điểm có tải cao.

Về quản lý chi phí, hệ thống sử dụng AWS Budgets với ngân sách hàng tháng được thiết lập ở mức **15 USD**. Các ngưỡng cảnh báo được cấu hình lần lượt tại **50%, 70% và 90%** ngân sách.

Khi chi phí đạt đến các ngưỡng trên hoặc xuất hiện dấu hiệu gia tăng bất thường, AWS Budgets sẽ tự động kích hoạt Amazon SNS (Simple Notification Service) để gửi email cảnh báo đến quản trị viên, giúp phát hiện sớm các rủi ro và có biện pháp xử lý kịp thời.

Luồng giám sát và cảnh báo được mô tả như sau:

**CloudWatch (Logs & Metrics) → Auto Scaling → AWS Budgets → Amazon SNS → Email Alert**

## 5.1.4. Kiến trúc hệ thống

### Kiến trúc tổng thể

![](images/2-Proposal/diagram1.png)

Kiến trúc hệ thống được chia thành năm lớp chính:

#### Lớp CI/CD

Bao gồm:

* GitHub Repository
* GitHub Actions
* Docker Build
* AWS STS
* Amazon ECR

Lớp này chịu trách nhiệm tự động hóa toàn bộ quá trình triển khai ứng dụng.

Sau mỗi lần push mã nguồn lên nhánh `main`:

1. Mã nguồn được build.
2. Docker image được tạo.
3. GitHub sử dụng OIDC để xác thực.
4. AWS STS cấp thông tin xác thực tạm thời.
5. Docker image được push lên Amazon ECR.
6. ECS service thực hiện rolling deployment.

---

#### Lớp Presentation

Bao gồm:

* Amazon CloudFront
* Amazon S3 Static Website

Frontend được lưu trữ trên Amazon S3 và phân phối thông qua CloudFront nhằm:

* giảm độ trễ
* tăng tốc độ truy cập
* giảm tải cho backend

---

#### Lớp Application

Bao gồm:

* Application Load Balancer
* Amazon ECS Cluster
* Backend Service
* Frontend Service

Ứng dụng được triển khai trên ECS Fargate, loại bỏ nhu cầu quản lý trực tiếp các EC2 instance.

Các service hoạt động độc lập, cho phép:

* scale từng thành phần độc lập
* thực hiện rolling update
* tự động khởi động lại khi xảy ra lỗi

---

#### Lớp Data

Bao gồm:

* Amazon RDS MySQL
* Multi-AZ Deployment

Database được triển khai trong **private database subnet**.

Việc sử dụng Multi-AZ mang lại:

* tăng khả năng chịu lỗi
* tự động chuyển đổi dự phòng (automatic failover)
* giảm thời gian gián đoạn dịch vụ

---

#### Lớp Monitoring

Bao gồm:

* Amazon CloudWatch
* Amazon SNS

CloudWatch thu thập:

* ECS logs
* container logs
* metrics
* application logs

SNS chịu trách nhiệm gửi email cảnh báo khi phát hiện các dấu hiệu bất thường.

---

### Kiến trúc triển khai ECS

![](images/2-Proposal/diagram2.png)

Hệ thống sử dụng một ECS Cluster bao gồm hai service:

#### Backend Service

Triển khai:

* Django REST API
* Docker container
* ECS Fargate

Backend chịu trách nhiệm xử lý:

* xác thực người dùng
* logic nghiệp vụ
* truy cập cơ sở dữ liệu
* tải lên và quản lý media

---

#### Frontend Service

Triển khai:

* React application
* Docker container
* ECS Fargate

Frontend giao tiếp với backend thông qua ALB.

---

#### Service Discovery

AWS Cloud Map được sử dụng để quản lý cơ chế service discovery giữa các container bên trong ECS Cluster.

---

#### Load Balancing

Application Load Balancer tiếp nhận:

* HTTP requests
* HTTPS requests

Sau đó, ALB định tuyến các request đến backend service.

---

## 5.1.5. Các thành phần AWS được sử dụng

| Dịch vụ                 | Mục đích                                               |
| ----------------------- | ------------------------------------------------------ |
| IAM                     | Quản lý quyền truy cập                                 |
| STS                     | Cấp thông tin xác thực tạm thời                        |
| VPC                     | Mạng riêng                                             |
| Public / Private Subnet | Phân tách mạng                                         |
| NAT Gateway             | Cung cấp khả năng truy cập Internet cho Private Subnet |
| Internet Gateway        | Kết nối mạng với Internet                              |
| ECS Fargate             | Chạy container                                         |
| ECR                     | Lưu trữ Docker image                                   |
| RDS MySQL               | Cơ sở dữ liệu                                          |
| S3                      | Lưu trữ website tĩnh, media và log                     |
| CloudFront              | Phân phối nội dung (CDN)                               |
| ALB                     | Cân bằng tải                                           |
| CloudWatch              | Giám sát hệ thống                                      |
| SNS                     | Gửi thông báo và cảnh báo                              |
| Secrets Manager         | Quản lý thông tin bí mật                               |

---
