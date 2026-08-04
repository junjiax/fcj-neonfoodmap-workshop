---
title : "Chuẩn bị mã nguồn và cấu trúc dự án"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.4.1. </b> "
---

### 5.4.1. Chuẩn bị mã nguồn và cấu trúc dự án

Trước khi triển khai, hãy đảm bảo repo đã có cấu trúc như sau:

```text
NeonFoodmap/
├── .github/
│   └── workflows/
│       └── deploy.yml
├── backend/
│   ├── Dockerfile
│   ├── requirements.txt
│   └── config/
│       ├── settings.py
│       └── settings_test.py
├── frontend/
│   ├── Dockerfile
│   ├── package.json
│   └── playwright.config.ts
└── neonfoodmap-iam-setup.yaml
```

Các kiểm tra cần có trước khi tiếp tục:

- `backend/Dockerfile` build được local
- `frontend/Dockerfile` build được local
- `backend/config/settings_test.py` dùng SQLite in-memory
- `frontend` có script `npm run lint` và `npm run build`
- `.github/workflows/deploy.yml` đã tồn tại trong repo

![Hình 1. Cấu trúc repo chuẩn bị triển khai](/images/5-Workshop/5.4-neon-deployment/placeholder-repo-structure.png)

