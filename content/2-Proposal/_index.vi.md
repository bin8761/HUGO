---
title: "Đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
Trong phần này, bạn cần tóm tắt nội dung hội thảo mà bạn **dự định** tiến hành.

# Nền tảng thời tiết IoT cho nghiên cứu trong phòng thí nghiệm
## Giải pháp máy chủ AWS thống nhất để theo dõi thời tiết theo thời gian thực

### 1. Tóm tắt điều hành
Nền tảng thời tiết IoT được thiết kế cho nhóm ITea Lab tại Thành phố Hồ Chí Minh để tăng cường thu thập và phân tích dữ liệu thời tiết. Nó hỗ trợ tối đa 5 trạm thời tiết, với khả năng mở rộng lên 10-15, sử dụng các thiết bị biên Raspberry Pi có cảm biến ESP32 để truyền dữ liệu qua MQTT. Nền tảng này tận dụng các dịch vụ AWS Serverless để cung cấp khả năng giám sát theo thời gian thực, phân tích dự đoán và tiết kiệm chi phí, với quyền truy cập được giới hạn ở 5 thành viên phòng thí nghiệm thông qua Amazon Cognito.

### 2. Tuyên bố vấn đề
### Vấn đề là gì?
Các trạm thời tiết hiện tại yêu cầu thu thập dữ liệu thủ công, trở nên khó quản lý với nhiều đơn vị. Không có hệ thống tập trung cho dữ liệu hoặc phân tích thời gian thực và nền tảng của bên thứ ba rất tốn kém và quá phức tạp.

### Giải pháp
Nền tảng này sử dụng AWS IoT Core để thu thập dữ liệu MQTT, AWS Lambda và API Gateway để xử lý, Amazon S3 để lưu trữ (bao gồm hồ dữ liệu), cũng như các công việc AWS Glue Crawler và ETL để trích xuất, chuyển đổi và tải dữ liệu từ hồ dữ liệu S3 sang bộ chứa S3 khác để phân tích. AWS Amplify with Next.js cung cấp giao diện web và Amazon Cognito đảm bảo quyền truy cập an toàn. Tương tự như Thingsboard và CoreIoT, người dùng có thể đăng ký thiết bị mới và quản lý kết nối, mặc dù nền tảng này hoạt động ở quy mô nhỏ hơn và được thiết kế cho mục đích sử dụng cá nhân. Các tính năng chính bao gồm bảng điều khiển thời gian thực, phân tích xu hướng và chi phí vận hành thấp.

### Lợi ích và lợi tức đầu tư
Giải pháp này thiết lập nguồn tài nguyên nền tảng cho các thành viên phòng thí nghiệm để phát triển nền tảng IoT lớn hơn, đóng vai trò là tài nguyên nghiên cứu và cung cấp nền tảng dữ liệu cho những người đam mê AI để đào tạo hoặc phân tích mô hình. Nó giảm bớt việc báo cáo thủ công cho từng trạm thông qua nền tảng tập trung, đơn giản hóa việc quản lý và bảo trì, đồng thời cải thiện độ tin cậy của dữ liệu. Chi phí hàng tháng là 0,66 USD cho mỗi Bộ tính giá AWS, với tổng chi phí trong 12 tháng là 7,92 USD. Tất cả chi phí thiết bị IoT đều được chi trả bởi việc thiết lập trạm thời tiết hiện có, loại bỏ các chi phí phát triển bổ sung. Khoảng thời gian hòa vốn từ 6-12 tháng đạt được nhờ tiết kiệm đáng kể thời gian nhờ giảm bớt công việc thủ công.

