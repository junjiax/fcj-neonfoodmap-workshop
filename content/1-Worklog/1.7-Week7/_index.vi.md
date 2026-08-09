---
title: "Worklog Tuần 7"
date: 2026-08-03
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

---

### Mục tiêu tuần 7:

**Nhiệm vụ cá nhân:** Kiểm thử và rà soát toàn bộ hệ thống NeonFoodMap sau khi triển khai trên AWS, theo dõi trạng thái vận hành, phân tích log, kiểm tra chi phí và hoàn thiện tài liệu triển khai.

Trong tuần 7, em tập trung vào giai đoạn kiểm tra sau triển khai và chuẩn hóa tài liệu cho hệ thống NeonFoodMap. Nội dung công việc bao gồm:

- Tiếp tục kiểm tra khả năng hoạt động ổn định của **ECS Services** và các ECS Task sau khi triển khai.
- Kiểm tra cơ chế duy trì số lượng Task theo cấu hình của ECS Service.
- Theo dõi trạng thái hoạt động của Backend và Frontend thông qua **CloudWatch Dashboard**.
- Theo dõi CPU, Memory và các Metrics liên quan đến ECS Task/Service.
- Kiểm tra log của các Container thông qua **CloudWatch Logs**.
- Sử dụng **CloudWatch Logs Insights** để truy vấn, lọc và phân tích các log phát sinh trong quá trình vận hành.
- Kiểm tra các lỗi ứng dụng, lỗi Container hoặc lỗi kết nối thông qua log và Metrics.
- Theo dõi chi phí sử dụng các dịch vụ AWS trong quá trình triển khai.
- Tìm hiểu và kiểm tra các cơ chế **Cost Monitoring & Alerts** để phát hiện nguy cơ phát sinh chi phí ngoài dự kiến.
- Rà soát toàn bộ quy trình triển khai từ **Source Code → GitHub Actions → Docker Build → ECR → ECS → CloudWatch**.
- Tham gia hỗ trợ team hoàn thiện và chuẩn hóa tài liệu triển khai dự án **NeonFoodMap**, bổ sung hình ảnh minh họa, cấu hình, kết quả kiểm thử và các lưu ý cần thiết cho từng bước.
- Rà soát lại các lỗi trình bày, thứ tự thao tác và thông tin cấu hình trong tài liệu.
- Tổng hợp kết quả thực hiện và ghi nhận các nội dung cần tiếp tục hoàn thiện.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                                                                                                                                                                |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Tiếp nhận yêu cầu và phạm vi công việc của tuần.<br>- Rà soát trạng thái triển khai hiện tại của NeonFoodMap.<br>- Kiểm tra **ECS Cluster, ECS Service, ECS Task và Task Definition** của Frontend và Backend.<br>- Kiểm tra Desired Count và Running Count của các ECS Service.<br>- Kiểm tra trạng thái Container và xác nhận các Task có thể khởi chạy ổn định.<br>- Rà soát lại quy trình triển khai từ ECR đến ECS sau khi Docker Image được cập nhật.                                                                                                    | 03/08/2026   | 03/08/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_services.html                                                                                                 |
| 3   | - Tìm hiểu cơ chế Service Auto Scaling và các thành phần liên quan đến việc điều chỉnh số lượng Task.<br>- Kiểm tra khả năng duy trì số lượng Task theo cấu hình Desired Count.<br>- Theo dõi CPU và Memory của ECS Task thông qua CloudWatch Metrics.<br>- Kiểm tra CloudWatch Dashboard và bổ sung các Metrics cần thiết phục vụ giám sát hệ thống.<br>- Kiểm tra trạng thái hệ thống trong các trường hợp Task được khởi động lại hoặc thay đổi trạng thái.                                                                                                   | 04/08/2026   | 04/08/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-auto-scaling.html<br>https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html |
| 4   | - Kiểm tra **CloudWatch Logs** của Frontend và Backend Container.<br>- Kiểm tra Log Group và Log Stream được tạo tương ứng với các ECS Task.<br>- Sử dụng **CloudWatch Logs Insights** để truy vấn và phân tích log.<br>- Thực hiện lọc log theo khoảng thời gian và nội dung cần kiểm tra.<br>- Xác định các log liên quan đến lỗi ứng dụng, lỗi kết nối hoặc lỗi Container nếu phát sinh.                                                                                                                                                                      | 05/08/2026   | 05/08/2026      | https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html<br>https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html          |
| 5   | - Kiểm tra chi phí sử dụng các tài nguyên AWS trong quá trình triển khai NeonFoodMap.<br>- Rà soát các dịch vụ có khả năng phát sinh chi phí như ECS Fargate, RDS, NAT Gateway, Load Balancer, CloudWatch và các dịch vụ liên quan.<br>- Tìm hiểu **AWS Cost Management** và cơ chế theo dõi chi phí.<br>- Kiểm tra các cảnh báo Cost Monitoring & Alerts nếu đã được cấu hình.<br>- Rà soát các tài nguyên không cần thiết hoặc có nguy cơ phát sinh chi phí ngoài dự kiến.<br>- Tổng hợp kết quả kiểm tra và ghi nhận các lưu ý liên quan đến quản lý chi phí. | 06/08/2026   | 06/08/2026      | https://docs.aws.amazon.com/cost-management/latest/userguide/what-is-costmanagement.html                                                                                      |
| 6   | - Rà soát toàn bộ quy trình triển khai NeonFoodMap từ Source Code đến môi trường AWS.<br>- Kiểm tra luồng **GitHub → GitHub Actions → Docker → ECR → ECS/Fargate → CloudWatch**.<br>- Kiểm tra thứ tự các bước hướng dẫn và điều chỉnh những nội dung chưa chính xác hoặc chưa thống nhất.<br>- Bổ sung hình ảnh minh họa cho các bước triển khai còn thiếu.<br>- Bổ sung thông tin cấu hình, kết quả kiểm thử và các lưu ý trong quá trình thực hiện.<br>- Hoàn thiện tài liệu triển khai NeonFoodMap và tổng hợp kết quả thực tập.<br>                         | 07/08/2026   | 07/08/2026      | https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html                                                                                                      |

### Kết quả đạt được tuần 7:

Sau khi hoàn thành các nhiệm vụ được giao, em đạt được các kết quả sau:

- Kiểm tra và xác nhận trạng thái hoạt động của **ECS Cluster, ECS Service và ECS Task** sau khi triển khai.

- Rà soát toàn bộ quy trình triển khai của NeonFoodMap theo luồng:

  **Source Code → GitHub → GitHub Actions → Docker Build → Amazon ECR → Amazon ECS/Fargate → CloudWatch**

- Rèn luyện quy trình kiểm thử sau triển khai theo hướng **kiểm tra trạng thái → theo dõi Metrics → phân tích Logs → xác định vấn đề → điều chỉnh cấu hình → kiểm thử lại**.

- Có cái nhìn tổng thể hơn về quy trình triển khai một ứng dụng thực tế trên Cloud, từ **phát triển, container hóa, CI/CD, triển khai, giám sát đến kiểm soát chi phí và tài liệu hóa**.
