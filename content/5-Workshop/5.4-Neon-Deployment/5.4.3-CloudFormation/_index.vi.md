---
title : "Tạo stack IAM bằng CloudFormation"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.4.3. </b> "
---

### 5.4.3. Tạo stack IAM bằng CloudFormation

Stack này tạo toàn bộ IAM Users, Groups, Policies, Roles và Budget Alerts cho dự án.

1. Đăng nhập AWS với tài khoản Root hoặc IAM Admin.
2. Mở dịch vụ CloudFormation.
3. Đảm bảo region đang chọn là `ap-southeast-1`.
4. Chọn Create stack → With new resources (standard).
5. Chọn Upload a template file.
6. Tải lên file `neonfoodmap-iam-setup.yaml`.
7. Nhấn Next để tiếp tục.
8. Hoàn tất các bước review và submit để tạo stack.

I. Triển khai IAM qua CloudFormation
1. Tổng quan dự án
Dự án NeonFoodmap yêu cầu thiết lập hạ tầng định danh và quản lý truy cập (IAM) tập trung, đảm bảo tính bảo mật cao thông qua việc áp dụng nghiêm ngặt nguyên tắc đặc quyền tối thiểu (Least Privilege). Toàn bộ người dùng trong hệ thống bắt buộc phải kích hoạt xác thực đa yếu tố (MFA) thông qua chính sách Force MFA trước khi có thể thực hiện bất kỳ thao tác nào trên các tài nguyên AWS. Việc triển khai được thực hiện tự động hóa bằng AWS CloudFormation để đảm bảo tính nhất quán, quản lý hạ tầng dưới dạng mã (IaC) và dễ dàng mở rộng. 
2. Các thành phần chính
Mẫu neonfoodmap-iam-setup.yaml bao gồm:
Chính sách (Policies):
ForceMFAPolicy: Chặn tất cả các thao tác dịch vụ (ngoại trừ các lệnh thiết lập MFA và xem thông tin tài khoản) nếu người dùng chưa kích hoạt xác thực đa yếu tố.
SelfServicePolicy: Cho phép người dùng tự quản lý tài khoản cơ bản.
Nhóm người dùng (Groups):
DevOpsAdmins: Quyền quản trị hệ thống.
BackendDevs: Quản lý ECS, RDS, S3 cho Backend.
FrontendDevs: Quản lý S3, CloudFront cho Frontend.
Vai trò & Tích hợp (Roles & OIDC):
IAM Roles & OIDC Provider:
GitHubOIDCProvider: Khởi tạo tích hợp OIDC với GitHub Actions.
ECSBackendRole: Cấp quyền cho container truy cập tài nguyên AWS.
GitHubActionsRole: Cho phép deploy tự động từ repo GitHub.
GitHubActionsRole: Cấp quyền cho GitHub Actions workflow (repo:HaoWasabi/NeonFoodmap) đẩy ECR image và deploy lên ECS không cần dùng Access Key dài hạn.
Giám sát chi phí (Budgets):
MonthlyBudget: Ngân sách $40 USD/tháng với các ngưỡng cảnh báo.
CostAnomaly: Phát hiện chi tiêu bất thường vượt mức $3.
3. Quy trình triển khai
Truy cập CloudFormation trong AWS Console bằng tài khoản Admin.
Chọn Create stack và tải lên tệp neonfoodmap-iam-setup.yaml.
Cấu hình các Parameters: Tên dự án, mật khẩu tạm thời cho thành viên và ngân sách hàng tháng.
Tại bước Review, tích chọn xác nhận tạo tài nguyên IAM (Acknowledge IAM resources).
Nhấn Submit để bắt đầu khởi tạo hạ tầng.

![Hình 3. Tạo stack IAM trên CloudFormation](/images/5-Workshop/5.4-neon-deployment/placeholder-cloudformation.png)

