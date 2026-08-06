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

### Bước 1. Tạo ECS Cluster sử dụng AWS Fargate

Trong bước này, chúng ta sẽ tạo một Amazon ECS Cluster sử dụng **AWS Fargate** để triển khai các container của hệ thống NeonFoodMap. AWS Fargate là dịch vụ Serverless dành cho Container, cho phép chạy ứng dụng mà không cần quản lý hoặc cấu hình máy chủ EC2.

1. Đăng nhập vào **AWS Management Console**.

2. Tại thanh tìm kiếm dịch vụ, nhập **Amazon ECS** và chọn dịch vụ **Elastic Container Service (ECS)**.

![Hình 1.](/images/5-Workshop/5.5-Neon-Operations/image001.png)

3. Trong thanh điều hướng bên trái, chọn **Clusters** để xem danh sách các ECS Cluster hiện có.

![Hình 2.](/images/5-Workshop/5.5-Neon-Operations/image002.png)

4. Nhấn **Create Cluster** để bắt đầu tạo một Cluster mới.

![Hình 3.](/images/5-Workshop/5.5-Neon-Operations/image003.png)

5. Tại phần **Infrastructure**, chọn kiểu triển khai:

- **Amazon ECS Managed Instances** (giao diện mới)
- Hoặc **Networking only (AWS Fargate)** nếu sử dụng giao diện cũ.

Workshop này sử dụng **AWS Fargate** nhằm đơn giản hóa việc triển khai Container và loại bỏ nhu cầu quản lý máy chủ EC2.

![Hình 4.](/images/5-Workshop/5.5-Neon-Operations/image004.png)

6. Nhập tên Cluster.

Ví dụ:

```text
neonfoodmap-cluster
```

Tên Cluster nên phản ánh đúng tên dự án để thuận tiện trong việc quản lý nhiều môi trường triển khai.

![Hình 5.](/images/5-Workshop/5.5-Neon-Operations/image005.png)

7. Trong phần **Networking**, chọn **VPC** đã được tạo ở các bước trước.

Sau đó chọn hai Subnet thuộc hai Availability Zone khác nhau.

Ví dụ:

- Public Subnet AZ1
- Public Subnet AZ2

hoặc

- Private Subnet AZ1
- Private Subnet AZ2

Việc triển khai trên nhiều Availability Zone giúp tăng tính sẵn sàng (High Availability), đảm bảo khi một AZ gặp sự cố thì ứng dụng vẫn có thể hoạt động tại AZ còn lại.

![Hình 6.](/images/5-Workshop/5.5-Neon-Operations/image006.png)

![Hình 7.](/images/5-Workshop/5.5-Neon-Operations/image007.png)

![Hình 8.](/images/5-Workshop/5.5-Neon-Operations/image008.png)

8. Kiểm tra lại toàn bộ thông tin cấu hình, bao gồm:

- Cluster Name
- Infrastructure
- VPC
- Availability Zones
- Networking Configuration

![Hình 9.](/images/5-Workshop/5.5-Neon-Operations/image009.png)

9. Nhấn **Create** để tạo ECS Cluster.

AWS sẽ mất khoảng vài chục giây để khởi tạo tài nguyên.

![Hình 10.](/images/5-Workshop/5.5-Neon-Operations/image010.png)

10. Sau khi quá trình tạo hoàn tất, màn hình sẽ hiển thị Cluster vừa tạo cùng trạng thái **Active**.

Tiếp tục mở Cluster để kiểm tra các thành phần như Services, Tasks, Infrastructure và Monitoring nhằm xác nhận Cluster đã được tạo thành công.

![Hình 1.](/images/5-Workshop/5.4-Neon-Deployment/image001.png)

![Hình 2.](/images/5-Workshop/5.4-Neon-Deployment/image002.png)

![Hình 3.](/images/5-Workshop/5.4-Neon-Deployment/image003.png)

![Hình 4.](/images/5-Workshop/5.4-Neon-Deployment/image004.png)

![Hình 5.](/images/5-Workshop/5.4-Neon-Deployment/image005.png)

![Hình 6.](/images/5-Workshop/5.4-Neon-Deployment/image006.png)

![Hình 7.](/images/5-Workshop/5.4-Neon-Deployment/image007.png)

![Hình 8.](/images/5-Workshop/5.4-Neon-Deployment/image008.png)

![Hình 9.](/images/5-Workshop/5.4-Neon-Deployment/image009.png)