### 3. Kiến trúc giải pháp
Nền tảng này sử dụng kiến ​​trúc AWS không có máy chủ để quản lý dữ liệu từ 5 trạm dựa trên Raspberry Pi, có thể mở rộng lên 15. Dữ liệu được nhập qua AWS IoT Core, được lưu trữ trong hồ dữ liệu S3 và được xử lý bởi AWS Glue Crawler và các tác vụ ETL để chuyển đổi và tải dữ liệu đó vào một bộ chứa S3 khác để phân tích. Lambda và API Gateway xử lý quá trình xử lý bổ sung, trong khi Amplify with Next.js lưu trữ bảng thông tin, được bảo mật bằng Cognito. Kiến trúc được trình bày chi tiết dưới đây:

![Kiến trúc trạm thời tiết IoT](/images/2-Proposal/edge_architecture.jpeg)

![Kiến trúc nền tảng thời tiết IoT](/images/2-Proposal/platform_architecture.jpeg)

### Dịch vụ AWS đã sử dụng
- **AWS IoT Core**: Nhập dữ liệu MQTT từ 5 trạm, có thể mở rộng lên 15.
- **AWS Lambda**: Xử lý dữ liệu và kích hoạt công việc Glue (hai chức năng).
- **Cổng API của Amazon**: Tạo điều kiện giao tiếp với ứng dụng web.
- **Amazon S3**: Lưu trữ dữ liệu thô trong hồ dữ liệu và kết quả đầu ra được xử lý (hai nhóm).
- **AWS Glue**: Dữ liệu danh mục của trình thu thập thông tin và các công việc ETL chuyển đổi và tải dữ liệu đó.
- **AWS Amplify**: Lưu trữ giao diện web Next.js.
- **Amazon Cognito**: Đảm bảo quyền truy cập cho người dùng phòng thí nghiệm.

### Thiết kế thành phần
- **Thiết bị biên**: Raspberry Pi thu thập và lọc dữ liệu cảm biến, gửi dữ liệu đó đến IoT Core.
- **Nhập dữ liệu**: AWS IoT Core nhận tin nhắn MQTT từ các thiết bị biên.
- **Lưu trữ dữ liệu**: Dữ liệu thô được lưu trữ trong hồ dữ liệu S3; dữ liệu đã xử lý được lưu trữ trong một nhóm S3 khác.
- **Xử lý dữ liệu**: AWS Glue Crawler lập danh mục dữ liệu và các tác vụ ETL chuyển đổi dữ liệu đó để phân tích.
- **Giao diện web**: AWS Amplify lưu trữ ứng dụng Next.js cho bảng thông tin và phân tích theo thời gian thực.
- **Quản lý người dùng**: Amazon Cognito quản lý quyền truy cập của người dùng, cho phép tối đa 5 tài khoản đang hoạt động.

### 4. Triển khai kỹ thuật
**Các giai đoạn thực hiện**
Dự án này có hai phần—thiết lập các trạm biên thời tiết và xây dựng nền tảng thời tiết—mỗi phần gồm 4 giai đoạn sau:
- Xây dựng lý thuyết và kiến ​​trúc vẽ: Nghiên cứu thiết lập Raspberry Pi với cảm biến ESP32 và thiết kế kiến ​​trúc serverless AWS (1 tháng trước khi thực tập)
- Tính giá và kiểm tra tính thực tiễn: Sử dụng Công cụ tính giá AWS để ước tính chi phí và điều chỉnh nếu cần (Tháng 1).
- Khắc phục Kiến trúc để đảm bảo chi phí hoặc Phù hợp với giải pháp: Tinh chỉnh thiết kế (ví dụ: tối ưu hóa Lambda với Next.js) để duy trì hiệu quả về mặt chi phí và có thể sử dụng được (Tháng 2).
- Phát triển, thử nghiệm và triển khai: Viết mã thiết lập Raspberry Pi, dịch vụ AWS bằng CDK/SDK và ứng dụng Next.js, sau đó thử nghiệm và phát hành vào sản xuất (Tháng 2-3).

