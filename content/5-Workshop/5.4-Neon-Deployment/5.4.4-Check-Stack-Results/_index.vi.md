---
title : "Kiểm tra kết quả stack và lấy output quan trọng"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.4.4. </b> "
---

### 5.4.4. Kiểm tra kết quả stack và lấy output quan trọng

Sau khi stack tạo thành công, vào tab Outputs để lấy các giá trị cần dùng cho pipeline.

Các output quan trọng:

- `GitHubActionsRoleArn` → lưu vào GitHub Secrets
- `ECSBackendRoleArn` → dùng trong ECS Task Definition
- `ECSTaskExecutionRoleArn` → dùng trong ECS Task Definition
- `ConsoleLoginURL` → gửi cho thành viên để đăng nhập

![Hình 4. Xem output từ CloudFormation](/images/5-Workshop/5.4-neon-deployment/placeholder-stack-output.png)

### 5.4.5. Khai báo Secrets và Variables trên GitHub

Truy cập repo GitHub → Settings → Secrets and variables → Actions.

#### 5.4.5.1. Thêm Repository Secrets

Các secret cần thiết:

- `AWS_ROLE_ARN`
- `ECS_SUBNETS`
- `ECS_SECURITY_GROUPS`
- `ECS_BACKEND_SERVICE`
- `ECS_BACKEND_TASK_DEF`
- `SECRET_KEY`
- `DEBUG`
- `ALLOWED_HOSTS`
- `DB_HOST`
- `DB_NAME`
- `DB_USER`
- `DB_PASSWORD`
- `DB_PORT`
- `CLOUDINARY_URL`
- `GOOGLE_TTS_API_KEY`
- `PAYPAL_CLIENT_ID`
- `PAYPAL_SECRET`
- `PAYPAL_BASE`

#### 5.4.5.2. Thêm Repository Variables

Các biến cần thiết:

- `AWS_REGION = ap-southeast-1`
- `ECR_REGISTRY = 497172038341.dkr.ecr.ap-southeast-1.amazonaws.com`
- `ECS_CLUSTER = neonfoodmap-cluster`
- `APP_URL = https://neonfoodmap.example.com`
- `VITE_API_URL = https://api.neonfoodmap.example.com`

![Hình 5. Thiết lập GitHub Secrets và Variables](/images/5-Workshop/5.4-neon-deployment/placeholder-github-secrets.png)

### 5.4.6. Tạo GitHub Environment `production`

1. Vào Settings → Environments.
2. Nhấn New environment.
3. Nhập tên `production`.
4. Chọn Configure environment.
5. Tùy chọn: bật Required reviewers.
6. Tùy chọn: bật Wait timer nếu cần độ trễ trước khi deploy.

![Hình 6. Tạo GitHub Environment production](/images/5-Workshop/5.4-neon-deployment/placeholder-environment.png)

### 5.4.7. Tạo ECR repositories

Pipeline cần 2 repository để lưu image backend và frontend.

#### Cách 1: dùng script có sẵn

```powershell
cd aws_04_deploy
.\01_create_ecr_repos.ps1
```

#### Cách 2: dùng AWS CLI

```bash
aws ecr create-repository --repository-name neonfoodmap-backend --region ap-southeast-1
aws ecr create-repository --repository-name neonfoodmap-frontend --region ap-southeast-1
```

![Hình 7. Tạo ECR repositories](/images/5-Workshop/5.4-neon-deployment/placeholder-ecr.png)

### 5.4.8. Tạo ECS cluster và service

1. Mở ECS Console.
2. Tạo cluster `neonfoodmap-cluster`.
3. Chọn kiểu chạy Fargate.
4. Tạo task definition cho backend và frontend.
5. Tạo service tương ứng.
6. Đảm bảo service đã chạy trước khi pipeline deploy lần đầu.

![Hình 8. Tạo ECS cluster](/images/5-Workshop/5.4-neon-deployment/placeholder-ecs-cluster.png)

### 5.4.9. Kiểm tra pipeline CI/CD

Pipeline chính gồm 6 job theo thứ tự:

1. `backend-test`
2. `frontend-check`
3. `e2e-tests`
4. `build-and-push`
5. `deploy-backend`
6. `smoke-tests`

#### Trigger policy

- Push vào `main` → chạy toàn bộ pipeline
- Push vào `develop` hoặc `feature/**` → chạy các job test cơ bản
- Pull request về `main` → chạy các job test cơ bản

![Hình 9. Pipeline CI/CD](/images/5-Workshop/5.4-neon-deployment/placeholder-pipeline.png)

### 5.4.10. Kích hoạt pipeline

1. Chuyển sang nhánh `main`.
2. Merge branch `develop` vào `main`.
3. Push code lên `main` để trigger pipeline.

Ví dụ:

```bash
git checkout main
git merge develop
git push origin main
```

![Hình 10. Trigger pipeline](/images/5-Workshop/5.4-neon-deployment/placeholder-trigger-pipeline.png)

