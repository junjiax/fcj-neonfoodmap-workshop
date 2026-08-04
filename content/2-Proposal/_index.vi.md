---
title: "Bản đề xuất"
date: 2026-07-01
weight: 2
chapter: false
pre: "<b>2.</b>"
---

# Tự động hóa quy trình CI/CD cho ứng dụng Neon Food Map trên nền tảng AWS
## 2.1. Bối cảnh chung về dự án

Đề xuất này trình bày giải pháp triển khai hệ thống NeonFoodMap trên nền tảng Amazon Web Services (AWS) theo kiến trúc Cloud-Native, đáp ứng các yêu cầu về khả năng mở rộng, tính sẵn sàng cao, bảo mật và tự động hóa quy trình phát hành phần mềm. Mục tiêu của giải pháp là xây dựng một hạ tầng triển khai có khả năng tái sử dụng, hỗ trợ triển khai lặp lại, đồng thời chuẩn hóa quy trình vận hành theo định hướng DevOps trong môi trường Production.

NeonFoodMap là nền tảng bản đồ ẩm thực trên nền tảng web, cho phép người dùng tìm kiếm, khám phá và đánh giá các địa điểm ăn uống theo thời gian thực. Hệ thống tích hợp các chức năng như tìm kiếm địa điểm (POI), định vị GPS, hiển thị lộ trình, đánh giá địa điểm và phát nội dung mô tả bằng công nghệ Text-to-Speech nhằm nâng cao trải nghiệm người dùng. Với đặc điểm xử lý dữ liệu theo thời gian thực và yêu cầu phục vụ nhiều người dùng đồng thời, hệ thống cần được triển khai trên một hạ tầng có khả năng mở rộng linh hoạt, đảm bảo tính sẵn sàng và dễ dàng bảo trì.

Đề xuất tập trung xây dựng kiến trúc triển khai sử dụng Docker và Amazon ECS Fargate, quản lý mã nguồn bằng GitHub, tự động hóa quy trình Build–Test–Deploy thông qua GitHub Actions và OpenID Connect (OIDC), lưu trữ Docker Image trên Amazon ECR, triển khai cơ sở dữ liệu Amazon RDS trong Private Subnet, quản lý tài nguyên tĩnh bằng Amazon S3 và giám sát hệ thống bằng Amazon CloudWatch. Giải pháp hướng tới việc hình thành một quy trình triển khai thống nhất, an toàn và có khả năng mở rộng cho các giai đoạn phát triển tiếp theo của dự án.

---

## 2.2. Hiện trạng thực tế và giải pháp

Qua quá trình khảo sát, hệ thống hiện chưa hoàn thiện các thành phần hạ tầng và quy trình triển khai trên môi trường AWS. Các hạng mục cần được xây dựng bao gồm:

- Thiết kế kiến trúc hạ tầng AWS.
- Xây dựng quy trình CI/CD.
- Triển khai Backend và Frontend bằng Amazon ECS Fargate.
- Quản lý Docker Image.
- Cấu hình cơ sở dữ liệu.
- Quản lý Static Assets.
- Xây dựng hệ thống Logging và Monitoring.
- Hoàn thiện tài liệu triển khai theo từng Sprint.

---

# 2.3. Mục tiêu triển khai

Đề xuất hướng tới các mục tiêu kỹ thuật sau:

- Tự động hóa quy trình Build, Test và Deploy.
- Loại bỏ việc sử dụng AWS Access Key trong GitHub thông qua OpenID Connect (OIDC).
- Chuẩn hóa quy trình triển khai ứng dụng theo mô hình Container.
- Đảm bảo tính sẵn sàng cao (High Availability) cho hệ thống.
- Hỗ trợ mở rộng tài nguyên linh hoạt theo nhu cầu tải.
- Thiết lập cơ chế giám sát, ghi log và cảnh báo tập trung.
- Chuẩn hóa quy trình triển khai theo mô hình DevOps và nâng cao khả năng tái sử dụng.

---

# 2.4. Kết quả mong đợi

Sau khi hoàn thành quá trình triển khai, hệ thống dự kiến đạt được các kết quả sau:

- Hoàn thiện kiến trúc triển khai trên nền tảng AWS theo mô hình Cloud-Native.
- Quy trình CI/CD hoạt động tự động từ Build đến Deploy.
- Ứng dụng được triển khai bằng Amazon ECS Fargate.
- Docker Image được quản lý tập trung trên Amazon ECR.
- Cơ sở dữ liệu được triển khai an toàn trong Private Subnet.
- Hệ thống được giám sát thông qua cơ chế Logging, Monitoring và Alerting.
- Quy trình triển khai được chuẩn hóa, có khả năng mở rộng và tái sử dụng cho các dự án tương tự.