![Hình 10.](/images/5-Workshop/5.4-Neon-Deployment/image010.png)

![Hình 11.](/images/5-Workshop/5.4-Neon-Deployment/image011.png)

![Hình 12.](/images/5-Workshop/5.4-Neon-Deployment/image012.png)

![Hình 13.](/images/5-Workshop/5.4-Neon-Deployment/image013.png)

![Hình 14.](/images/5-Workshop/5.4-Neon-Deployment/image014.png)

![Hình 15.](/images/5-Workshop/5.4-Neon-Deployment/image015.png)

---

### Bước 2. Tạo Task Definition cho Backend

Sau khi đã tạo thành công ECS Cluster, bước tiếp theo là tạo **Task Definition** cho ứng dụng Backend.

Task Definition là bản mô tả cấu hình của Container, bao gồm Image, CPU, Memory, Network, Port Mapping, Logging và các biến môi trường. ECS sẽ dựa vào Task Definition để khởi chạy các Container trong quá trình triển khai.

1. Trong giao diện **Amazon ECS**, chọn **Task Definitions** ở thanh điều hướng bên trái.

2. Nhấn **Create new Task Definition**.

![Hình 16.](/images/5-Workshop/5.4-Neon-Deployment/image016.png)

![Hình 17.](/images/5-Workshop/5.4-Neon-Deployment/image017.png)

3. Chọn **Launch Type** là **AWS Fargate**.

AWS Fargate sẽ tự động cấp phát tài nguyên tính toán mà không cần quản lý máy chủ EC2.

![Hình 18.](/images/5-Workshop/5.4-Neon-Deployment/image018.png)

4. Nhập tên Task Definition.

Ví dụ:

```text
backend-task
```

Tên Task Definition nên phản ánh đúng chức năng của dịch vụ để thuận tiện trong quá trình quản lý.

![Hình 19.](/images/5-Workshop/5.4-Neon-Deployment/image019.png)

5. Tại phần **Task Size**, cấu hình tài nguyên cho Task.

Thiết lập:

- CPU: **256 (.25 vCPU)**
- Memory: **512 MiB**

Đây là cấu hình phù hợp cho môi trường Workshop. Khi triển khai thực tế, có thể điều chỉnh CPU và Memory dựa trên nhu cầu xử lý của ứng dụng.

![Hình 20.](/images/5-Workshop/5.4-Neon-Deployment/image020.png)

![Hình 21.](/images/5-Workshop/5.4-Neon-Deployment/image021.png)

6. Trong phần **Container**, chọn **Add container**.

Cấu hình các thông tin sau:

- Container Name:

```text
backend
```

- Image URI

Chọn Image Backend đã được Push lên Amazon ECR.

Ví dụ:

```text
<account-id>.dkr.ecr.ap-southeast-1.amazonaws.com/neonfoodmap-backend:latest
```

- Port Mapping

```text
8000
```

- Essential

Giữ mặc định là **Enabled** để ECS luôn duy trì Container này trong Task.

![Hình 22.](/images/5-Workshop/5.4-Neon-Deployment/image022.png)

![Hình 23.](/images/5-Workshop/5.4-Neon-Deployment/image023.png)

![Hình 24.](/images/5-Workshop/5.4-Neon-Deployment/image024.png)

![Hình 25.](/images/5-Workshop/5.4-Neon-Deployment/image025.png)

![Hình 26.](/images/5-Workshop/5.4-Neon-Deployment/image026.png)

![Hình 27.](/images/5-Workshop/5.4-Neon-Deployment/image027.png)

![Hình 28.](/images/5-Workshop/5.4-Neon-Deployment/image028.png)

![Hình 29.](/images/5-Workshop/5.4-Neon-Deployment/image029.png)

![Hình 30.](/images/5-Workshop/5.4-Neon-Deployment/image030.png)

![Hình 31.](/images/5-Workshop/5.4-Neon-Deployment/image031.png)

![Hình 32.](/images/5-Workshop/5.4-Neon-Deployment/image032.png)

![Hình 33.](/images/5-Workshop/5.4-Neon-Deployment/image033.png)

![Hình 34.](/images/5-Workshop/5.4-Neon-Deployment/image034.png)

![Hình 35.](/images/5-Workshop/5.4-Neon-Deployment/image035.png)

7. Sau khi hoàn tất cấu hình Task Definition, nhấn **Next** để chuyển sang bước tiếp theo.

Kiểm tra lại toàn bộ thông tin cấu hình trước khi lưu Task Definition.

