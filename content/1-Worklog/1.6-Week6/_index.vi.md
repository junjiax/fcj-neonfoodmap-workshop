---
title: "Worklog Tuần 6"
date: 2026-07-27
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

---

### Mục tiêu tuần 6:

**Nhiệm vụ cá nhân:** Thiết lập hệ thống giám sát và quản lý log cho các thành phần của ứng dụng trên AWS, tập trung vào Amazon CloudWatch.

Trong tuần 6, em thực hiện xây dựng khả năng quan sát hệ thống thông qua CloudWatch, giúp theo dõi trạng thái hoạt động, kiểm tra log ứng dụng và hỗ trợ phát hiện, phân tích các vấn đề phát sinh trong quá trình vận hành.

Các mục tiêu chính trong tuần:

- Kiểm tra trạng thái hoạt động của các thành phần đã triển khai trên AWS và xác định các thông tin cần theo dõi.
- Tìm hiểu cơ chế hoạt động của **Amazon CloudWatch**, đặc biệt là Metrics, Logs, Dashboards và Logs Insights.
- Cấu hình **CloudWatch Dashboard** để tập trung các thông tin quan trọng về trạng thái và hiệu năng của hệ thống.
- Cấu hình **CloudWatch Log Group** và Log Stream phục vụ việc lưu trữ, phân loại và theo dõi log.
- Kiểm tra khả năng thu thập log từ các Container đang chạy trên Amazon ECS.
- Sử dụng **CloudWatch Logs Insights** để truy vấn, lọc và phân tích log ứng dụng.
- Thực hiện kiểm thử hệ thống sau khi cấu hình các thành phần giám sát.
- Phát hiện, phân tích và xử lý các lỗi liên quan đến cấu hình log, quyền truy cập IAM hoặc quá trình ghi nhận log nếu phát sinh.
- Hoàn thiện tài liệu cấu hình và quy trình giám sát, tạo nền tảng cho các bước kiểm thử và vận hành.

### Các công việc cần triển khai trong tuần:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                                                                                   |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Tiếp nhận yêu cầu và phân tích phạm vi công việc.<br>- Kiểm tra các thành phần AWS đã được triển khai từ các Sprint trước và xác định các tài nguyên cần giám sát.<br>- Xác định các Metrics và Logs cần thu thập để theo dõi trạng thái hoạt động của hệ thống.<br>- Tìm hiểu cơ chế hoạt động của CloudWatch Dashboard, CloudWatch Logs và CloudWatch Logs Insights.                                                                                                                                                                         | 27/07/2026   | 27/07/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html                                                                                 |
| 3   | - Kiểm tra môi trường vận hành và trạng thái của các dịch vụ AWS liên quan.<br>- Kiểm tra trạng thái ECS Cluster, ECS Service và ECS Task.<br>- Kiểm tra các Metrics được cung cấp bởi AWS để xác định tình trạng hoạt động của hệ thống.<br>- Tạo và cấu hình **CloudWatch Dashboard**.<br>- Thêm các biểu đồ và Metrics cần thiết vào Dashboard để tập trung theo dõi hệ thống.<br>- Kiểm tra khả năng cập nhật dữ liệu trên Dashboard theo trạng thái thực tế của tài nguyên.                                                                 | 28/07/2026   | 28/07/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Dashboards.html                                                                            |
| 4   | - Kiểm thử hoạt động của hệ thống sau khi cấu hình Dashboard.<br>- Theo dõi Metrics để phát hiện các trạng thái bất thường của tài nguyên.<br>- Xác nhận các thành phần cần giám sát đã được thể hiện đầy đủ trên CloudWatch Dashboard.                                                                                                                                                                                                                                                                                                          | 29/07/2026   | 29/07/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitoring-services.html                                                                              |
| 5   | - Tạo và cấu hình **Amazon CloudWatch Log Group** cho các dịch vụ cần theo dõi.<br>- Kiểm tra Log Stream được tạo trong quá trình Container hoạt động.<br>- Kiểm tra cấu hình `awslogs` của ECS Task Definition.<br>- Kiểm tra quyền IAM cần thiết để ECS Task có thể gửi log đến CloudWatch.<br>- Khởi chạy và kiểm thử Container để tạo log mẫu.<br>- Kiểm tra log được ghi nhận và hiển thị đầy đủ trên CloudWatch Logs.<br>- Sử dụng **CloudWatch Logs Insights** để truy vấn, lọc và tìm kiếm các bản ghi log theo thời gian hoặc nội dung. | 30/07/2026   | 30/07/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html<br>https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html |
| 6   | - Kiểm tra CloudWatch Dashboard và xác nhận các Metrics được hiển thị chính xác.<br>- Kiểm tra log của các Container và dịch vụ trên CloudWatch Logs.<br>- Thực hiện truy vấn bằng Logs Insights để xác nhận khả năng tìm kiếm và phân tích log.<br>- Kiểm tra khả năng phát hiện lỗi thông qua Metrics và Logs.<br>- Khắc phục các vấn đề phát sinh liên quan đến cấu hình Dashboard, Log Group, Log Stream hoặc IAM Permission nếu có.<br>- Hoàn thiện tài liệu cấu hình và tổng hợp kết quả.                                                  | 31/07/2026   | 31/07/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html                                                                                 |

### Kết quả đạt được tuần 6:

Sau khi hoàn thành các nhiệm vụ được giao, em đạt được các kết quả sau:

- Hiểu rõ hơn về cơ chế giám sát tài nguyên AWS thông qua **Amazon CloudWatch**.
- Cấu hình thành công **CloudWatch Dashboard** để tập trung theo dõi các Metrics quan trọng của hệ thống.
- Biết cách lựa chọn và thêm các Metrics phù hợp vào Dashboard để phục vụ việc theo dõi trạng thái hoạt động của tài nguyên.
- Thực hiện kiểm thử Dashboard và xác nhận dữ liệu được cập nhật theo trạng thái thực tế của hệ thống.
- Hoàn thành triển khai hệ thống thu thập và quản lý log bằng **Amazon CloudWatch Logs**.
- Tạo và cấu hình **Log Group** phục vụ việc phân loại và lưu trữ log của ứng dụng.
- Kiểm tra **Log Stream** và xác nhận log từ Container được ghi nhận thành công.
- Kiểm tra cấu hình ECS Task Definition và IAM Permission liên quan đến quá trình gửi log lên CloudWatch.
- Sử dụng **CloudWatch Logs Insights** để truy vấn và phân tích log ứng dụng.
- Hiểu được sự khác biệt và mối liên hệ giữa **CloudWatch Metrics, CloudWatch Dashboard và CloudWatch Logs** trong quá trình giám sát hệ thống.
- Đảm bảo môi trường triển khai có khả năng **theo dõi trạng thái hoạt động, thu thập log và hỗ trợ phân tích sự cố**, tạo nền tảng cho các nhiệm vụ tiếp theo liên quan đến Load Balancer, routing và hoàn thiện hệ thống.
