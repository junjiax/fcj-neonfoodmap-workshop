---
title: "Worklog Tuần 1"
date: 2026-06-22
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

---

### Mục tiêu tuần 1:

**Nhiệm vụ cá nhân:** Làm quen với môi trường thực tập, xây dựng nền tảng kiến thức về điện toán đám mây và AWS, thực hành các thao tác cơ bản trên AWS Management Console và AWS CLI.

Trong tuần đầu tiên, em tập trung tìm hiểu các kiến thức nền tảng cần thiết trước khi tham gia triển khai hệ thống trên AWS. Nội dung học tập và thực hành bao gồm:

- Tìm hiểu tổng quan về **điện toán đám mây (Cloud Computing)**, đặc điểm và lợi ích của việc sử dụng tài nguyên điện toán thông qua Internet.
- Tìm hiểu các mô hình cung cấp dịch vụ Cloud:
  - **IaaS (Infrastructure as a Service):** Cung cấp hạ tầng như máy chủ, mạng và lưu trữ dưới dạng dịch vụ.
  - **PaaS (Platform as a Service):** Cung cấp môi trường và nền tảng để phát triển, triển khai ứng dụng.
  - **SaaS (Software as a Service):** Cung cấp phần mềm hoàn chỉnh để người dùng sử dụng thông qua Internet.

- Tìm hiểu về **AWS**, các nhóm dịch vụ chính và vai trò của AWS trong việc cung cấp hạ tầng Cloud.
- Tìm hiểu về doanh nghiệp, môi trường làm việc, nội quy và quy trình làm việc trong chương trình thực tập **FCAJ**.
- Tìm hiểu chương trình đào tạo, lộ trình học tập và phương thức tiếp nhận nhiệm vụ trong quá trình thực tập.
- Tìm hiểu **AWS Global Infrastructure**, bao gồm:
  - Region.
  - Availability Zone.
  - Cách AWS tổ chức và phân bố hạ tầng trên phạm vi toàn cầu.

- Tìm hiểu các khái niệm nền tảng của **AWS Foundation** và mối quan hệ giữa các nhóm dịch vụ Core Services.
- Làm quen với **AWS Management Console**, cách lựa chọn Region và quản lý tài nguyên AWS theo từng Region.
- Tìm hiểu mô hình chi phí **Pay-as-you-go**, trong đó chi phí được tính dựa trên lượng tài nguyên thực tế sử dụng.
- Tìm hiểu **AWS Shared Responsibility Model**, phân biệt trách nhiệm bảo mật của AWS và trách nhiệm bảo mật của khách hàng.
- Tìm hiểu các kiến thức cơ bản về **IAM**, bao gồm User, Group, Role, Policy và nguyên tắc cấp quyền tối thiểu (**Least Privilege**).
- Làm quen với **AWS CLI**, cách cấu hình thông tin xác thực và thực hiện các thao tác quản lý tài nguyên thông qua dòng lệnh.
- Tìm hiểu tổng quan về **Amazon EC2**, Elastic IP và EBS.
- Tìm hiểu **Amazon VPC** và các thành phần cơ bản như VPC, Subnet, Route Table, Internet Gateway và Security Group.
- Thực hành tạo và kết nối EC2 để củng cố kiến thức về Compute, Networking và Storage trên AWS.

