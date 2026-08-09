---

title: "Event 2"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
----------------------

# Bài thu hoạch “Chung kết Event Cloud Architect”

## Mục Đích Của Sự Kiện

Event Cloud Architect là sự kiện tổng kết và chia sẻ kiến thức về điện toán đám mây, kiến trúc ứng dụng hiện đại và các giải pháp bảo mật trên AWS. Sự kiện tạo cơ hội để các thành viên tham gia chương trình được tiếp cận với kiến thức thực tế từ các chuyên gia, đồng thời giải quyết các bài toán liên quan đến Cloud Architecture.

### Session 1: Chung kết Event Cloud Architect

Tham gia vòng chung kết Event Cloud Architect cùng team, trả lời câu hỏi từ một bộ đề được bốc thăm ngẫu nhiên từ 2 bộ đề cuối cùng do ban tổ chức biên soạn. 

### Session 2: Chia sẻ về thiết kế ứng dụng hiện đại và AWS Security Agent

Anh **Thinh Nguyen** chia sẻ các best practices trong quá trình thiết kế và phát triển ứng dụng hiện đại, đồng thời giới thiệu giải pháp **AWS Security Agent** hỗ trợ phân tích bảo mật mã nguồn theo đặc tả.

Một số vấn đề được đề cập trong session bao gồm:

* Thời gian release sản phẩm kéo dài có thể khiến doanh nghiệp bỏ lỡ cơ hội kinh doanh và phát sinh chi phí.
* Quy trình phát triển hoặc vận hành kém hiệu quả làm giảm năng suất của đội ngũ và tăng chi phí.
* Việc không đáp ứng các yêu cầu về bảo mật và tuân thủ có thể gây ảnh hưởng đến an toàn hệ thống cũng như uy tín của doanh nghiệp.
* Bảo mật cần được xem xét ngay từ quá trình phát triển phần mềm thay vì chỉ thực hiện kiểm tra ở giai đoạn cuối.
* Các công cụ hỗ trợ bằng AI có thể giúp đội ngũ phát triển phát hiện và xử lý một số vấn đề nhanh hơn trong quá trình phát triển.

Qua session này, em hiểu rõ hơn về xu hướng kết hợp giữa Cloud, DevOps, Security và AI trong quy trình phát triển phần mềm hiện đại.

### Session 3: Giới thiệu kiến trúc ứng dụng 3 tầng trên AWS

Anh **Nguyễn Huỳnh Sơn** giới thiệu một mô hình kiến trúc ứng dụng 3 tầng được triển khai trên AWS. Kiến trúc được thiết kế theo hướng phân tách các thành phần hệ thống, triển khai trên nhiều Availability Zone và áp dụng các cơ chế kiểm soát truy cập, giám sát tập trung.

Các nội dung chính bao gồm:

* Phân tách hệ thống thành các tầng nhằm tăng khả năng quản lý và bảo mật.
* Sử dụng VPC và các subnet để tổ chức tài nguyên theo từng lớp mạng.
* Triển khai hệ thống trên nhiều Availability Zone nhằm tăng tính sẵn sàng.
* Sử dụng cơ chế kiểm soát truy cập để hạn chế quyền truy cập giữa các thành phần.
* Sử dụng các dịch vụ monitoring và logging để theo dõi hoạt động của hệ thống.
* Thiết kế kiến trúc có khả năng mở rộng và đáp ứng yêu cầu vận hành thực tế.

Nội dung này giúp em củng cố kiến thức về kiến trúc 3 tầng và hiểu rõ hơn cách kết hợp nhiều dịch vụ AWS để xây dựng một hệ thống có tính sẵn sàng, bảo mật và khả năng giám sát tốt.

## Danh Sách Diễn Giả

