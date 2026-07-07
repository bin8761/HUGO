---
title: "Chia sẻ và phản hồi"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

# Chia sẻ và phản hồi

Chương trình First Cloud AI Journey cho tôi một góc nhìn rất thực tế về AWS, đặc biệt là ở phần backend. Điều tôi cảm nhận rõ nhất trong suốt quá trình tham gia là chương trình không dừng ở việc học dịch vụ riêng lẻ, mà luôn kéo người học đi theo toàn bộ luồng của một hệ thống: request đi như thế nào, backend xử lý ra sao, database kết nối thế nào, log được xem ở đâu và lỗi được kiểm tra bằng cách nào sau khi deploy.

Với tôi, đây là điểm giá trị nhất của chương trình. Nó khiến việc học AWS gắn chặt hơn với cách một hệ thống backend thực sự vận hành trên cloud.

## 1. Đánh giá tổng thể

Tổng thể, tôi đánh giá chương trình rất hữu ích. Điểm mạnh của chương trình là giúp tôi hiểu rằng backend trên AWS không chỉ là viết API hay tạo database, mà còn phải biết cách deploy, quan sát, kiểm tra và xử lý lỗi trong môi trường thật.

Nhờ đó, tôi thấy kiến thức mình học được không còn nằm rời rạc nữa. Mỗi phần đều có vị trí riêng trong một kiến trúc backend hoàn chỉnh.

## 2. Trải nghiệm học backend trên AWS

Từ góc nhìn backend, điều hữu ích nhất là tôi bắt đầu nhìn rõ luồng xử lý của hệ thống:

- client gửi request
- API Gateway nhận và chuyển tiếp request
- Elastic Beanstalk chạy backend Node.js/Express
- RDS lưu dữ liệu của hệ thống
- SES hỗ trợ gửi email và OTP
- CloudWatch giúp xem log và kiểm tra trạng thái

Khi hiểu được luồng này, tôi thấy AWS dễ học hơn rất nhiều. Tôi không còn xem từng dịch vụ là những khái niệm riêng lẻ nữa, mà nhìn chúng như các lớp hỗ trợ cho backend ở các khâu khác nhau.

Chính chương trình cũng giúp tôi hiểu tại sao backend luôn cần environment variables, database credentials, network rules và health check. Đây không phải là phần phụ, mà là một phần của backend.

## 3. Trải nghiệm triển khai

Phần tôi nhớ nhất là giai đoạn triển khai. Khi deploy lên AWS, tôi phải kiểm tra rất nhiều thứ mà khi chạy local thường không nhìn thấy:

- backend có đọc đúng biến môi trường hay không
- API Gateway có trỏ đúng sang backend hay không
- chuỗi kết nối database có hợp lệ hay không
- thông tin SMTP của SES có khớp hay không
- endpoint health có trả kết quả đúng hay không
- CloudWatch logs đang cho biết lỗi nằm ở đâu

Từ những việc đó, tôi học được rằng lỗi triển khai backend hiếm khi chỉ nằm ở một chỗ. Thường nó là kết quả của nhiều cấu hình nhỏ ghép lại. Muốn xử lý tốt thì phải kiểm tra theo từng lớp thay vì đoán mò.

Tôi cũng nhận ra rằng debug backend trên AWS cần sự kiên nhẫn. Có lúc lỗi nằm trong code, nhưng cũng có lúc nó nằm ở route, ở môi trường, ở database, ở security group hoặc ở cấu hình service. Chương trình giúp tôi hình thành cách kiểm tra có hệ thống hơn.

## 4. Hỗ trợ từ mentor và team

Điều tôi đánh giá cao là cách mentor và team hỗ trợ. Thay vì đưa ngay đáp án, mọi người thường hướng dẫn tôi tự kiểm tra từng bước để hiểu nguyên nhân. Cách làm này rất phù hợp với backend, vì backend không thể xử lý tốt nếu chỉ dựa vào đoán lỗi.

Nhờ cách hỗ trợ đó, tôi học được cách kiểm tra request flow, đối chiếu cấu hình và xác định lỗi theo từng lớp của hệ thống.

Team cũng cung cấp bối cảnh kiến trúc và quy trình triển khai khá rõ ràng, nên tôi dễ liên hệ phần báo cáo với hệ thống thật hơn. Điều này rất hữu ích khi viết workshop và phần mô tả triển khai.

## 5. Phần hài lòng nhất

Phần tôi hài lòng nhất là khi tôi hiểu rõ hơn cách một backend có thể hoạt động đầy đủ trên AWS, thay vì chỉ chạy được ở máy local. Lúc đó tôi thấy rõ sự khác nhau giữa một project đã code xong và một hệ thống đã deploy, kiểm tra và giám sát được.

Điểm tôi nhớ nhất là luồng:

`API Gateway -> Elastic Beanstalk -> RDS -> SES / CloudWatch`

Với tôi, đó là lúc kiến thức AWS thực sự “khớp” lại thành một hệ thống hoàn chỉnh.

## 6. Khó khăn trong chương trình

Khó khăn lớn nhất của tôi không phải là thiếu thông tin, mà là có quá nhiều phần phải kiểm tra cùng lúc. Backend deploy trên AWS đòi hỏi phải chú ý đồng thời đến:

- routing
- environment variables
- database connection
- email credentials
- logging
- health check

Ban đầu điều đó khiến tôi hơi rối, nhưng sau một thời gian, nó buộc tôi phải học cách kiểm tra cẩn thận và có trình tự hơn. Tôi cũng thấy rõ rằng tài liệu viết tốt sẽ giúp việc debug và làm lại quy trình dễ hơn rất nhiều.

## 7. Đề xuất cho chương trình

Nếu có thể góp ý, tôi nghĩ chương trình sẽ còn hữu ích hơn nếu có thêm checklist riêng cho backend deployment. Một danh sách ngắn cho API Gateway, Elastic Beanstalk, RDS, SES và CloudWatch sẽ giúp người học tự kiểm tra nhanh hơn.

Tôi cũng thấy một tài liệu hướng dẫn troubleshoot ngắn cho các lỗi thường gặp như sai biến môi trường, lỗi health check, routing sai hoặc không kết nối được database sẽ rất thực tế.

Ngoài ra, một flow mẫu thể hiện rõ cần kiểm tra gì trước và sau khi deploy backend sẽ giúp sinh viên mới dễ hình dung hơn, nhất là khi lần đầu làm việc với AWS.

## 8. Kỳ vọng sau chương trình

Sau chương trình, tôi muốn tiếp tục đi sâu hơn theo hướng backend và cloud. Những phần tôi muốn học thêm gồm:

- AWS CDK hoặc Terraform
- CloudWatch Logs và alert
- VPC, private subnet, NAT Gateway, VPC Endpoint
- IAM policy và quản lý secrets
- backup/restore cho RDS
- các pattern deploy backend gần với production hơn

Nhìn chung, chương trình cho tôi một cái nhìn thực tế hơn về backend trên AWS. Tôi không chỉ học từng dịch vụ riêng lẻ, mà còn hiểu cách kết hợp chúng để tạo thành một hệ thống có thể deploy, theo dõi, debug và vận hành rõ ràng hơn.
