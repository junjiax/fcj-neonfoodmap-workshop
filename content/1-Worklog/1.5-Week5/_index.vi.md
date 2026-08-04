---
title: "Worklog Tuần 5"
date: 2026-07-20
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Thông tin dưới đây chỉ mang tính tham khảo. Vui lòng không sao chép nguyên văn cho báo cáo cá nhân, bao gồm cả cảnh báo này.
{{% /notice %}}

### Mục tiêu tuần 5:

- Hoàn thành triển khai Task AWS-005 theo kế hoạch Sprint 2.
- Hoàn thành Task FRONTEND-001, xây dựng và container hóa ứng dụng Frontend.
- Chuẩn bị môi trường để Frontend có thể triển khai trên hạ tầng AWS.

### Các công việc cần triển khai trong tuần:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | - Tiếp nhận yêu cầu của Sprint 2 và phân tích Task AWS-005 cùng FRONTEND-001 <br> - Nghiên cứu Acceptance Criteria và tài liệu kỹ thuật của hai task | 20/07/2026 | 20/07/2026 | |
| 3 | - Triển khai Task AWS-005 <br> - Tạo ECS Cluster bằng AWS Fargate <br> - Khởi tạo Task Definition cho Frontend <br> - Cấu hình CloudWatch Logs để theo dõi ứng dụng | 21/07/2026 | 21/07/2026 | |
| 4 | - Thực hiện Task FRONTEND-001 <br> - Thiết lập môi trường phát triển Frontend <br> - Xây dựng Dockerfile và kiểm thử trên môi trường local <br> - Push Docker Image lên Amazon ECR | 22/07/2026 | 22/07/2026 | |
| 5 | - Tiếp tục hoàn thiện FRONTEND-001 <br> - Cấu hình biến môi trường phục vụ Frontend <br> - Kiểm tra khả năng chạy container trên ECS Task Definition <br> - Kiểm thử ghi log lên Amazon CloudWatch | 23/07/2026 | 23/07/2026 | |
| 6 | - Kiểm thử tổng thể các nội dung triển khai của AWS-005 và FRONTEND-001 <br> - Khắc phục lỗi cấu hình phát sinh <br> - Hoàn thiện tài liệu triển khai và báo cáo kết quả Sprint 2 | 24/07/2026 | 24/07/2026 | |

### Kết quả đạt được tuần 5:

- Hoàn thành Task AWS-005, triển khai thành công Amazon ECS Cluster và cấu hình Task Definition cho Frontend.
- Thiết lập CloudWatch Logs để theo dõi trạng thái và log của container.
- Hoàn thành Task FRONTEND-001, xây dựng Docker Image cho Frontend và lưu trữ trên Amazon ECR.
- Kiểm thử thành công việc chạy Frontend trong môi trường container và xác nhận cấu hình đáp ứng Acceptance Criteria của Sprint 2.
- Hoàn thiện tài liệu triển khai và sẵn sàng tích hợp Frontend với các thành phần Backend trong các Sprint tiếp theo.