![Hình 36.](/images/5-Workshop/5.4-Neon-Deployment/image036.png)

![Hình 37.](/images/5-Workshop/5.4-Neon-Deployment/image037.png)

![Hình 38.](/images/5-Workshop/5.4-Neon-Deployment/image038.png)

### Bước 3. Tạo Task Definition cho Frontend

1. Chọn **Create new Task Definition**.
2. Đặt tên:

```
frontend-task
```

3. Thiết lập:

- CPU: **256 (.25 vCPU)**
- Memory: **512 MiB**

4. Thêm Container Frontend:

- Image: Image Frontend trên Amazon ECR
- Port Mapping:
  - 80
  - hoặc 3000 (tùy ứng dụng)

5. Hoàn tất việc tạo Task Definition.

---

### Bước 4. Cấu hình CloudWatch Log Groups

1. Trong phần Container của Task Definition, chọn **Logging**.
2. Chọn Log Driver:

```
awslogs
```

3. Đối với Backend:

```
Log Group:
/ecs/backend
```

4. Đối với Frontend:

```
Log Group:
/ecs/frontend
```

5. Thiết lập Region AWS.
6. Đặt Stream Prefix phù hợp, ví dụ:

```
backend
frontend
```

7. Lưu Task Definition.

---

### Bước 5. Thiết lập biến môi trường và Secrets

1. Trong phần Container Definition, chọn **Environment Variables**.
2. Thêm các biến môi trường cần thiết, ví dụ:

- DEBUG
- ALLOWED_HOSTS
- DB_HOST
- DB_NAME
- DB_PORT

3. Trong mục **Secrets**, chọn **Add Secret**.
4. Liên kết các Secret từ AWS Secrets Manager:

- Endpoint Amazon RDS
- Username Database
- Password Database
- API Keys
- JWT Secret
- Các khóa bí mật khác

5. Kiểm tra toàn bộ biến môi trường trước khi lưu.

---

### Bước 6. Tạo Task Execution Role

1. Truy cập dịch vụ **IAM**.
2. Chọn **Roles**.
3. Nhấn **Create Role**.
4. Chọn Trusted Entity:

```
Elastic Container Service Task
```

5. Gán các Policy cần thiết:

- AmazonECSTaskExecutionRolePolicy
- AmazonEC2ContainerRegistryReadOnly
- CloudWatchLogsFullAccess (hoặc quyền ghi Logs phù hợp)
- SecretsManagerReadWrite hoặc quyền chỉ đọc Secrets cần thiết

6. Đặt tên Role, ví dụ:

```
ecsTaskExecutionRole
```

7. Quay lại Task Definition.
8. Chọn Role vừa tạo tại mục **Task Execution Role**.

---

### Bước 7. Tạo ECS Service và kiểm tra Task

1. Mở **ECS Cluster** vừa tạo.
2. Chọn **Create Service**.
![Hình 39.](/images/5-Workshop/5.4-Neon-Deployment/image039.png)

3. Chọn Launch Type:

```
Fargate
```

4. Chọn Task Definition tương ứng.
5. Đặt tên Service:

```
backend-service
```

hoặc

```
frontend-service
```
![Hình 40.](/images/5-Workshop/5.4-Neon-Deployment/image040.png)
![Hình 41.](/images/5-Workshop/5.4-Neon-Deployment/image041.png)

6. Thiết lập:

- Desired Tasks: **2**
- Deployment Type: Rolling Update

7. Chọn VPC và hai Subnet thuộc AZ1 và AZ2.
8. Chọn Security Group phù hợp.
9. Nếu sử dụng Load Balancer, liên kết với Target Group tương ứng.
![Hình 42.](/images/5-Workshop/5.4-Neon-Deployment/image042.png)

10. Nhấn **Create Service**.
![Hình 43.](/images/5-Workshop/5.4-Neon-Deployment/image043.png)

---

### Bước 8. Kiểm tra Task khởi chạy

1. Mở ECS Cluster.
2. Chọn tab **Services**.
3. Kiểm tra trạng thái Service là:

```
Active
```

4. Chọn tab **Tasks**.
5. Xác nhận các Task đều có trạng thái:

```
RUNNING
```

6. Mở **CloudWatch Logs** để kiểm tra Log của Backend và Frontend.
7. Truy cập ứng dụng thông qua DNS của Application Load Balancer (nếu đã cấu hình).
8. Kiểm tra ứng dụng phản hồi thành công và không phát sinh lỗi trong quá trình khởi chạy.