* **Thinh Nguyen** – Cloud Engineer | DevOps Engineer | Full-Stack Developer | AWS First Cloud AI Journey
  [LinkedIn của Thinh Nguyen](https://www.linkedin.com/in/thinhnguyen1211/?utm_source=chatgpt.com)

* **Nguyễn Huỳnh Sơn** – Cloud RAN 5G Support Engineer @Endava | AWS Cloud Club Core Team
  [LinkedIn của Nguyễn Huỳnh Sơn](https://www.linkedin.com/in/huynhson081103/?utm_source=chatgpt.com)

## Nội Dung Nổi Bật

### Giới thiệu AWS Security Agent – Phân tích bảo mật mã nguồn

Một trong những nội dung nổi bật của sự kiện là phần giới thiệu về AWS Security Agent và cách ứng dụng các công cụ hiện đại để hỗ trợ quá trình kiểm tra, phân tích bảo mật mã nguồn.

Trong quá trình phát triển phần mềm, một số vấn đề có thể ảnh hưởng trực tiếp đến hoạt động của doanh nghiệp:

| Vấn đề                           | Ảnh hưởng                                                                      |
| -------------------------------- | ------------------------------------------------------------------------------ |
| Thời gian release sản phẩm lâu   | Làm chậm quá trình đưa sản phẩm đến người dùng, có thể bỏ lỡ cơ hội kinh doanh |
| Quy trình hoạt động kém hiệu quả | Giảm năng suất và làm tăng chi phí vận hành                                    |
| Không đảm bảo yêu cầu bảo mật    | Tăng nguy cơ xảy ra sự cố và ảnh hưởng đến uy tín doanh nghiệp                 |
| Phát hiện lỗi bảo mật muộn       | Làm tăng thời gian và chi phí khắc phục                                        |

Qua nội dung được chia sẻ, em nhận thấy bảo mật nên được tích hợp xuyên suốt vòng đời phát triển phần mềm. Việc sử dụng các công cụ hỗ trợ tự động có thể giúp phát hiện sớm các vấn đề, giảm thời gian kiểm tra thủ công và hỗ trợ đội ngũ phát triển cải thiện chất lượng mã nguồn.

### Monitoring

Monitoring là một thành phần quan trọng trong quá trình vận hành hệ thống Cloud. Không chỉ triển khai ứng dụng thành công, người phát triển còn cần theo dõi được tình trạng hoạt động của hệ thống sau khi đưa vào vận hành.

Các nội dung em nhận thức rõ hơn sau session gồm:

* Theo dõi tình trạng hoạt động của các tài nguyên và ứng dụng.
* Thu thập và tập trung log để phục vụ quá trình phân tích.
* Thiết lập cảnh báo khi hệ thống xuất hiện dấu hiệu bất thường.
* Sử dụng dữ liệu monitoring để hỗ trợ xác định nguyên nhân khi xảy ra sự cố.
* Kết hợp monitoring với logging nhằm nâng cao khả năng quan sát hệ thống.

Những nội dung này có tính thực tế cao đối với hệ thống triển khai trên AWS, đặc biệt khi hệ thống sử dụng nhiều dịch vụ như ECS, Load Balancer, RDS và các thành phần mạng.

## Những Gì Học Được

### Tư Duy Thiết Kế

Em hiểu rõ hơn rằng thiết kế kiến trúc Cloud cần bắt đầu từ yêu cầu của hệ thống thay vì lựa chọn dịch vụ trước. Khi xây dựng kiến trúc cần xem xét đồng thời các yếu tố:

* Tính sẵn sàng.
* Khả năng mở rộng.
* Bảo mật.
* Hiệu năng.
* Khả năng giám sát.
* Chi phí vận hành.
* Khả năng bảo trì và mở rộng trong tương lai.

Việc lựa chọn dịch vụ AWS cần dựa trên yêu cầu thực tế và mối quan hệ giữa các thành phần thay vì chỉ sử dụng nhiều dịch vụ để làm cho kiến trúc trở nên phức tạp.

### Kiến Trúc Kỹ Thuật

Qua phần trình bày về kiến trúc ứng dụng 3 tầng, em củng cố được kiến thức về cách tổ chức một hệ thống Cloud theo từng lớp.

Đặc biệt, em hiểu rõ hơn vai trò của việc phân tách mạng, triển khai Multi-AZ và kiểm soát luồng truy cập giữa các thành phần. Đây cũng là những kiến thức có thể áp dụng trực tiếp vào quá trình triển khai dự án NeonFoodmap trong thời gian thực tập.

### Chiến Lược Hiện Đại Hóa

Em nhận thấy hiện đại hóa hệ thống không chỉ đơn giản là đưa một ứng dụng hiện có lên Cloud. Quá trình hiện đại hóa cần xem xét lại kiến trúc, cách triển khai, khả năng tự động hóa, bảo mật và phương thức giám sát.

Việc kết hợp Cloud với các phương pháp như DevOps, CI/CD và các công cụ hỗ trợ AI giúp rút ngắn thời gian phát triển, nâng cao chất lượng phần mềm và cải thiện hiệu quả vận hành.

## Ứng Dụng Vào Công Việc

Những kiến thức thu được từ sự kiện có thể áp dụng trực tiếp vào công việc thực tập và dự án đang triển khai.

Đối với dự án NeonFoodmap, em có thể vận dụng các kiến thức đã học để:

* Phân tích kiến trúc hệ thống trước khi triển khai.
* Phân tách các thành phần frontend, backend và database.
* Sử dụng VPC và subnet để tổ chức tài nguyên theo từng tầng.
* Triển khai ECS Fargate trên nhiều Availability Zone.
* Sử dụng Application Load Balancer để phân phối request đến backend.
* Sử dụng RDS theo hướng tăng tính sẵn sàng.
* Sử dụng Security Group để kiểm soát luồng truy cập.
* Sử dụng CloudWatch để thu thập log, theo dõi metric và thiết lập cảnh báo.
* Kết hợp GitHub Actions, OIDC, AWS STS và ECR để xây dựng quy trình CI/CD.
* Chú trọng bảo mật trong quá trình phát triển và triển khai thay vì chỉ kiểm tra sau khi hoàn thành hệ thống.

Qua đó, em có thể kết nối kiến thức lý thuyết với quy trình triển khai thực tế và hiểu rõ hơn vai trò của từng thành phần trong kiến trúc Cloud.

## Trải nghiệm trong Event

### Học hỏi từ các diễn giả có chuyên môn cao

Sự kiện giúp em có cơ hội tiếp cận những kinh nghiệm thực tế từ các diễn giả đang làm việc trong các lĩnh vực Cloud, DevOps, Full-Stack và AWS. Các ví dụ thực tế giúp em hiểu rõ hơn cách kiến thức Cloud được áp dụng trong môi trường doanh nghiệp.

### Trải nghiệm kỹ thuật thực tế

Việc tham gia chung kết Event Cloud Architect giúp em có cơ hội vận dụng kiến thức đã học để giải quyết một bài toán kiến trúc cụ thể. Qua đó, em hiểu rằng việc xây dựng kiến trúc đòi hỏi sự phối hợp giữa nhiều yếu tố kỹ thuật thay vì chỉ tập trung vào một dịch vụ riêng lẻ.

### Ứng dụng công cụ hiện đại

Nội dung về AWS Security Agent và các công cụ hỗ trợ AI giúp em có thêm góc nhìn về xu hướng sử dụng AI trong quá trình phát triển và bảo mật phần mềm.

Em nhận thấy việc sử dụng công cụ hiện đại cần đi cùng với kiến thức nền tảng của người phát triển. Công cụ có thể hỗ trợ phân tích và tăng năng suất, nhưng người sử dụng vẫn cần hiểu rõ vấn đề để đánh giá kết quả và đưa ra quyết định phù hợp.

### Kết nối và trao đổi

Event cũng tạo điều kiện để em trao đổi với các thành viên khác có cùng định hướng về Cloud và công nghệ. Qua quá trình trao đổi, em có thêm góc nhìn về cách học tập, triển khai hệ thống và phát triển kỹ năng trong lĩnh vực Cloud Computing.

### Bài học rút ra

Sau khi tham gia sự kiện, em rút ra một số bài học quan trọng:

1. Thiết kế kiến trúc Cloud cần xuất phát từ yêu cầu nghiệp vụ và yêu cầu kỹ thuật.
2. Một hệ thống tốt cần cân bằng giữa bảo mật, khả năng sẵn sàng, hiệu năng, khả năng mở rộng và chi phí.
3. Monitoring và logging là thành phần cần được thiết kế ngay từ đầu.
4. Bảo mật cần được tích hợp xuyên suốt vòng đời phát triển phần mềm.
5. Tự động hóa CI/CD giúp giảm các thao tác thủ công và tăng tính nhất quán trong quá trình triển khai.
6. Các công cụ AI đang trở thành một phần quan trọng trong quá trình phát triển và bảo mật phần mềm.
7. Kiến thức về từng dịch vụ AWS cần được kết hợp thành một kiến trúc hoàn chỉnh để giải quyết bài toán thực tế.

## Một số hình ảnh khi tham gia sự kiện

* ![Hình ảnh tham gia Event Cloud Architect](images/image.png)
* ![Hình ảnh tham gia Event Cloud Architect](images/image-1.png)

[Bài đăng về sự kiện trên LinkedIn](https://www.linkedin.com/posts/huynhson081103_it-was-an-honor-to-stand-on-the-fcaj-stage-ugcPost-7481615527300202496-F5eo/?utm_medium=member_desktop&rcm=ACoAAFd44wMBcNLkJz447g4e80PkvcnRgv0AXXE&utm_source=chatgpt.com)
