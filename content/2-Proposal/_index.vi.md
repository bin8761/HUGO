---
title: "Đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

Trong phần này, bạn cần tóm tắt nội dung hội thảo mà bạn **dự định** tiến hành.

# Đề xuất Enterprise Asset Management
## Nền tảng AWS thống nhất cho theo dõi tài sản, phân công, bảo trì và báo cáo

### 1. Tóm tắt điều hành
Đề xuất Enterprise Asset Management mô tả một hệ thống nội bộ dành cho người quản trị và nhân viên để quản lý tài sản trong một luồng tập trung duy nhất. Nền tảng bao phủ các nghiệp vụ theo dõi tài sản, phân công, thu hồi, chuyển giao, bảo trì, báo cáo, tải tệp đính kèm, gửi email OTP và lưu lịch sử có kiểm toán ở một nơi.

Giải pháp sử dụng React + Vite trên AWS Amplify Hosting cho frontend, Node.js + Express trên AWS Elastic Beanstalk phía sau Application Load Balancer cho backend, và Amazon RDS for MySQL thông qua Prisma cho dữ liệu bền vững. Các dịch vụ hỗ trợ gồm Amazon S3 private bucket cho tệp, Amazon SES cho OTP và thông báo, AWS Secrets Manager và Systems Manager Parameter Store cho cấu hình, cùng CloudWatch, CloudTrail và Session Manager cho vận hành và audit.

### 2. Tuyên bố vấn đề
### Vấn đề là gì?
Hoạt động quản lý tài sản hiện đang bị phân tán giữa quy trình thủ công, tệp rời rạc và nhiều kênh trao đổi khác nhau. Luồng công việc của quản trị viên và nhân viên cần phân quyền rõ ràng, nhưng khi không có một hệ thống tập trung thì rất khó biết tài sản đang thuộc về ai, đã bàn giao cho ai, đã thu hồi hay chưa, và hạng mục bảo trì nào vẫn còn treo.

### Giải pháp
Nền tảng tập trung toàn bộ hồ sơ tài sản, phân công, thu hồi, chuyển giao, bảo trì, phản hồi, thông báo và tệp đính kèm trong một hệ thống nội bộ duy nhất. Các màn hình theo vai trò cho phép quản trị viên xử lý toàn bộ vòng đời tài sản, trong khi nhân viên chỉ cần thực hiện các tác vụ tự phục vụ như xem tài sản được giao, gửi yêu cầu và theo dõi trạng thái. Nhờ đó hệ thống loại bỏ trùng lặp dữ liệu và đảm bảo toàn bộ quy trình có thể kiểm toán từ đầu đến cuối.

### Lợi ích và lợi tức đầu tư
Kết quả là quy trình xử lý tài sản nhanh hơn, ít sai sót khi bàn giao hơn và có một nguồn dữ liệu duy nhất cho lịch sử vận hành. Hồ sơ tập trung giúp cải thiện chất lượng báo cáo, dễ truy xuất tệp đính kèm và vết kiểm toán hơn, đồng thời giảm thời gian đối soát các bảng tính hoặc tin nhắn rời rạc. Nhóm nội bộ cũng có một nền tảng MVP ổn định hơn để mở rộng về sau mà không phải thay đổi luồng nghiệp vụ cốt lõi.

### 3. Kiến trúc giải pháp
Giải pháp dùng kiến trúc AWS phân lớp cho nghiệp vụ quản lý tài sản nội bộ. React + Vite được host trên AWS Amplify Hosting, điểm vào công khai của API là Application Load Balancer, và backend chạy trên AWS Elastic Beanstalk với Node.js + Express. Dữ liệu nghiệp vụ bền vững được lưu trong Amazon RDS for MySQL và được truy cập thông qua Prisma. Kiến trúc được trình bày chi tiết dưới đây:

![Tổng quan kiến trúc Enterprise Asset Management](/images/2-Proposal/enterprise-asset-management-architecture-overview.svg)