**Yêu cầu kỹ thuật**
- Trạm biên thời tiết: Các cảm biến (nhiệt độ, độ ẩm, lượng mưa, tốc độ gió), bộ vi điều khiển (ESP32) và Raspberry Pi làm thiết bị biên. Raspberry Pi chạy Raspbian, xử lý Docker để lọc và gửi 1 MB/ngày mỗi trạm qua MQTT qua Wi-Fi.
- Nền tảng thời tiết: Kiến thức thực tế về AWS Amplify (lưu trữ Next.js), Lambda (mức sử dụng tối thiểu do Next.js), AWS Glue (ETL), S3 (hai nhóm), IoT Core (cổng và quy tắc) và Cognito (5 người dùng). Sử dụng AWS CDK/SDK để mã hóa các tương tác (ví dụ: quy tắc IoT Core thành S3). Next.js giảm khối lượng công việc Lambda cho ứng dụng web fullstack.

### 5. Dòng thời gian & các cột mốc quan trọng
**Dòng thời gian của dự án**
- Trước khi thực tập (Tháng 0): 1 tháng để lập kế hoạch và đánh giá trạm cũ.
- Thực tập (Tháng 1-3): 3 tháng.
    - Tháng 1: Nghiên cứu AWS và nâng cấp phần cứng.
    - Tháng 2: Thiết kế và điều chỉnh kiến ​​trúc.
    - Tháng 3: Triển khai, thử nghiệm và triển khai.
- Sau khi ra mắt: Tối đa 1 năm cho nghiên cứu.

### 6. Dự toán ngân sách
Bạn có thể tìm thấy ước tính ngân sách trên [Công cụ tính giá AWS](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01).  
Hoặc bạn có thể tải xuống [Tệp dự toán ngân sách](../attachments/budget_estimation.pdf).

### Chi phí cơ sở hạ tầng
- Dịch vụ AWS:
    - AWS Lambda: 0,00 USD/tháng (1.000 yêu cầu, dung lượng lưu trữ 512 MB).
    - Tiêu chuẩn S3: 0,15 USD/tháng (6 GB, 2.100 yêu cầu, 1 GB được quét).
    - Truyền dữ liệu: 0,02 USD/tháng (1 GB gửi vào, 1 GB gửi đi).
    - AWS Amplify: 0,35 USD/tháng (yêu cầu 256 MB, 500 ms).
    - Cổng API Amazon: 0,01 USD/tháng (2.000 yêu cầu).
    - Công việc AWS Glue ETL: 0,02 USD/tháng (2 DPU).
    - Trình thu thập keo AWS: 0,07 USD/tháng (1 trình thu thập thông tin).
    - MQTT (IoT Core): 0,08 USD/tháng (5 thiết bị, 45.000 tin nhắn).

Tổng cộng: 0,7 USD/tháng, 8,40 USD/12 tháng

- Phần cứng: $265 một lần (Raspberry Pi 5 và cảm biến).

### 7. Đánh giá rủi ro
#### Ma trận rủi ro
- Mất mạng: Tác động trung bình, xác suất trung bình.
- Lỗi cảm biến: Tác động cao, xác suất thấp.
- Vượt chi phí: Tác động trung bình, xác suất thấp.

#### Chiến lược giảm thiểu
- Mạng: Bộ nhớ cục bộ trên Raspberry Pi với Docker.
- Cảm biến: Kiểm tra thường xuyên và thay thế phụ tùng.
- Chi phí: Cảnh báo và tối ưu hóa ngân sách AWS.

#### kế hoạch dự phòng
- Hoàn nguyên về phương pháp thủ công nếu AWS không thành công.
- Sử dụng CloudFormation để khôi phục liên quan đến chi phí.

### 8. Kết quả mong đợi
#### Cải tiến kỹ thuật: 
Dữ liệu và phân tích thời gian thực thay thế các quy trình thủ công.  
Có thể mở rộng tới 10-15 trạm.
#### Giá trị lâu dài
Nền tảng dữ liệu 1 năm cho nghiên cứu AI.  
Có thể tái sử dụng cho các dự án trong tương lai.
