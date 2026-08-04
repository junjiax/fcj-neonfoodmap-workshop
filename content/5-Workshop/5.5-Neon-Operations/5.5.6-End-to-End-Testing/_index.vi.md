---
title : "End-to-End Testing"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.5.6. </b> "
---

### 5.5.6. End-to-End Testing

Mục tiêu kiểm thử: 
-	Kiểm thử toàn bộ luồng hoạt động hệ thống phía người dùng (frontend) kết nối thông qua Application Load Balancer (ALB) đến Backend (ECS) và các dịch vụ lưu trữ/CDN (S3, Cloudfront, RDS, MySQL).
-	Đảm bảo không có lỗi, liên kết hỏng hoặc sự cố dữ liệu ở các tính năng cốt lõi.

Các kịch bản kiểm thử chi tiết:

1. Test user registration → login flow
Mục tiêu	Đảm bảo login/signup thành công
Quy trình	1. Truy cập web qua Cloudfront.
2. Vào trang Settings, chọn “Đăng nhập tài khoản khác” và nhấn Tạo tài khoản.
3. Điền thông tin đầy đủ vào form.
4. Sử dụng tài khoản vừa tạo để thực hiện Đăng nhập. 
Kết quả mong đợi	Người dùng thanh toán thành công, cập nhật trạng thái đơn hàng.
Trường hợp ngoại lệ	TH1: Không mở được cổng giao dịch do trục trặc
TH2: Điền sai thông tin nên không thanh toán
TH3: Đăng nhập thất bại do mật khẩu không chính xác
 
Màn hình đăng ký
 
Màn hình đăng nhập

2. Test browse POIs + fetch descriptions
Mục tiêu	Kiểm thử thông khả năng tải danh sách điểm đến và lấy thông tin mô tả
Quy trình	1. Tại trang chủ, lướt xem các POI trong bản đồ.
2. Chọn 1 POI để xem thông tin chi tiết
Kết quả mong đợi	Dữ liệu địa điểm hiển thị đầy đủ, hình ảnh và đoạn văn bản mô tả tải nhanh chóng không bị lỗi kết nối API Backend.
Trường hợp ngoại lệ	TH1: Lỗi mất địa điểm khi reload trang (hiếm)

 
Màn hình trang chính
3. Test audio playback via CloudFront
Mục tiêu	Đảm bảo các tệp âm thanh phát mượt mà thông qua mạng lưới CDN CloudFront
Quy trình	1. Tại trang chủ, chọn 1 POI để nghe thuyết minh
2. Âm thanh tự phát khi nhấp vào và có thể kiểm soát theo nút Phát âm thanh.
Kết quả mong đợi	Âm thanh phát trực tuyến nhanh, ổn định, không bị giật lag, đúng tệp mong đợi.
Trường hợp ngoại lệ	TH1: Tệp đứng hình khoảng thời gian ngắn do chưa được tạo sẵn và trong quá trình generate tts (phương án phòng TH tệp âm thanh gốc bị xóa)
TH2: Lỗi phát tệp không như mong đợi (lộn giọng đọc cho ngôn ngữ) (đã fix)

 
Màn hình POI đang phát thuyết minh
 
Màn hình POI đang ngừng thuyết minh

4. Test tour booking flow
Mục tiêu	Kiểm thử tính năng đặt tour
Quy trình	1. Tại trang Tour, chọn một Tour (Mở khóa với Tour premium) và nhấn Bắt đầu hành trình.
2. Người dùng di chuyển đến đến các địa điểm trong tour chỉ định
Kết quả mong đợi	Hệ thống tự phát tệp thuyết minh và cập nhật trạng thái hành trình khi người dùng di chuyển đến một địa điểm trong Tour.
Trường hợp ngoại lệ	TH1: Không thể book Tour do chưa mở khóa các Tour Premium.
 
Màn hình TOUR Premium chưa mở khóa
5. Test payment integration (Sandbox)
Mục tiêu	Kiểm thử cổng thanh toán
Quy trình	1. Tiến hành thanh toán một dịch vụ/đơn hàng bất kỳ trên hệ thống.
2. Sử dụng thông tin tài khoản paypal hoặc thẻ thanh toán.
3. Tiến hành điền thông tin và nhấn xác nhận.
Kết quả mong đợi	Thanh toán thành công, trạng thái đơn hàng cập nhật.
Trường hợp ngoại lệ	TH1: Không thể thanh toán do cung cấp không đủ thông tin.
TH2: Không thể thanh toán do cung cấp sai thông tin.
TH3: Không thể thanh toán do không đủ số tiền thanh toán.
TH4: Không thể thanh toán do thiết bị đang trong trạng thái offline.

6. Test error scenarios (invalid data, timeouts)
Mục tiêu	Đảm bảo cơ chế xử lý ngoại lệ thân thiện người dùng
Quy trình	1. Nhập dữ liệu không hợp lệ vào các form đăng ký/đặt chỗ (Invalid data).
2. Kiểm tra hành vi của ứng dụng khi gặp sự cố độ trễ mạng hoặc timeout.
Kết quả mong đợi	Giao diện hiển thị thông báo lỗi rõ ràng, dễ hiểu, giúp người dùng biết cách khắc phục mà không làm sập ứng dụng
Trường hợp ngoại lệ	

7. Test mobile responsiveness
Mục tiêu	Đảm bảo hoạt động đa nền tảng (Desktop, Mobile)
Quy trình	1. Sử dụng công cụ Developer Tools trên trình duyệt (hoặc thiết bị thực tế) để giả lập các kích thước màn hình di động khác nhau.
2. Kiểm tra UI, UX.
Kết quả mong đợi	 Giao diện co giãn linh hoạt, không bị tràn viền hay che khuất các thành phần quan trọng.
Trường hợp ngoại lệ	

 
Màn hình khi hoạt động trên điện thoại
 
Màn hình khi hoạt động trên máy tính
Tổng kết: Hầu hết trường hợp kiểm thử đều hoạt động đúng như kỳ vọng.