![Luồng yêu cầu Enterprise Asset Management](/images/2-Proposal/enterprise-asset-management-request-flow.svg)

### Dịch vụ AWS đã sử dụng
- **AWS Amplify Hosting**: Host frontend React + Vite.
- **Application Load Balancer**: Nhận traffic API và chuyển tiếp vào backend.
- **AWS Elastic Beanstalk**: Chạy ứng dụng Node.js + Express.
- **Amazon RDS for MySQL Single-AZ**: Lưu tài sản, phân công, lịch sử bảo trì và báo cáo.
- **Amazon S3 private bucket**: Lưu tệp đính kèm, file tải lên và tài liệu xuất ra.
- **Amazon SES**: Gửi email OTP và thông báo nội bộ.
- **AWS Secrets Manager**: Lưu secret nhạy cảm như thông tin kết nối CSDL và mail.
- **AWS Systems Manager Parameter Store**: Lưu cấu hình theo môi trường.
- **Amazon CloudWatch**: Thu thập log và cảnh báo về tình trạng hệ thống.
- **AWS CloudTrail**: Ghi nhận hoạt động audit ở mức AWS.
- **AWS Systems Manager Session Manager**: Hỗ trợ quản trị an toàn mà không cần SSH công khai.

### Thiết kế thành phần
- **Frontend**: React + Vite cung cấp màn hình cho quản trị viên và nhân viên.
- **Điểm vào API**: Application Load Balancer chuyển request vào tầng backend.
- **Tầng ứng dụng**: Node.js + Express xử lý xác thực, phân quyền và business rules.
- **Lưu trữ dữ liệu**: Amazon RDS for MySQL lưu mô hình dữ liệu chính qua Prisma.
- **Xử lý tệp**: Amazon S3 private bucket lưu tệp đính kèm, bằng chứng và file xuất ra.
- **Thông báo**: Amazon SES gửi email OTP và email thông báo từ các tác vụ backend.
- **Secret và cấu hình**: Secrets Manager và Parameter Store giữ giá trị runtime ngoài source code.
- **Giám sát và vận hành**: CloudWatch, CloudTrail và Session Manager hỗ trợ giám sát, audit và vận hành.

### 4. Triển khai kỹ thuật
**Các giai đoạn thực hiện**
Dự án này đi qua bốn giai đoạn triển khai thực tế, phù hợp với luồng nghiệp vụ quản lý tài sản:
- Nền tảng frontend và phân vai người dùng: thiết lập màn hình React + Vite cho quản trị viên và nhân viên, cấu trúc route, layout dùng chung và hành vi giao diện có nhận biết quyền.
- Nền tảng backend, xác thực và lược đồ CSDL: triển khai API Node.js + Express, JWT authentication, phân quyền theo vai trò, mô hình Prisma và thiết lập schema MySQL.
- Luồng nghiệp vụ vòng đời tài sản: xây dựng end-to-end các luồng tài sản, phân công, thu hồi, chuyển giao, bảo trì, kiểm kê, báo cáo, tệp đính kèm và thông báo.
- Triển khai, QA, tài liệu và hoàn thiện demo: xác thực bản deploy AWS, ổn định xử lý lỗi, chuẩn bị seed data, viết tài liệu và làm mượt luồng demo.

**Yêu cầu kỹ thuật**
- Stack frontend: React + Vite với các màn hình nhận biết vai trò admin và employee.
- Stack backend: Node.js + Express với JWT, bcrypt, Prisma và MySQL.
- Stack kiểm thử: Playwright cho kiểm tra end-to-end và Jest cho backend hoặc service-level test khi phù hợp.
- Stack triển khai: AWS Amplify Hosting, AWS Elastic Beanstalk, Amazon RDS for MySQL, Amazon S3 private bucket, Amazon SES, AWS Secrets Manager, AWS Systems Manager Parameter Store, Amazon CloudWatch, AWS CloudTrail và AWS Systems Manager Session Manager.
- Yêu cầu vận hành: giữ schema đồng bộ giữa local development và production, bảo toàn phân quyền theo vai trò và giữ luồng demo đủ ổn định cho buổi trình bày.

