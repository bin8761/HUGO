---
title: "Tự đánh giá"
date: 2026-07-05
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

Trong thời gian thực tập từ 17/04/2026 đến 10/07/2026 tại Amazon Web Services Vietnam Company Limited trong chương trình Workforce Bootcamp - First Cloud AI Journey, em đã xây dựng được cái nhìn cụ thể hơn về công việc cloud thông qua tự học, tham gia sự kiện, đọc tài liệu kỹ thuật, thực hành triển khai và viết báo cáo.

Dự án chính được dùng trong báo cáo là EAM Workspace - Enterprise Asset Management System. Phần đóng góp trực tiếp của em tập trung vào frontend, nhưng giá trị rộng hơn của kỳ thực tập đến từ việc em học được cách một hệ thống web hoàn chỉnh được ghép nối, triển khai, theo dõi và mô tả trong môi trường AWS.

---

## 1. Kết quả đạt được

### 1.1. Xây dựng nền tảng AWS thực tế
Ngay từ đầu kỳ thực tập, em tập trung vào các khái niệm xuất hiện lặp đi lặp lại trong các dự án cloud: Cloud Computing, AWS Global Infrastructure, AWS Management Console, AWS Free Tier, AWS Budgets và thói quen theo dõi chi phí sớm thay vì để đến cuối mới xử lý.

Từ đó, em đi qua các nhóm dịch vụ cốt lõi theo cách có hệ thống hơn:
* **Định danh và truy cập:** Role-based access control (RBAC), IAM Policy Simulator, cross-account roles và Cognito user pools.
* **Mạng:** Transit Gateway, VPC peering, flow logs, Bastion hosts, Application Load Balancers và định tuyến DNS bằng Route 53.
* **Compute:** Auto Scaling Groups, Launch Templates, Spot Instances, AWS Lambda cho tác vụ serverless và các lớp container.
* **Tầng dữ liệu:** Amazon RDS Read Replicas, Multi-AZ deployment để tăng khả năng sẵn sàng, connection pooling và chính sách snapshot tự động.
* **Lưu trữ:** S3 Lifecycle Policies, Glacier deep archive, cross-region replication, tích hợp CloudFront CDN và signed URLs.
* **Triển khai:** AWS CodePipeline, CodeBuild, CodeDeploy cho CI/CD tự động và các mô hình cấp phát hạ tầng.
* **Vận hành và bảo vệ:** Mối đe dọa từ GuardDuty, tuân thủ với AWS Config, lỗ hổng từ Inspector, Systems Manager và cơ chế cảnh báo chủ động.

Nhờ vậy, em nhìn AWS như một nền tảng tích hợp thay vì chỉ là một tập hợp công cụ rời rạc.

### 1.2. Hiểu dự án thông qua kiến trúc cloud
Phần có giá trị nhất của kỳ thực tập là em được thấy cách dịch vụ AWS ánh xạ vào một kiến trúc ứng dụng thật thay vì chỉ học chúng riêng lẻ.

Trong EAM Workspace, em quan sát vai trò của từng dịch vụ trong luồng tổng thể:
* **Amazon CloudFront** tăng tốc phân phối tài nguyên và phục vụ frontend tĩnh trên phạm vi toàn cầu.
* **AWS WAF** kiểm tra lưu lượng đầu vào ở lớp edge để chặn các tấn công SQL injection.
* **Application Load Balancer** phân phối request của người dùng qua nhiều Availability Zone.
* **Amazon ElastiCache (Redis)** giảm tải cho database bằng cách lưu cache các truy vấn tài sản thường gặp.
* **AWS Secrets Manager** tự động xoay vòng thông tin đăng nhập database mà không cần triển khai lại code.
* **Amazon SNS** xử lý việc fan-out thông báo cho các cảnh báo tài sản doanh nghiệp quan trọng.

Dự án này giúp em thấy rõ hơn mối phụ thuộc giữa các tầng. Một deployment không thể coi là hoàn tất chỉ vì code chạy được trên máy local; thực tế còn phải tính đến routing, environment variables, permissions, truy cập database, cấu hình build và tình trạng của dịch vụ.

