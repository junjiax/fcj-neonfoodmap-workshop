---
title: "Worklog Tuần 4"
date: 2026-07-13
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

---

### Mục tiêu tuần 4:

**Nhiệm vụ cá nhân:** Thiết lập và cấu hình Amazon S3 Bucket, S3 Object, Lifecycle Rules và IAM Policy/Role liên quan đến quyền truy cập S3.

Trong tuần 4, em tập trung tìm hiểu và triển khai dịch vụ **Amazon Simple Storage Service (S3)** nhằm phục vụ việc lưu trữ và phân phối các tài nguyên của hệ thống. Nội dung thực hiện bao gồm:

- Tìm hiểu cơ chế lưu trữ **Object Storage** của Amazon S3, cấu trúc **Bucket – Object – Key** và cách tổ chức dữ liệu trong S3.
- Tìm hiểu các **Storage Class** của S3 và mục đích sử dụng của từng loại trong các trường hợp lưu trữ khác nhau.
- Tìm hiểu **Lifecycle Rules** để tự động quản lý vòng đời của Object, hỗ trợ chuyển đổi Storage Class hoặc xử lý Object theo thời gian lưu trữ.
- Tìm hiểu cơ chế phân quyền truy cập S3 thông qua **IAM User, IAM Policy và IAM Role**, đồng thời xác định quyền cần thiết cho từng thành phần trong hệ thống.
- Tạo và cấu hình S3 Bucket phục vụ việc lưu trữ các tài nguyên của hệ thống, đặc biệt là các tài nguyên tĩnh được sử dụng bởi phía Front-end.
- Cấu hình **Object Ownership** và các thiết lập bảo mật của Bucket nhằm hạn chế việc truy cập trái phép vào tài nguyên.
- Kiểm tra quá trình upload, lưu trữ và truy xuất Object trên S3 sau khi hoàn tất cấu hình.
- Đối chiếu cấu hình thực tế với kiến trúc hệ thống để đảm bảo S3 có thể tích hợp với các thành phần AWS khác trong các nhiệm vụ tiếp theo.
- Ghi nhận kết quả triển khai, các vấn đề phát sinh và cập nhật tài liệu hướng dẫn triển khai.

### Các công việc cần triển khai trong tuần:

| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                                                                                      |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Tiếp nhận nhiệm vụ, yêu cầu và tiêu chí hoàn thành từ chuyên gia hướng dẫn.<br>- Phân tích kiến trúc hệ thống để xác định vai trò của S3 và vị trí của S3 trong luồng xử lý tài nguyên.<br>- Tìm hiểu cấu trúc Bucket, Object, Key và các khái niệm cơ bản của Amazon S3.<br>- Xác định loại dữ liệu cần lưu trữ trên S3 và yêu cầu về quyền truy cập đối với từng loại tài nguyên.                                                                                                                                | 13/07/2026   | 13/07/2026      | https://aws.amazon.com/vi/s3/ <br> https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html                                                                   |
| 3   | - Tạo S3 Bucket theo yêu cầu của task.<br>- Cấu hình các thông số cơ bản của Bucket như Region, Object Ownership và các thiết lập Block Public Access phù hợp với kiến trúc hệ thống.<br>- Thực hiện tạo và upload S3 Object để kiểm tra khả năng lưu trữ dữ liệu.<br>- Tìm hiểu và cấu hình Lifecycle Rule nhằm quản lý vòng đời Object.<br>- Xác định các quyền IAM cần thiết để thực hiện các thao tác với S3 Bucket và Object.<br>- Kiểm tra quyền truy cập thông qua IAM Policy/Role theo yêu cầu của hệ thống. | 14/07/2026   | 14/07/2026      | https://docs.aws.amazon.com/AmazonS3/latest/userguide/create-bucket-overview.html <br> https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html |
| 4   | - Kiểm tra hoạt động của S3 Bucket sau khi hoàn tất cấu hình.<br>- Kiểm tra quá trình upload, lưu trữ và truy xuất Object.<br>- Kiểm tra quyền truy cập bằng IAM Role/Policy và xác định các thao tác được phép thực hiện.<br>- Kiểm tra Lifecycle Configuration đã được áp dụng đúng theo yêu cầu.<br>- Phân tích và khắc phục các lỗi liên quan đến quyền IAM hoặc cấu hình Bucket nếu phát sinh.<br>- Điều chỉnh lại cấu hình nhằm đảm bảo tài nguyên hoạt động đúng với kiến trúc đã thiết kế.                   | 15/07/2026   | 15/07/2026      | https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html <br> https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html              |
| 5   | - Thực hiện kiểm thử lại toàn bộ cấu hình S3 sau khi điều chỉnh.<br>- Kiểm tra khả năng lưu trữ và truy xuất Object theo đúng quyền được cấp.<br>- Đối chiếu cấu hình thực tế với yêu cầu và tiêu chí hoàn thành của task.<br>- Kiểm tra khả năng sử dụng S3 làm nơi lưu trữ tài nguyên tĩnh cho hệ thống Front-end.<br>- Ghi nhận kết quả kiểm thử và xác nhận các tiêu chí của nhiệm vụ đã được đáp ứng.                                                                                                           | 16/07/2026   | 16/07/2026      | https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingObjects.html                                                                                                 |
| 6   | - Tổng hợp kết quả triển khai S3 Bucket, Object, Lifecycle và IAM.<br>- Hoàn thiện tài liệu hướng dẫn triển khai, cấu hình và kiểm thử.<br>- Bổ sung hình ảnh minh họa cho từng bước thực hiện.<br>- Ghi nhận các lỗi hoặc vấn đề phát sinh trong quá trình triển khai và cách xử lý.<br>- Rà soát lại cấu hình để đảm bảo tính nhất quán với kiến trúc tổng thể của hệ thống.<br>- Chuẩn bị kiến thức và môi trường cho nhiệm vụ tiếp theo.                                                                         | 17/07/2026   | 17/07/2026      | https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html                                                                                                      |

### Kết quả đạt được tuần 4:

Sau khi hoàn thành các nhiệm vụ được giao, em đạt được các kết quả sau:

- Hoàn thành việc **tạo và cấu hình S3 Bucket** theo yêu cầu của nhiệm vụ.
- Hiểu được mô hình lưu trữ **Object Storage** của Amazon S3 và mối quan hệ giữa Bucket, Object và Key.
- Thực hiện được các thao tác cơ bản với S3 Object như upload, kiểm tra và truy xuất dữ liệu.
- Hiểu và thực hiện cấu hình **Object Ownership** nhằm quản lý quyền sở hữu đối với các Object được lưu trữ trong Bucket.
- Hiểu vai trò của **Block Public Access** trong việc hạn chế truy cập công khai ngoài ý muốn đối với tài nguyên S3.
- Tìm hiểu và cấu hình **Lifecycle Rule** để quản lý vòng đời của Object theo yêu cầu lưu trữ.
- Hiểu cách sử dụng **IAM Policy và IAM Role** để cấp quyền cho các thành phần cần thao tác với S3.
- Thực hiện kiểm thử quyền truy cập và xác nhận các thao tác được thực hiện đúng theo chính sách đã cấu hình.
- Kiểm tra thành công việc lưu trữ tài nguyên tĩnh trên S3, tạo nền tảng cho việc tích hợp S3 với các thành phần phục vụ Front-end và phân phối nội dung ở các bước triển khai tiếp theo.
- Sẵn sàng tiếp tục triển khai các thành phần AWS tiếp theo trong kiến trúc hệ thống.
