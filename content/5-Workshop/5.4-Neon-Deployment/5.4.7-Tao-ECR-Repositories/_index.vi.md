---
title : "Tạo ECR repositories"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.4.7. </b> "
---

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

