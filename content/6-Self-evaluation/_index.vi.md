---
title: "Tự đánh giá"
date: 2026-07-05
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

Trong khoảng thời gian thực tập từ **17/04/2026 đến 10/07/2026** tại **Amazon Web Services Vietnam Company Limited** trong chương trình **Workforce Bootcamp - First Cloud AI Journey**, tôi có cơ hội làm việc với AWS theo cách thực tế hơn rất nhiều so với việc chỉ học trên tài liệu. Những gì tôi trải qua trong kỳ thực tập không chỉ là tự học, tham gia sự kiện, đọc AWS Blog, triển khai project hay viết workshop, mà còn là quá trình nhìn rõ hơn cách một hệ thống backend được đưa từ môi trường local lên cloud và được vận hành như một hệ thống hoàn chỉnh.

Báo cáo này dựa trên project **EAM Workspace - Enterprise Asset Management System**. Trong project, tôi tham gia phần frontend, nhưng điều khiến tôi học được nhiều nhất lại nằm ở phần backend phía sau: cách API được tổ chức, cách backend kết nối với database, cách các dịch vụ AWS hỗ trợ cho luồng deploy, và cách theo dõi hệ thống khi nó đã chạy trên cloud. Chính góc nhìn đó giúp tôi hiểu backend không chỉ là viết API, mà còn là biết thiết kế, triển khai và kiểm tra toàn bộ luồng hoạt động của hệ thống.

## 1. Kết quả đạt được

### 1.1. Nền tảng về AWS

Ở giai đoạn đầu, tôi bắt đầu từ những khái niệm cơ bản như **Cloud Computing**, **AWS Global Infrastructure**, **AWS Management Console**, **AWS Free Tier** và cách kiểm soát chi phí với **AWS Budgets**. Đây là phần nền giúp tôi hiểu rằng AWS không chỉ là nơi tạo ra tài nguyên, mà là một nền tảng để vận hành hệ thống theo cách có tổ chức hơn.

Sau đó, tôi tiếp tục tìm hiểu các nhóm dịch vụ quan trọng đối với một hệ thống backend:

- **IAM** để hiểu user, role, policy và nguyên tắc phân quyền tối thiểu.
- **Networking** để nắm VPC, subnet, route table, Internet Gateway, NAT Gateway, Security Group và Network ACL.
- **Compute** để làm quen với EC2, AMI, instance type và cách dịch vụ compute hỗ trợ backend.
- **Database** để hiểu Amazon RDS for MySQL, endpoint, backup và kết nối từ backend.
- **Storage** để tìm hiểu Amazon S3, object storage và cách dùng cho file, ảnh, tài liệu.
- **Deployment** để biết Elastic Beanstalk và API Gateway tham gia vào luồng triển khai như thế nào.
- **Monitoring và Security** để làm quen với CloudWatch, CloudTrail, WAF, KMS và Secrets Manager.

Từ quá trình này, tôi hiểu rõ hơn rằng AWS không chỉ giúp ứng dụng chạy được, mà còn giúp hệ thống có thể được giám sát, bảo mật và mở rộng theo cách phù hợp hơn với môi trường thực tế.

### 1.2. Học qua luồng backend của EAM Workspace

Điểm tôi học được nhiều nhất là khi đặt kiến thức AWS vào chính project **EAM Workspace**. Thay vì nhìn từng dịch vụ như những phần rời rạc, tôi bắt đầu thấy rõ vai trò của chúng trong luồng backend:

- **Amazon API Gateway** nhận và chuyển tiếp các request `/api/*`.
- **AWS Elastic Beanstalk** chạy backend Node.js/Express.
- **Amazon RDS for MySQL** lưu dữ liệu của hệ thống.
- **Amazon SES** hỗ trợ gửi email và OTP thông qua SMTP credentials.
- **CloudWatch** dùng để theo dõi log, kiểm tra trạng thái và hỗ trợ xử lý sự cố.

Điều này giúp tôi hiểu rõ sự khác nhau giữa backend chạy local và backend đã triển khai lên AWS. Khi hệ thống bắt đầu chạy trên cloud, không chỉ code quan trọng mà còn có rất nhiều yếu tố đi kèm như biến môi trường, routing, quyền truy cập, kết nối database, cấu hình mạng, trạng thái health và cách quan sát log.

### 1.3. Kỹ năng triển khai và xử lý lỗi

