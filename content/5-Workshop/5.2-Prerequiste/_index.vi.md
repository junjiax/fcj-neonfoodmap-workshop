---

title : "Các bước chuẩn bị"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
-----------------------

### 5.2. Các bước chuẩn bị

Trước khi bắt đầu quá trình triển khai NeonFoodMap trên AWS, cần chuẩn bị tài khoản AWS, mã nguồn, môi trường phát triển cục bộ, repository GitHub và các quyền truy cập AWS cần thiết.

Phần này chỉ tập trung vào các yêu cầu về môi trường và quyền truy cập. Việc tạo và cấu hình các tài nguyên AWS như IAM, VPC, RDS, S3, ECR, ECS và CloudWatch sẽ được thực hiện trong các phần triển khai chi tiết tiếp theo.

---

### 5.2.1. Tài khoản AWS và Region

Cần có một tài khoản AWS để triển khai và vận hành ứng dụng NeonFoodMap.

1. Truy cập **AWS Management Console**.

2. Đăng nhập bằng tài khoản AWS có đủ quyền thực hiện quá trình triển khai.

3. Thiết lập AWS Region:

```text
Asia Pacific (Singapore) - ap-southeast-1
```

4. Kiểm tra Region đã chọn được hiển thị thống nhất trên AWS Management Console trước khi tạo tài nguyên.

Dự án sử dụng `ap-southeast-1` làm Region triển khai chính. Các tài nguyên AWS được tạo trong các bước tiếp theo sẽ được triển khai tại Region này, trừ khi có yêu cầu khác.

> Các tài nguyên AWS chưa được tạo trong phần chuẩn bị này. Phần này chỉ kiểm tra tài khoản AWS và Region triển khai đã sẵn sàng.

---

### 5.2.2. Mã nguồn NeonFoodMap

NeonFoodMap gồm hai thành phần ứng dụng chính:

```text
NeonFoodMap
├── Backend
│   └── Django
│
└── Frontend
    └── React + TypeScript
```

Mã nguồn phải được tải về máy cục bộ trước khi bắt đầu quá trình triển khai.

Clone repository NeonFoodMap:

```bash
git clone https://github.com/HaoWasabi/NeonFoodmap.git
```

Di chuyển vào thư mục dự án:

```bash
cd NeonFoodmap
```

Kiểm tra trạng thái mã nguồn:

```bash
git status
```

Repository phải chứa đầy đủ mã nguồn cần thiết cho cả Backend và Frontend.

Mã nguồn sẽ được sử dụng trong các bước tiếp theo để:

* Cài đặt dependency cho Backend và Frontend.
* Chạy ứng dụng trên môi trường cục bộ.
* Build Docker Image.
* Push Docker Image lên Amazon ECR.
* Thực thi pipeline CI/CD thông qua GitHub Actions.

---

### 5.2.3. Môi trường phát triển

Môi trường phát triển cục bộ cần có các công cụ phục vụ việc phát triển, kiểm thử và đóng gói ứng dụng NeonFoodMap.

Các công cụ cần thiết:

```text
Development Environment
├── Git
├── Python
├── Python Virtual Environment
├── Node.js / npm
└── Docker
```

#### Git

Git được sử dụng để clone mã nguồn NeonFoodMap và quản lý các thay đổi trong quá trình phát triển.

Kiểm tra phiên bản Git đã cài đặt:

```bash
git --version
```

Ví dụ:

```text
git version 2.x.x
```

Nếu lệnh trả về phiên bản Git, Git đã sẵn sàng để sử dụng.

---

#### Python

Python được sử dụng để chạy Backend Django của NeonFoodMap.

Kiểm tra phiên bản Python:

```bash
python --version
```

Ví dụ:

```text
Python 3.12.x
```

Nếu hệ thống sử dụng lệnh `python3`, thực hiện:

```bash
python3 --version
```

Phiên bản Python cần tương thích với phiên bản được yêu cầu bởi dự án Backend.

---

#### Môi trường ảo Python

Môi trường ảo Python được sử dụng để tách biệt các dependency của Backend khỏi môi trường Python của hệ thống.

Di chuyển vào thư mục Backend:

```bash
cd backend
```

Tạo môi trường ảo:

```bash
python -m venv venv
```

Sau khi tạo, thư mục Backend sẽ có cấu trúc tương tự:

```text
backend/
├── venv/
├── manage.py
├── requirements.txt
├── config/
└── ...
```

Kích hoạt môi trường ảo.

**Windows PowerShell:**

```powershell
.\venv\Scripts\Activate.ps1
```

**Windows Command Prompt:**

```cmd
venv\Scripts\activate
```

**Linux/macOS:**

```bash
source venv/bin/activate
```

Sau khi kích hoạt thành công, `(venv)` sẽ xuất hiện ở đầu dòng lệnh:

```text
(venv) PS D:\NeonFoodMap\backend>
```

Cập nhật `pip`:

```bash
python -m pip install --upgrade pip
```

Cài đặt các dependency của Backend từ `requirements.txt`:

```bash
pip install -r requirements.txt
```

Kiểm tra Django đã được cài đặt:

```bash
python -m django --version
```

Môi trường ảo không được commit lên Git. Thêm dòng sau vào `.gitignore`:

```gitignore
venv/
```

> Môi trường ảo được sử dụng cho quá trình phát triển và kiểm thử trên máy cục bộ. Trong quá trình triển khai ECS, các dependency Python sẽ được cài đặt bên trong Docker Image theo `requirements.txt`.

---

#### Node.js / npm

Node.js và npm được sử dụng để cài đặt dependency và build Frontend React của NeonFoodMap.