### 1.3. Kỷ luật triển khai và thói quen gỡ lỗi
Làm việc với các lỗi triển khai giúp em hình thành quy trình xử lý vấn đề có kỷ luật hơn. Em học cách chia một lỗi thành các kiểm tra nhỏ thay vì coi nó là một vấn đề mơ hồ.

Một số bài học vận hành em rút ra là:
* Phân tích custom error response của CloudFront trước khi thay đổi cấu hình phân phối tài nguyên.
* Debug rule ingress của security group khi container instance không thể truy cập lớp cache.
* Giải mã lỗi IAM permission denied bằng AWS CLI để tìm ra action còn thiếu.
* Kiểm tra cấu hình timeout kết nối database trong target group settings.
* Xác định xem một đợt tăng độ trễ đến từ serialization của mạng hay từ truy vấn database chưa có index.
* Viết các bước triển khai theo cách người khác có thể lặp lại sau này.

Quy trình đó rèn cho em thói quen kiểm tra cấu hình trước, code sau và luôn xem triệu chứng trong đúng ngữ cảnh của nó.

### 1.4. Đọc nội dung AWS và rút ra phần hữu ích
Một phần đáng giá khác của kỳ thực tập là đọc AWS Blog và chuyển chúng thành các ghi chú ngắn, hữu ích. Em đã tìm hiểu các chủ đề như EKS, Istio Ambient Mesh, EKS Control Plane Egress và AWS Continuum.

Việc này giúp em cải thiện cùng lúc hai kỹ năng. Thứ nhất, em hiểu hơn cách AWS giải thích kiến trúc và các đánh đổi trong vận hành. Thứ hai, em luyện cách cô đọng một bài viết kỹ thuật thành những ý thực sự quan trọng cho việc học và triển khai.

Các sự kiện em tham gia cũng mở rộng góc nhìn của em. Nội dung bao gồm security, AI, containers, automation, tuyển dụng và cách các nền tảng cloud được dùng trong quy trình doanh nghiệp.

### 1.5. Biến công việc thành tài liệu rõ ràng
Viết workshop là một kỹ năng khác với xây dựng hệ thống, và em đã cải thiện bằng cách nhìn nó như một phần công việc riêng. Workshop yêu cầu em mô tả quy trình kỹ thuật theo trình tự để người khác có thể làm theo mà không phải đoán.

Trong lúc chuẩn bị hướng dẫn triển khai, em phải suy nghĩ về:
* Mục đích của từng bước.
* Dịch vụ AWS nào đang được cấu hình.
* Cần những input hoặc thiết lập nào.
* Cần chụp lại bằng chứng gì.
* Kết quả mong đợi sau từng bước là gì.
* Cách xác nhận bước đó đã thành công.

Điều này cho em thấy tài liệu tốt không phải là bản chép lại thao tác. Nó là phần giải thích có định hướng về mục tiêu, cách thiết lập, cách kiểm tra và kết quả cần đạt.

---

## 2. Bảng tự đánh giá

| STT | Tiêu chí | Mô tả | Mức tự đánh giá |
| :--- | :--- | :--- | :--- |
| 1 | Nền tảng AWS | Hiểu các ý chính đằng sau IAM, VPC, EC2, RDS, S3, CloudWatch và nhận thức về chi phí AWS | Khá |
| 2 | Triển khai AWS | Có thể hỗ trợ một bản demo deployment gồm frontend, backend, API Gateway, RDS và SES | Khá |
| 3 | Hiểu kiến trúc cloud | Hiểu luồng traffic từ Amplify đến API Gateway, Elastic Beanstalk và RDS | Khá |
| 4 | Gỡ lỗi triển khai | Có thể kiểm tra endpoint, environment variables, health check, rewrite rules và kết nối database | Khá |
| 5 | Đọc tài liệu AWS | Có thể đọc AWS Blog và tài liệu kỹ thuật rồi diễn đạt lại ý rõ ràng hơn | Tốt |
| 6 | Viết workshop | Có thể giải thích các bước triển khai, thêm ảnh chụp và ghi lại kết quả kiểm tra | Tốt |
| 7 | Tự học cloud | Chủ động tìm hiểu các dịch vụ AWS dựa trên yêu cầu của dự án | Tốt |
| 8 | Làm việc nhóm | Phối hợp với nhóm để hiểu frontend, backend, database và chi tiết triển khai | Khá |
| 9 | Quản lý tiến độ | Giữ worklog, proposal, blog, event, workshop và self-assessment theo từng giai đoạn | Khá |
| 10 | Tổng thể | Hoàn thành báo cáo cá nhân gắn với cả dự án và quá trình học AWS | Tốt |