Phần đem lại cho tôi nhiều kinh nghiệm thực tế nhất là triển khai và kiểm tra lỗi. Tôi phải xem lại environment variables của Elastic Beanstalk, kiểm tra thông tin SMTP của Amazon SES, xác minh API Gateway có thể kết nối đúng tới backend hay không, và điều chỉnh cấu hình triển khai khi cần.

Qua những tình huống đó, tôi rút ra một thói quen rất quan trọng: khi hệ thống không hoạt động, không nên chỉ nhìn vào code. Lỗi có thể đến từ API, backend, database, IAM, network hoặc chính cấu hình AWS. Vì vậy, tôi tập cho mình cách kiểm tra theo từng lớp, từ request đầu vào, log, endpoint, credential cho đến trạng thái deploy.

### 1.4. Đọc tài liệu và tổng hợp kiến thức

Trong kỳ thực tập, tôi đọc và tổng hợp một số AWS Blog liên quan đến EKS, Istio Ambient Mesh, EKS Control Plane Egress và AWS Continuum. Việc đọc các bài viết này giúp tôi quen hơn với cách AWS trình bày giải pháp, mô tả kiến trúc và phân tích vấn đề vận hành trong thực tế.

Ngoài ra, các sự kiện tôi tham gia cũng mở rộng góc nhìn của tôi về cloud, security, container, AI, tuyển dụng và cách doanh nghiệp ứng dụng AWS trong vận hành.

Từ đó, tôi nhận ra rằng học AWS không chỉ là thao tác trên console. Quan trọng hơn là phải biết đọc tài liệu, nhận ra ý chính, hiểu use case và liên hệ ngược lại với bài toán thực tế của project.

### 1.5. Viết workshop và tài liệu

Một điểm tôi cải thiện khá rõ là khả năng viết lại quy trình kỹ thuật thành tài liệu có thể theo dõi. Khi viết workshop triển khai EAM Workspace lên AWS, tôi phải sắp xếp nội dung sao cho người đọc dễ theo dõi từng bước:

- Mục tiêu của bước triển khai.
- Dịch vụ AWS được sử dụng.
- Cấu hình cần chuẩn bị.
- Hình ảnh minh họa cần chụp.
- Kết quả mong đợi sau mỗi bước.
- Cách kiểm tra khi gặp lỗi.

Quá trình này giúp tôi hiểu rằng tài liệu kỹ thuật tốt không chỉ ghi lại việc đã làm, mà còn phải giúp người khác hiểu được vì sao làm như vậy, kiểm tra ở đâu và kết quả đúng sẽ trông như thế nào.

## 2. Bảng tự đánh giá

| STT | Tiêu chí | Mô tả | Mức tự đánh giá |
| --- | --- | --- | --- |
| 1 | Kiến thức AWS nền tảng | Hiểu các khái niệm cơ bản về IAM, VPC, EC2, RDS, S3, CloudWatch và kiểm soát chi phí AWS | Khá |
| 2 | Triển khai backend | Có thể hỗ trợ triển khai và kiểm tra luồng backend với API Gateway, Elastic Beanstalk, RDS và SES | Khá |
| 3 | Hiểu kiến trúc backend | Hiểu luồng request từ client đến API Gateway, backend service và database | Khá |
| 4 | Xử lý lỗi triển khai | Biết kiểm tra endpoint, biến môi trường, log, health check và kết nối database | Khá |
| 5 | Đọc tài liệu AWS | Có thể đọc AWS Blog/tài liệu kỹ thuật và viết lại nội dung theo hướng dễ hiểu hơn | Tốt |
| 6 | Viết workshop | Biết mô tả bước triển khai, thêm ảnh minh họa và ghi chú kết quả kiểm tra | Tốt |
| 7 | Tự học cloud | Chủ động tìm hiểu thêm dịch vụ AWS theo nhu cầu của project | Tốt |
| 8 | Làm việc nhóm | Phối hợp với nhóm để hiểu nội dung backend, database và triển khai | Khá |
| 9 | Quản lý tiến độ | Duy trì worklog, proposal, blog, event, workshop và self-assessment theo từng giai đoạn | Khá |
| 10 | Tổng thể | Hoàn thành báo cáo cá nhân gắn với project và quá trình học AWS | Tốt |

## 3. Điểm mạnh