Kiểm tra phiên bản Node.js:

```bash
node --version
```

Kiểm tra phiên bản npm:

```bash
npm --version
```

Ví dụ:

```text
Node.js: 22.x.x
npm: 10.x.x
```

Di chuyển vào thư mục Frontend:

```bash
cd frontend
```

Cài đặt dependency cho Frontend:

```bash
npm install
```

Kiểm tra các dependency của Frontend đã được cài đặt thành công.

Sau đó có thể kiểm thử Frontend trên môi trường cục bộ bằng các npm script được cấu hình trong dự án.

---

#### Docker

Docker được sử dụng để build và kiểm thử các Container Image của NeonFoodMap.

Kiểm tra Docker đã được cài đặt:

```bash
docker --version
```

Kiểm tra Docker đang hoạt động:

```bash
docker info
```

Trong các bước tiếp theo, Docker sẽ được sử dụng để đóng gói ứng dụng thành Container Image:

```text
Backend Source Code
        ↓
Docker Build
        ↓
Backend Image
```

và:

```text
Frontend Source Code
        ↓
Docker Build
        ↓
Frontend Image
```

Các Image sau đó sẽ được push lên Amazon ECR và triển khai trên Amazon ECS Fargate.

---

### 5.2.4. GitHub Repository

Mã nguồn NeonFoodMap được lưu trữ tại repository GitHub:

```text
https://github.com/HaoWasabi/NeonFoodmap.git
```

Kiểm tra repository cục bộ đã được kết nối với đúng remote:

```bash
git remote -v
```

Kết quả mong đợi:

```text
origin  https://github.com/HaoWasabi/NeonFoodmap.git (fetch)
origin  https://github.com/HaoWasabi/NeonFoodmap.git (push)
```

Repository sẽ được sử dụng bởi pipeline CI/CD để:

1. Trigger workflow khi code được push hoặc tạo Pull Request.
2. Thực hiện kiểm thử Backend.
3. Kiểm tra Frontend.
4. Thực hiện End-to-End Test.
5. Build Docker Image.
6. Push Image lên Amazon ECR.
7. Deploy ứng dụng lên Amazon ECS.
8. Thực hiện Smoke Test sau khi triển khai.

GitHub Actions Workflow được lưu trong:

```text
.github/
└── workflows/
```

Ở bước này, chỉ cần kiểm tra repository có thể truy cập và mã nguồn có thể được clone thành công. Việc cấu hình chi tiết GitHub Actions, OIDC, ECR và ECS Deployment sẽ được thực hiện trong các phần CI/CD tiếp theo.

---

### 5.2.5. Quyền truy cập AWS cần thiết

Tài khoản AWS được sử dụng cho dự án phải có đủ quyền để tạo và cấu hình các tài nguyên AWS cần thiết cho NeonFoodMap.

Quá trình triển khai sẽ cần truy cập các dịch vụ:

| Dịch vụ AWS            | Mục đích                                                    |
| ---------------------- | ----------------------------------------------------------- |
| IAM                    | Quản lý user, group, policy và role                         |
| VPC                    | Cấu hình mạng cho ứng dụng                                  |
| Amazon RDS             | Cung cấp cơ sở dữ liệu cho ứng dụng                         |
| Amazon S3              | Lưu trữ file ứng dụng và static assets                      |
| Amazon ECR             | Lưu trữ Docker Image                                        |
| Amazon ECS             | Chạy các Container Backend và Frontend                      |
| Elastic Load Balancing | Phân phối lưu lượng truy cập ứng dụng                       |
| Amazon CloudWatch      | Thu thập và giám sát application logs                       |
| AWS Secrets Manager    | Lưu trữ thông tin cấu hình nhạy cảm                         |
| AWS STS                | Cung cấp temporary credentials cho quá trình xác thực CI/CD |

Trước khi bắt đầu triển khai, kiểm tra tài khoản AWS hoặc IAM identity đang sử dụng được cấp quyền truy cập các dịch vụ cần thiết.

Dự án tuân theo nguyên tắc **Least Privilege**, do đó quyền chỉ nên được cấp tương ứng với các thao tác mà từng user, role hoặc thành phần triển khai cần thực hiện.

> Các IAM Policy và Role không được tạo trong phần chuẩn bị này. Việc cấu hình chi tiết sẽ được thực hiện trong phần triển khai IAM.

---

### Kiểm tra Prerequisite

Trước khi chuyển sang các bước triển khai AWS, kiểm tra các yêu cầu sau:

| STT | Yêu cầu                     | Trạng thái                   |
| --- | --------------------------- | ---------------------------- |
| 1   | AWS Account                 | Sẵn sàng                     |
| 2   | AWS Region `ap-southeast-1` | Đã chọn                      |
| 3   | Mã nguồn NeonFoodMap        | Đã có                        |
| 4   | Git                         | Đã cài đặt                   |
| 5   | Python                      | Đã cài đặt                   |
| 6   | Python Virtual Environment  | Đã tạo                       |
| 7   | Backend Dependencies        | Đã cài đặt                   |
| 8   | Node.js / npm               | Đã cài đặt                   |
| 9   | Frontend Dependencies       | Đã cài đặt                   |
| 10  | Docker                      | Đã cài đặt và đang hoạt động |
| 11  | GitHub Repository           | Có thể truy cập              |
| 12  | GitHub Actions Workflow     | Đã có                        |
| 13  | AWS Access                  | Đã được cấp                  |

Sau khi hoàn tất toàn bộ các yêu cầu trên, môi trường đã sẵn sàng để chuyển sang các bước **triển khai chi tiết NeonFoodMap trên AWS**.