### Các công việc cần triển khai trong tuần:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                                                                                                 |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Tìm hiểu mục tiêu, nội dung và kế hoạch của chương trình thực tập FCAJ.<br>- Làm quen với môi trường làm việc và các thành viên trong chương trình, tìm hiểu nội quy, quy định và quy trình làm việc tại đơn vị thực tập.<br>- Nghiên cứu tổng quan về điện toán đám mây và các mô hình cung cấp dịch vụ IaaS, PaaS, SaaS. Khái niệm Pay-as-you-go và Shared Responsibility Model của AWS.                                                                            | 22/06/2026   | 22/06/2026      | https://aws.amazon.com/what-is-cloud-computing/ https://aws.amazon.com/types-of-cloud-computing/                                                                                   |
| 3   | - Tìm hiểu tổng quan về AWS và các nhóm dịch vụ Cloud phổ biến.<br>- Nghiên cứu AWS Global Infrastructure, Region và Availability Zone. <br>- Tìm hiểu IAM User, Policy, Role và nguyên tắc Least Privilege.<br>- Làm quen với cách quản lý tài nguyên theo Region trên AWS Management Console.                                                                                                                                                                         | 23/06/2026   | 23/06/2026      | https://aws.amazon.com/about-aws/global-infrastructure/ <br> https://aws.amazon.com/iam/ <br> https://aws.amazon.com/console/                                                      |
| 4   | - Thiết lập môi trường AWS phục vụ quá trình học tập và thực hành.<br>- Tạo và cấu hình tài khoản AWS theo hướng dẫn của chương trình.<br>- Làm quen với AWS Management Console.<br>- Tìm hiểu cách lựa chọn Region và kiểm tra tài nguyên theo từng Region.<br>- Cài đặt AWS CLI trên máy tính.<br>- Cấu hình AWS CLI với thông tin xác thực, Region và các thiết lập cần thiết.<br>- Thực hiện các lệnh CLI cơ bản để kiểm tra thông tin tài khoản và môi trường AWS. | 24/06/2026   | 24/06/2026      | https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html <br> https://cloudjourney.awsstudygroup.com/                                                                |
| 5   | - Tìm hiểu kiến trúc và thành phần cơ bản của Amazon EC2.<br>- Nghiên cứu Instance Type, AMI và EBS.<br>- Tìm hiểu các phương thức kết nối đến EC2, tập trung vào kết nối SSH.<br>- Tìm hiểu Security Group và vai trò của nó trong kiểm soát lưu lượng đến EC2.<br>- Tìm hiểu Elastic IP và trường hợp sử dụng khi cần địa chỉ IPv4 cố định cho tài nguyên.                                                                                                            | 25/06/2026   | 25/06/2026      | https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html <br> https://cloudjourney.awsstudygroup.com/ <br> https://docs.aws.amazon.com/vpc/latest/userguide/vpc-eips.html |
| 6   | - Thực hành tạo một EC2 Instance trong AWS Management Console.<br>- Lựa chọn AMI và Instance Type phù hợp với môi trường thực hành.<br>- Cấu hình Network, Subnet và Security Group cho EC2.<br>- Thực hiện kết nối SSH đến EC2 Instance.<br>- Kiểm tra trạng thái và tài nguyên của EC2 sau khi khởi tạo.<br>- Thực hành gắn EBS Volume vào EC2 và kiểm tra khả năng sử dụng Storage.<br>- Tổng hợp kiến thức đã học và ghi nhận kết quả thực hành trong tuần.         | 26/06/2026   | 26/06/2026      | https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html <br> https://cloudjourney.awsstudygroup.com/                                                               |

### Kết quả đạt được tuần 1:

Sau khi hoàn thành các nhiệm vụ được giao, em đạt được các kết quả sau:

- Hiểu được khái niệm **Cloud Computing**, các đặc điểm cơ bản và lợi ích của việc sử dụng hạ tầng Cloud.
- Phân biệt được ba mô hình cung cấp dịch vụ:
  - **IaaS**.
  - **PaaS**.
  - **SaaS**.

- Hiểu được tổng quan về **AWS** và các nhóm dịch vụ phổ biến như Compute, Storage, Networking và Database.
- Nắm được cấu trúc **AWS Global Infrastructure**, đặc biệt là khái niệm Region và Availability Zone.
- Hiểu được vai trò của Region trong việc xác định vị trí triển khai tài nguyên và Availability Zone trong việc xây dựng kiến trúc có khả năng chịu lỗi.
- Hiểu nguyên tắc **Pay-as-you-go** và các yếu tố cơ bản ảnh hưởng đến chi phí sử dụng dịch vụ AWS.
- Nắm được **Shared Responsibility Model**, qua đó phân biệt trách nhiệm bảo mật của AWS đối với hạ tầng Cloud và trách nhiệm của khách hàng đối với tài nguyên, dữ liệu và cấu hình sử dụng.
- Làm quen với các thành phần cơ bản của **IAM**, bao gồm User, Role và Policy, đồng thời hiểu được nguyên tắc cấp quyền theo **Least Privilege**.
- Làm quen với **AWS Management Console** và thực hiện được các thao tác cơ bản để tìm kiếm, cấu hình và quản lý tài nguyên AWS.
- Cài đặt và cấu hình thành công **AWS CLI**, bao gồm các thiết lập liên quan đến thông tin xác thực và Region.
- Thực hiện được các thao tác cơ bản bằng AWS CLI để kiểm tra thông tin tài khoản và tài nguyên AWS.
- Hiểu được kiến trúc cơ bản của **Amazon EC2**, bao gồm Instance, AMI, EBS, Security Group và Elastic IP.
- Thực hành thành công việc tạo và cấu hình **EC2 Instance**.
- Thực hiện kết nối **SSH** đến EC2 và kiểm tra hoạt động của Instance.
- Thực hành gắn **EBS Volume** vào EC2 và kiểm tra tài nguyên lưu trữ.
- Nắm được các thành phần cơ bản của **Amazon VPC** và mối quan hệ giữa VPC, Subnet, Route Table, Internet Gateway và Security Group.
- Bước đầu hình thành tư duy triển khai ứng dụng trên AWS theo hướng kết hợp **Compute, Networking, Storage và Security**.
- Làm quen với môi trường làm việc, quy trình tiếp nhận nhiệm vụ và phương thức học tập trong chương trình thực tập FCAJ.
- Xây dựng được nền tảng kiến thức và kỹ năng thực hành cần thiết để tiếp tục triển khai các dịch vụ AWS chuyên sâu hơn trong những tuần tiếp theo.
