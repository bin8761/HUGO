---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
# Bắt đầu với Hồ dữ liệu chăm sóc sức khỏe: Sử dụng vi dịch vụ

Hồ dữ liệu có thể giúp các bệnh viện và cơ sở chăm sóc sức khỏe biến dữ liệu thành thông tin chi tiết về doanh nghiệp, duy trì tính liên tục trong kinh doanh và bảo vệ quyền riêng tư của bệnh nhân. **Hồ dữ liệu** là kho lưu trữ tập trung, được quản lý và bảo mật để lưu trữ tất cả dữ liệu của bạn, cả ở dạng thô và đã xử lý để phân tích. Hồ dữ liệu cho phép bạn chia nhỏ các kho dữ liệu và kết hợp các loại phân tích khác nhau để hiểu rõ hơn và đưa ra quyết định kinh doanh tốt hơn.

Bài đăng trên blog này là một phần của loạt bài lớn hơn về cách bắt đầu thiết lập hồ dữ liệu chăm sóc sức khỏe. Trong bài đăng cuối cùng của loạt bài này, *“Bắt đầu với Hồ dữ liệu chăm sóc sức khỏe: Đi sâu vào Amazon Cognito”*, tôi tập trung vào các chi tiết cụ thể về việc sử dụng Amazon Cognito và Kiểm soát truy cập dựa trên thuộc tính (ABAC) để xác thực và ủy quyền cho người dùng trong giải pháp hồ dữ liệu chăm sóc sức khỏe. Trong blog này, tôi trình bày chi tiết cách giải pháp phát triển ở cấp độ cơ bản, bao gồm các quyết định thiết kế mà tôi đã đưa ra và các tính năng bổ sung được sử dụng. Bạn có thể truy cập các mẫu mã cho giải pháp trong kho Git này để tham khảo.

---

## Hướng dẫn kiến ​​trúc

Thay đổi chính kể từ lần trình bày cuối cùng về kiến ​​trúc tổng thể là việc phân tách một dịch vụ thành một tập hợp các dịch vụ nhỏ hơn để cải thiện khả năng bảo trì và tính linh hoạt. Việc tích hợp một khối lượng lớn dữ liệu chăm sóc sức khỏe đa dạng thường yêu cầu các trình kết nối chuyên dụng cho từng định dạng; bằng cách đóng gói chúng riêng biệt dưới dạng vi dịch vụ, chúng ta có thể thêm, xóa và sửa đổi từng trình kết nối mà không ảnh hưởng đến các trình kết nối khác. Các vi dịch vụ được liên kết lỏng lẻo thông qua tin nhắn xuất bản/đăng ký tập trung vào cái mà tôi gọi là “trung tâm pub/sub”.

Giải pháp này thể hiện những gì tôi cho là một lần lặp nước rút hợp lý khác từ bài đăng trước của tôi. Phạm vi vẫn bị giới hạn ở việc nhập và phân tích cú pháp cơ bản của **thông báo HL7v2** được định dạng trong **Quy tắc mã hóa 7 (ER7)** thông qua giao diện REST.

**Cấu trúc giải pháp hiện tại như sau:**

> *Hình 1. Kiến trúc tổng thể; các hộp màu tượng trưng cho các dịch vụ riêng biệt.*

---

Mặc dù thuật ngữ *microservices* có một số điểm mơ hồ cố hữu nhưng có một số đặc điểm chung sau:  
- Nhỏ, tự chủ, liên kết lỏng lẻo  
- Có thể tái sử dụng, giao tiếp thông qua các giao diện được xác định rõ ràng  
- Chuyên làm tốt một việc  
- Thường được triển khai theo **kiến trúc hướng sự kiện**

Khi xác định nơi cần vạch ra ranh giới giữa các vi dịch vụ, hãy cân nhắc:  
- **Nội tại**: công nghệ được sử dụng, hiệu suất, độ tin cậy, khả năng mở rộng  
- **Bên ngoài**: chức năng phụ thuộc, tốc độ thay đổi, khả năng sử dụng lại  
- **Con người**: quyền sở hữu nhóm, quản lý *tải nhận thức*

