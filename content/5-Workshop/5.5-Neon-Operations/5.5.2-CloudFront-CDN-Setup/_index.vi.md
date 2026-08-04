---
title : "CloudFront + CDN Setup"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.5.2. </b> "
---

### 5.5.2. CloudFront + CDN Setup 

Điền thông số chi tiết 
Distribution name:
●	Nhập tên để dễ quản lý, ví dụ: neonfoodmap-frontend-cdn (hoặc để mặc định tùy bạn).
Description - optional:
●	Có thể bỏ trống hoặc nhập: CloudFront CDN for NeonFoodmap Frontend and API.
Distribution type:
●	Giữ nguyên tùy chọn Single website or app (như hệ thống đang tích sẵn).
Domain (Route 53 managed domain - optional):
●	BỎ TRỐNG (Không nhập gì cả vì bạn dùng URL mặc định *.cloudfront.net do AWS cấp).

 

Origin type:
●	Đã chọn đúng Amazon S3.
S3 origin:
●	Đã chọn đúng bucket neonfoodmap-frontend-dev.s3.ap-southeast-1.amazonaws.com.
Origin path - optional:
●	Bỏ trống (không nhập /path).
Allow private S3 bucket access to CloudFront:
●	Giữ tích chọn Allow private S3 bucket access to CloudFront - Recommended (đây chính là tính năng Origin Access Control - OAC, giúp bảo mật S3 bucket để người dùng không thể tự tiện vào S3 trực tiếp mà bắt buộc phải đi qua CloudFront).
Origin settings:
●	Để mặc định Use recommended origin settings.
Cache settings:
●	Để mặc định Use recommended cache settings tailored to serving S3 content.

 
Lưu ý: Sau khi khởi tạo, vào Distributions của Cloudfront và truy cập Distribution vừa khởi tạo. Chọn mục Origins, nhấn chỉnh sửa Elastic Load Balancing được liên kết ở bước khởi tạo trước và thay đổi Protocol sang HTTP only. (Mục đích: Đảm bảo không xảy ra lỗi 400 (Bad Request) do request  gửi lên từ trình duyệt không đúng định dạng mà Backend/API mong đợi ).
 