---

## 3. Điểm mạnh

* Em duy trì việc tự học và không chờ mọi việc được giải thích sẵn mới bắt đầu nghiên cứu AWS.
* Em có thể kết nối khái niệm cloud với luồng triển khai thực tế mà EAM Workspace đang dùng.
* Em cải thiện khả năng đọc tài liệu kỹ thuật và viết lại thành ngôn ngữ báo cáo rõ ràng hơn.
* Em hiểu tốt hơn cách frontend, API, backend và database tương tác trong một deployment AWS.
* Em nâng cao khả năng ghi lại các bước, thu thập bằng chứng và giải thích kết quả kiểm tra.

---

## 4. Điểm cần cải thiện

* Em vẫn cần thực hành nhiều hơn với AWS CLI và Infrastructure as Code để giảm phụ thuộc vào thao tác thủ công trên console.
* Em cần rèn thêm khả năng đọc log và lần theo lỗi backend qua CloudWatch.
* Em muốn hiểu sâu hơn về network isolation, private subnets, hành vi của NAT Gateway, VPC Endpoints và các mô hình kết nối an toàn.
* Em nên dành thêm thời gian cho IAM design, quản lý secrets và tách môi trường development, staging, production.
* Em cần suy nghĩ có hệ thống hơn về kiểm soát chi phí khi thiết kế deployment trên cloud.

---

## 5. Bài học rút ra

Kỳ thực tập này đã thay đổi cách em nhìn về công việc cloud. Em không còn xem AWS chỉ là nơi để deploy một ứng dụng, mà là tập hợp những quyết định về cấu trúc, quyền truy cập, giám sát, luồng dữ liệu và độ tin cậy khi vận hành.

Em cũng học được rằng lý thuyết sẽ dễ nhớ hơn nhiều khi nó gắn với một dự án đang chạy thật. Các dịch vụ như Amplify, API Gateway, Elastic Beanstalk, RDS và SES sẽ dễ hiểu hơn khi chúng được dùng chung trong một hệ thống thay vì học từng phần rời rạc.

Quá trình viết workshop đặc biệt hữu ích vì nó buộc em chuyển trải nghiệm thành kiến thức có thể tái sử dụng. Trong engineering cloud, các bước rõ ràng và bằng chứng rõ ràng quan trọng không kém kết quả cuối cùng.

---

## 6. Định hướng sau thực tập

Sau kỳ thực tập, em muốn tiếp tục phát triển theo các hướng AWS thực hành hơn:
* Học AWS CDK hoặc Terraform và dùng chúng cho công việc hạ tầng có thể lặp lại.
* Học sâu hơn về thiết kế VPC, mạng private, load balancing, Security Groups và IAM.
* Bổ sung monitoring mạnh hơn với CloudWatch Logs, metrics và alarms.
* Thực hành các mẫu upload S3, CloudFront, custom domains và cấu hình HTTPS.
* Cải thiện kỹ năng backup/restore database và áp dụng tối ưu chi phí AWS một cách chủ động hơn.
* Tiếp tục hoàn thiện EAM Workspace để nó tiến gần hơn đến một ứng dụng sẵn sàng cho production.

Nhìn chung, kỳ thực tập đã cho em một góc nhìn thực tế hơn về cloud computing. Em không chỉ học cách sử dụng các dịch vụ AWS, mà còn học cách kết hợp chúng thành một hệ thống có thể triển khai và được ghi chép để người khác có thể theo dõi.