Điểm mạnh lớn nhất của tôi trong kỳ thực tập là tinh thần chủ động. Khi gặp một dịch vụ hoặc một khái niệm mới, tôi thường tìm hiểu sớm để hiểu nó đang nằm ở đâu trong bức tranh tổng thể của project. Cách học này giúp tôi tiếp cận AWS có hệ thống hơn, thay vì chỉ biết từng phần riêng lẻ.

Tôi cũng dần hình thành thói quen nhìn hệ thống theo hướng backend. Thay vì chỉ nhìn vào giao diện hay từng màn hình, tôi bắt đầu theo dõi request đi như thế nào, API xử lý ra sao, backend lấy dữ liệu từ đâu và hệ thống được triển khai như thế nào trên cloud. Điều đó giúp tôi hiểu project sâu hơn rất nhiều.

Một điểm nữa là khả năng đọc tài liệu kỹ thuật và viết lại thành nội dung rõ ràng hơn. Kỹ năng này rất hữu ích khi viết workshop, mô tả ảnh minh họa và trình bày kết quả kiểm tra.

## 4. Điểm cần cải thiện

Bên cạnh những gì đã làm được, tôi vẫn còn nhiều điểm cần cải thiện. Trước hết, tôi cần thực hành sâu hơn với AWS CLI và Infrastructure as Code để giảm phụ thuộc vào thao tác thủ công trên console.

Tôi cũng cần luyện thêm cách đọc CloudWatch Logs và debug lỗi backend trong môi trường cloud, vì đây là kỹ năng rất quan trọng nếu muốn làm việc thực tế với hệ thống đã triển khai.

Ngoài ra, tôi muốn hiểu sâu hơn về các phần network nâng cao như private subnet, NAT Gateway, VPC Endpoint và các best practices về bảo mật. Tôi cũng cần học thêm về quản lý secrets, phân quyền IAM chi tiết và cách tách môi trường dev, staging, production.

Về lâu dài, tôi muốn rèn luyện thêm khả năng tối ưu chi phí AWS khi thiết kế kiến trúc triển khai, vì đây là yếu tố rất quan trọng trong môi trường doanh nghiệp.

## 5. Bài học rút ra

Qua kỳ thực tập, tôi nhận ra AWS không chỉ là công cụ để triển khai ứng dụng. Nó còn là một cách tiếp cận giúp hệ thống được thiết kế rõ ràng, vận hành tốt hơn và dễ theo dõi hơn. Khi đưa project lên AWS, tôi phải suy nghĩ nhiều hơn về kiến trúc, quyền truy cập, database, endpoint, giám sát và khả năng mở rộng.

Tôi cũng hiểu rằng việc học cloud phải đi cùng thực hành. Nếu chỉ đọc tài liệu, các dịch vụ như Amplify, API Gateway, Elastic Beanstalk, RDS hay SES sẽ dễ bị nhìn như những phần tách rời. Nhưng khi đặt chúng vào một project cụ thể, vai trò của từng dịch vụ trở nên rất rõ ràng.

Quan trọng hơn, quá trình viết workshop giúp tôi biết cách biến kinh nghiệm triển khai thành tài liệu. Đây là một kỹ năng rất cần thiết trong môi trường cloud, vì mọi bước cấu hình đều cần được ghi lại rõ ràng để người khác có thể kiểm tra, lặp lại hoặc cải tiến về sau.

## 6. Định hướng sau thực tập

Sau kỳ thực tập, tôi muốn tiếp tục học sâu hơn về AWS theo những hướng sau:

- Thực hành triển khai hạ tầng bằng AWS CDK hoặc Terraform.
- Tìm hiểu kỹ hơn về VPC, private subnet, load balancer, security group và IAM policy.
- Bổ sung CloudWatch Logs, metrics và alarm cho backend.
- Tìm hiểu thêm về S3 upload, CloudFront, custom domain và HTTPS.
- Thực hành backup/restore database và tối ưu chi phí AWS cho môi trường demo.
- Tiếp tục hoàn thiện EAM Workspace theo hướng gần với production-ready hơn.

Nhìn chung, kỳ thực tập tại AWS giúp tôi có cái nhìn thực tế hơn về cloud computing và đặc biệt là backend trên AWS. Tôi không chỉ học thêm các dịch vụ AWS riêng lẻ, mà còn hiểu cách kết hợp chúng để xây dựng một hệ thống web hoàn chỉnh, có thể kiểm thử, giám sát và tài liệu hóa rõ ràng.
