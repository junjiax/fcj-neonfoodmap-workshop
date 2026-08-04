---
title : "ECS Services + Auto-Scaling"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.5.1. </b> "
---

### 5.5.1. ECS Services + Auto-Scaling

Bước 1 & 3: Tạo Backend ECS Service & Rolling Update 
Vào AWS ECS Console $\rightarrow$ chọn Cluster NeonFoodmap-cluster.
Trong tab Services, chọn Create.
Task definition: Chọn neonfoodmap-task-be (family backend của bạn) và Revision mới nhất.
Service name: svc-neonfoodmap-be (hoặc tên theo chuẩn dự án của bạn).
Desired tasks: 2.
Launch type (FARGATE). 

Tích chọn Turn on ECS Exec

Desired tasks: 2. 
Turn on Availability Zone rebalancing 

Deployment Options:
Giữ nguyên Rolling Update

Troubleshooting configuration - recommended 

Mở Turn on ECS Exec
Deployment strategy
 

Networking:
●	VPC: Chọn VPC của dự án NeonFoodmap.
●	Subnets: Chọn 2 Private Subnets.
●	Security Group: Chọn Security Group default.
Load balancing:
Load balancer type: Application Load Balancer.
Select a load balancer: Chọn ALB của bạn (alb-neonfoodmap)
Target group: Select an existing target group $\rightarrow$ chọn TG-NeonFoodMap-BE 

Sau đó ấn create


Cấu hình Auto-Scaling
Vào ECS Console $\rightarrow$ NeonFoodmap-cluster $\rightarrow$ chọn Service svc-neonfoodmap-be.
Chuyển sang tab Service auto scaling $\rightarrow$ Bấm Update.
Tích chọn Use service auto scaling.
Capacity limits:
●	Minimum number of tasks: 2
●	Maximum number of tasks: 6
 


 
Policy 1 (CPU Scaling):
●	Policy type: Target tracking.
●	Policy name: cpu-70-target-tracking.
●	ECS service metric: ECSServiceAverageCPUUtilization.
●	Target value: 70.
●	Scale-out cooldown: 60 seconds.
●	Scale-in cooldown: 300 seconds.


 
1. ECS Service Metric (Chỉ số theo dõi)
●	ECSServiceAverageCPUUtilization: Mức sử dụng CPU trung bình của tất cả các Tasks đang chạy trong Service.
●	ECSServiceAverageMemoryUtilization: Mức sử dụng Bộ nhớ (RAM) trung bình của tất cả các Tasks.
👉 Ý nghĩa: AWS sẽ liên tục đo đạc CPU/RAM trung bình để quyết định xem hệ thống đang rảnh hay đang gánh tải nặng.
2. Target Value (Mức ngưỡng mục tiêu)
●	70% (với CPU) hoặc 80% (với Memory).
👉 Ý nghĩa: Đây là mức tải lý tưởng mà bạn muốn giữ cho hệ thống.
●	Nếu tải tăng vượt ngưỡng (VD: CPU > 70%): Auto Scaling sẽ nhận thấy hệ thống đang làm việc quá sức $\rightarrow$ Tự động Scale-out (bật thêm Tasks mới: 2 $\rightarrow$ 3 $\rightarrow$ 4...) để chia bớt tải.
●	Nếu tải giảm xuống dưới ngưỡng (VD: CPU < 70%): Auto Scaling nhận thấy hệ thống đang dư thừa tài nguyên $\rightarrow$ Tự động Scale-in (tắt bớt Tasks thừa đi) để tiết kiệm chi phí.
3. Scale-out Cooldown Period: 60 seconds (Thời gian chờ khi tăng Task)
👉 Ý nghĩa: Khoảng thời gian trì hoãn giữa 2 lần tăng số lượng Task.
●	Sau khi Auto Scaling vừa bật thêm 1 Task mới, nó sẽ đợi 60 giây để Task mới đó kịp khởi động hoàn tất, nhận traffic và giúp hạ tải CPU/RAM xuống.
●	Hết 60 giây, nếu CPU vẫn nằm trên 70%, nó mới tiếp tục bật thêm Task thứ 3, thứ 4... (tránh việc bật dồn dập quá nhiều Tasks cùng một lúc).
4. Scale-in Cooldown Period: 300 seconds (5 phút) (Thời gian chờ khi giảm Task)
👉 Ý nghĩa: Khoảng thời gian trì hoãn giữa 2 lần tắt bớt Task.
●	Khi lượng truy cập giảm xuống và CPU < 70%, Auto Scaling sẽ chờ đúng 5 phút trước khi quyết định tắt bớt 1 Task.
●	Vì sao thời gian này lâu hơn (5 phút)? Để tránh tình trạng "trập trùng" (Flapping) — vừa tắt Task xong được vài giây thì khách lại truy cập đông, phải bật lại Task mới, gây mất ổn định ứng dụng và tốn thời gian khởi động lại container.

  
 