### 5. Dòng thời gian & các cột mốc quan trọng
**Dòng thời gian của dự án**
Timeline được sắp theo thứ tự phụ thuộc trong 5 tuần để team xây nền tảng trước, sau đó mới ghép các luồng nghiệp vụ vòng đời tài sản lên trên.

- Tuần 1: Nền tảng và hợp đồng
  - Xây dựng nền tảng backend, schema cốt lõi, hợp đồng API, khung frontend và kế hoạch QA.
  - Cột mốc: schema, API contract, app skeleton, login flow.
- Tuần 2: Tính năng quản lý lõi
  - Hoàn thiện JWT login, CRUD cốt lõi, nối các màn hình admin CRUD và chuẩn bị khung profile cho nhân viên.
  - Cột mốc: core CRUD complete.
- Tuần 3: Tính năng vòng đời tài sản
  - Triển khai API và màn hình phân công, chi tiết tài sản cho nhân viên và luồng báo cáo tài sản hỏng.
  - Cột mốc: assignment, employee views, broken asset report complete.
- Tuần 4: Bảo trì, kiểm kê, báo cáo và thử nghiệm AWS
  - Triển khai API bảo trì, kiểm kê và báo cáo, xây các màn hình admin còn lại và chạy thử bản deploy AWS đầu tiên.
  - Cột mốc: maintenance, inventory, reports, first AWS deployment complete.
- Tuần 5: Triển khai cuối, QA và thuyết trình
  - Hoàn tất triển khai, kiểm tra ổn định dữ liệu và auth, chuẩn bị seed data, checklist QA, ảnh chụp màn hình và kịch bản demo.
  - Cột mốc: final deployment, demo data, QA, presentation complete.

### 6. Dự toán ngân sách
Ngân sách được tính theo kiến trúc AWS hiện tại và cần được tính lại bằng AWS Pricing Calculator khi chốt xong kích cỡ instance cuối cùng.

### Chi phí cơ sở hạ tầng ước tính
- Application Load Balancer + Elastic Beanstalk compute: UNCONFIRMED, khoảng 28-40 USD/tháng cho stack demo hiện tại.
- Amazon RDS for MySQL Single-AZ: UNCONFIRMED, khoảng 12-19 USD/tháng gồm lưu trữ và backup ở mức vừa phải.
- Amazon S3 private bucket: UNCONFIRMED, thường là chi phí hàng tháng rất thấp cho tệp đính kèm và file xuất ra.
- Amazon SES: UNCONFIRMED, thường là chi phí hàng tháng rất thấp cho OTP và email nội bộ.
- Amazon CloudWatch: UNCONFIRMED, thường là chi phí hàng tháng rất thấp cho log và alarm.
- AWS Secrets Manager, Systems Manager Parameter Store, CloudTrail và Session Manager: UNCONFIRMED hoặc gần như bằng 0 ở mức dùng cơ bản.

### Tổng ước tính
- Chi phí vận hành hàng tháng ước tính: UNCONFIRMED, khoảng 46-60 USD/tháng cho kiến trúc hiện tại.
- Chi phí vận hành hàng năm ước tính: UNCONFIRMED, khoảng 552-720 USD/năm.
- Chi phí phần cứng một lần: không cần mua phần cứng riêng ngoài thiết bị phát triển sẵn có.

