---
title : "Khai báo Secrets và Variables trên GitHub"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.4.5. </b> "
---

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