---

## Lựa chọn công nghệ và phạm vi truyền thông

| Phạm vi giao tiếp                       | Công nghệ/mô hình cần xem xét                                                        |
| ----------------------------------------- | ------------------------------------------------------------------------------------------ |
| Trong một microservice duy nhất              | Dịch vụ xếp hàng đơn giản của Amazon (Amazon SQS), AWS Step Functions                               |
| Giữa các vi dịch vụ trong một dịch vụ | Tài liệu tham khảo xếp chồng chéo AWS CloudFormation, Dịch vụ thông báo đơn giản của Amazon (Amazon SNS) |
| Giữa các dịch vụ                          | Amazon EventBridge, Bản đồ đám mây AWS, Cổng API Amazon                                      |

---

## Trung tâm quán rượu/phụ

Việc sử dụng kiến ​​trúc **trung tâm và nan hoa** (hoặc trình trung chuyển tin nhắn) hoạt động hiệu quả với một số lượng nhỏ vi dịch vụ có liên quan chặt chẽ.  
- Mỗi microservice chỉ phụ thuộc vào *hub*  
- Kết nối giữa các dịch vụ vi mô được giới hạn ở nội dung của tin nhắn được xuất bản  
- Giảm số lượng cuộc gọi đồng bộ vì pub/sub là không đồng bộ một chiều *đẩy*

Nhược điểm: **cần phối hợp và giám sát** để tránh vi dịch vụ xử lý sai thông báo.

---

## Dịch vụ vi mô cốt lõi

Cung cấp dữ liệu nền tảng và lớp giao tiếp, bao gồm:  
- **Nhóm Amazon S3** dành cho dữ liệu  
- **Amazon DynamoDB** cho danh mục dữ liệu  
- **AWS Lambda** để ghi thông báo vào hồ dữ liệu và danh mục  
- **Chủ đề Amazon SNS** là *trung tâm*  
- **Bộ chứa Amazon S3** dành cho các thành phần lạ như mã Lambda

> Chỉ cho phép quyền truy cập ghi gián tiếp vào hồ dữ liệu thông qua hàm Lambda â†’ để đảm bảo tính nhất quán.

---

## Dịch vụ vi mô cửa trước

- Cung cấp Cổng API để tương tác REST bên ngoài  
- Xác thực và ủy quyền dựa trên **OIDC** qua **Amazon Cognito**  
- Cơ chế *loại bỏ trùng lặp* tự quản lý bằng DynamoDB thay vì SNS FIFO vì:  
  1. Chống trùng lặp SNS TTL chỉ trong 5 phút  
  2. SNS FIFO yêu cầu SQS FIFO  
  3. Khả năng chủ động thông báo cho người gửi rằng tin nhắn bị trùng lặp  

---

## Dàn dựng microservice ER7

- Lambda “trigger” đã đăng ký vào pub/sub hub, lọc tin nhắn theo thuộc tính  
- Step Functions Express Workflow để chuyển đổi ER7 â†’ JSON  
- Hai Lambda:  
  1. Sửa định dạng ER7 (dòng mới, xuống dòng)  
  2. Logic phân tích cú pháp  
- Kết quả hoặc lỗi được đẩy trở lại trung tâm pub/sub  

---

## Các tính năng mới trong giải pháp

### 1. Tài liệu tham khảo ngăn xếp chéo AWS CloudFormation
Ví dụ *đầu ra* trong vi dịch vụ cốt lõi:
```yaml
Outputs:
  Bucket:
    Value: !Ref Bucket
    Export:
      Name: !Sub ${AWS::StackName}-Bucket
  ArtifactBucket:
    Value: !Ref ArtifactBucket
    Export:
      Name: !Sub ${AWS::StackName}-ArtifactBucket
  Topic:
    Value: !Ref Topic
    Export:
      Name: !Sub ${AWS::StackName}-Topic
  Catalog:
    Value: !Ref Catalog
    Export:
      Name: !Sub ${AWS::StackName}-Catalog
  CatalogArn:
    Value: !GetAtt Catalog.Arn
    Export:
      Name: !Sub ${AWS::StackName}-CatalogArn