### 5.4.11. Tạo Application Load Balancer và cấu hình routing

#### 5.4.11.1. Tạo security group cho ALB

1. Mở EC2 Console → Security Groups.
2. Chọn Create security group.
3. Thiết lập:
   - Name: `alb-sg`
   - Description: `Security Group cho Public Application Load Balancer`
   - VPC: chọn VPC dự án
4. Thêm inbound rule:
   - HTTP `80` từ `0.0.0.0/0`
   - HTTPS `443` từ `0.0.0.0/0`
5. Giữ outbound rule mặc định.

![Hình 11. Tạo ALB security group](/images/5-Workshop/5.4-neon-deployment/placeholder-alb-sg.png)

#### 5.4.11.2. Tạo target group cho frontend và backend

- `TG-NeonFoodMap-FE` cho frontend
- `TG-NeonFoodMap-BE` cho backend

Các cấu hình chính:

- Target type: `IP addresses`
- Protocol/Port: frontend `HTTP:80`, backend `HTTP:8000`
- Health check protocol: `HTTP`
- Path check: `/` hoặc `/api/health`
- Healthy threshold: `2`
- Unhealthy threshold: `2`
- Interval: `30 seconds`

![Hình 12. Tạo target group](/images/5-Workshop/5.4-neon-deployment/placeholder-target-group.png)

#### 5.4.11.3. Tạo Application Load Balancer

1. Mở EC2 Console → Load Balancers.
2. Chọn Create load balancer → Application Load Balancer.
3. Cấu hình:
   - Name: `ALB-NeonFoodMap`
   - Scheme: `Internet-facing`
   - IP address type: `IPv4`
4. Chọn public subnet phù hợp trong VPC.
5. Chọn security group `alb-sg`.
6. Cấu hình listener `HTTP:80` và route mặc định tới frontend target group.
7. Tạo load balancer.

![Hình 13. Tạo Application Load Balancer](/images/5-Workshop/5.4-neon-deployment/placeholder-alb.png)

#### 5.4.11.4. Tạo listener rule cho API path

1. Mở ALB → Listeners and rules.
2. Chọn listener `HTTP:80`.
3. Thêm rule:
   - Name: `route-backend-api`
   - Condition: `Path /api/*`
   - Action: Forward tới target group backend
4. Lưu rule.

![Hình 14. Tạo listener rule chia route /api](/images/5-Workshop/5.4-neon-deployment/placeholder-listener-rule.png)

### 5.4.12. Liên kết ECS Service với ALB

Để ECS tự động đăng ký task vào target group, cần cấu hình load balancing trong ECS service.

1. Mở ECS Console.
2. Chọn cluster `neonfoodmap-cluster`.
3. Chọn service frontend hoặc backend.
4. Chỉnh sửa hoặc tạo mới service.
5. Trong phần Load balancing:
   - Chọn `Application Load Balancer`
   - Chọn `ALB-NeonFoodMap`
   - Chọn container tương ứng
   - Chọn listener `80:HTTP`
   - Chọn target group tương ứng
6. Lưu lại.

![Hình 15. Kết nối ECS Service với ALB](/images/5-Workshop/5.4-neon-deployment/placeholder-ecs-alb-attach.png)

### 5.4.13. Kiểm tra health check và smoke test sau deploy

Sau khi ECS task chạy xong, kiểm tra trạng thái target group.

Các mục cần kiểm tra:

- Target group frontend chuyển sang `Healthy`
- Target group backend chuyển sang `Healthy`
- ALB DNS có thể truy cập bằng browser
- Endpoint `/api/...` trả về response hợp lệ

Ví dụ kiểm tra:

- Frontend: `http://<alb-dns>`
- Backend: `http://<alb-dns>/api/...`

![Hình 16. Kiểm tra health check và smoke test](/images/5-Workshop/5.4-neon-deployment/placeholder-smoke-test.png)

### 5.4.14. Kết luận triển khai

Sau khi hoàn thành các bước trên, hệ thống đã sẵn sàng hoạt động theo luồng production-like trên AWS:

- Code được kiểm thử bằng CI
- Image được build và push lên ECR
- ECS service chạy bằng Fargate
- ALB phân phối traffic đến frontend và backend đúng route
- Smoke test xác nhận hệ thống có thể đáp ứng request cơ bản

### 5.4.15. Dọn dẹp tài nguyên

Khi kết thúc thực hành, hãy dọn dẹp tài nguyên để tránh phát sinh chi phí.

Các bước chủ yếu:

1. Xóa ECS service
2. Xóa task definition không còn dùng
3. Xóa cluster nếu cần
4. Xóa ECR repositories
5. Xóa load balancer và target group
6. Xóa stack CloudFormation nếu không còn cần thiết

![Hình 17. Dọn dẹp tài nguyên sau triển khai](/images/5-Workshop/5.4-neon-deployment/placeholder-cleanup.png)