### 7. Đánh giá rủi ro
#### Ma trận rủi ro
- Rủi ro chỉ chạy được một instance: Tác động trung bình, xác suất trung bình.
- Rủi ro độ bền của file tải lên: Tác động cao, xác suất trung bình.
- Rủi ro rò rỉ auth hoặc phân quyền: Tác động cao, xác suất thấp.
- Rủi ro backup và restore cơ sở dữ liệu: Tác động cao, xác suất thấp.
- Rủi ro trạng thái SSE hoặc thông báo realtime: Tác động trung bình, xác suất trung bình.
- Rủi ro vượt ngân sách: Tác động trung bình, xác suất trung bình.
- Rủi ro deploy hoặc rollback: Tác động trung bình, xác suất trung bình.
- Rủi ro toàn vẹn lịch sử và audit: Tác động cao, xác suất thấp.

#### Chiến lược giảm thiểu
- Chỉ chạy một instance ở giai đoạn đầu và ghi rõ giả định này, sau đó mới nâng cấp khi luồng nghiệp vụ đã ổn định.
- Lưu tệp đính kèm vào S3 private bucket và kiểm tra validation ở backend trước khi ghi.
- Bắt buộc JWT, kiểm tra vai trò và authorization server-side cho mọi route được bảo vệ.
- Giữ backup CSDL và ghi rõ quy trình restore trước khi đưa vào production.
- Xem trạng thái notification in-memory của SSE như một giới hạn baseline và chỉ mở rộng sau khi đánh giá phương án multi-instance.
- Kiểm soát chi phí bằng cảnh báo ngân sách, kích cỡ instance nhỏ và rà soát chi phí hàng tháng.
- Giữ ghi chú deploy, version release và đường rollback sẵn sàng trước ngày demo.
- Giữ lịch sử vận hành trong MySQL và ghi audit AWS qua CloudTrail và CloudWatch.

#### Kế hoạch dự phòng
- Chuyển sang quy trình thủ công tạm thời nếu bản deploy AWS không sẵn sàng cho giai đoạn chuẩn bị demo.
- Khôi phục từ bản backup CSDL nếu dữ liệu bị hỏng hoặc deploy lỗi ảnh hưởng đến bộ dữ liệu chính.
- Roll back về version trước nếu release mới gây bug chặn luồng chính.
- Xem lại thiết kế notification nếu mở rộng multi-instance làm hỏng giả định SSE in-memory.

### 8. Kết quả mong đợi
#### Cải tiến kỹ thuật:
Tầm nhìn tài sản được tập trung thay cho các bảng tính rời rạc và việc nhắc việc thủ công.
Luồng phân công, thu hồi và chuyển giao nhanh hơn giúp giảm độ trễ khi bàn giao.
Xử lý bảo trì tốt hơn giúp trạng thái yêu cầu, chi phí sửa chữa và lịch sử nằm chung một nơi.
Các màn hình tự phục vụ cho nhân viên cho phép theo dõi tài sản và yêu cầu mà không phải hỏi quản trị viên cho từng cập nhật.
Báo cáo và khả năng kiểm toán tốt hơn giúp việc xem tổng hợp, tệp đính kèm và lịch sử dễ dàng hơn.
#### Giá trị lâu dài
Nền tảng MVP nội bộ ổn định hỗ trợ mở rộng trong tương lai mà không phải đổi luồng nghiệp vụ cốt lõi.
Dữ liệu tài sản, bảo trì và kiểm kê có thể tái sử dụng cho các báo cáo và cải tiến quy trình sau này.
Nhóm có thể tiếp tục dùng dự án như một hệ thống nội bộ sẵn sàng demo cho các vòng lặp tiếp theo.

### 9. Kết luận tổng quan
Giải pháp Enterprise Asset Management được đề xuất là một MVP nội bộ thực tế, bám đúng phạm vi team và đúng stack AWS đang dùng.
React + Vite trên Amplify, Node.js + Express trên Elastic Beanstalk và MySQL qua Prisma tạo ra lộ trình rõ ràng từ local development đến một bản demo có thể triển khai.
Các dịch vụ AWS hỗ trợ đủ cho theo dõi tài sản, bảo trì, báo cáo, xử lý tệp, thông báo, audit và vận hành an toàn mà không làm hệ thống phức tạp quá mức.
