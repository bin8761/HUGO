---
title : "On-premises DNS Simulation"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4.4 </b> "
---

Điểm cuối AWS PrivateLink có địa chỉ IP cố định trong mỗi Vùng sẵn sàng nơi chúng được triển khai trong suốt thời gian hoạt động của điểm cuối (cho đến khi địa chỉ đó bị xóa). Các địa chỉ IP này được gắn vào Giao diện mạng đàn hồi (ENI). AWS khuyến nghị sử dụng DNS để phân giải địa chỉ IP cho điểm cuối để các ứng dụng hạ nguồn sử dụng địa chỉ IP mới nhất khi ENI được thêm vào AZ mới hoặc bị xóa theo thời gian.

Trong phần này, bạn sẽ tạo quy tắc chuyển tiếp để gửi yêu cầu phân giải DNS từ môi trường mô phỏng tại chỗ đến Vùng lưu trữ riêng của Route 53. Phần này tận dụng cơ sở hạ tầng được CloudFormation triển khai trong phần Chuẩn bị môi trường.

#### Tạo Bản ghi bí danh DNS cho điểm cuối Giao diện
1. Điều hướng đến [Bảng điều khiển quản lý Tuyến 53](https://us-east-1.console.aws.amazon.com/route53/v2/hostedzones?region=us-east-1#) (phần Vùng được lưu trữ).  Mẫu CloudFormation mà bạn đã triển khai trong phần Chuẩn bị môi trường đã tạo Vùng lưu trữ riêng tư này. Nhấp vào tên của Vùng lưu trữ riêng tư, s3.us-east-1.amazonaws.com:

![Vùng được lưu trữ](/images/5-Workshop/5.4-S3-onprem/hosted-zone.png)

2. Tạo một bản ghi mới trong Private Hosted Zone:

![Tạo bản ghi](/images/5-Workshop/5.4-S3-onprem/create-record1.png)

+ Tên bản ghi và loại bản ghi giữ các tùy chọn mặc định
+ Nút bí danh: Nhấp để bật
+ Định tuyến lưu lượng truy cập đến: Bí danh đến Điểm cuối VPC
+ Khu vực: Miền Đông Hoa Kỳ (Bắc Virginia) [us-east-1]
+ Chọn điểm cuối: Dán tên DNS điểm cuối VPC khu vực từ trình soạn thảo văn bản của bạn (bạn đã lưu khi thực hiện phần 4.3)

![record1](/images/5-Workshop/5.4-S3-onprem/record1.png)

3. Bấm vào Thêm bản ghi khác và thêm bản ghi thứ hai bằng cách sử dụng các giá trị sau. Nhấp vào Tạo bản ghi khi hoàn tất để tạo cả hai bản ghi.
+ Tên bản ghi: *.
+ Loại bản ghi: giữ giá trị mặc định (loại A)
+ Nút bí danh: Nhấp để bật
+ Định tuyến lưu lượng truy cập đến: Bí danh đến Điểm cuối VPC
+ Khu vực: Miền Đông Hoa Kỳ (Bắc Virginia) [us-east-1]
+ Chọn điểm cuối: Dán tên DNS của điểm cuối VPC khu vực từ trình soạn thảo văn bản của bạn

![bản ghi 2](/images/5-Workshop/5.4-S3-onprem/record2.png)

Các bản ghi mới xuất hiện trong bảng điều khiển Route 53:

![kết quả](/images/5-Workshop/5.4-S3-onprem/result.png)

#### Tạo quy tắc chuyển tiếp trình giải quyết

Quy tắc chuyển tiếp trình phân giải Route 53 cho phép bạn chuyển tiếp các truy vấn DNS từ VPC của mình tới các nguồn khác để phân giải tên. Bên ngoài môi trường hội thảo, bạn có thể sử dụng tính năng này để chuyển tiếp các truy vấn DNS từ VPC của mình đến các máy chủ DNS chạy tại chỗ. Trong phần này, bạn sẽ mô phỏng trình chuyển tiếp có điều kiện tại chỗ bằng cách tạo quy tắc chuyển tiếp để chuyển tiếp các truy vấn DNS cho Amazon S3 tới Vùng lưu trữ riêng chạy trong "VPC Cloud" để phân giải tên DNS khu vực của điểm cuối giao diện PrivateLink.

1. Từ bảng điều khiển quản lý Tuyến 53, nhấp vào **Điểm cuối trong nước** trên thanh bên trái
2. Trong bảng điều khiển Điểm cuối gửi đến, hãy nhấp vào ID của điểm cuối gửi đến

![Điểm cuối gửi đến](/images/5-Workshop/5.4-S3-onprem/route53-1.png)

3. Sao chép hai địa chỉ IP được liệt kê vào trình soạn thảo văn bản của bạn

![Địa chỉ IP](/images/5-Workshop/5.4-S3-onprem/route53-2.png)

4. Từ menu Tuyến 53, chọn **Trình giải quyết** > **Quy tắc** và nhấp vào **Tạo quy tắc**:

![Địa chỉ IP](/images/5-Workshop/5.4-S3-onprem/route53-3.png)

5. Trong bảng điều khiển Tạo quy tắc:
+ Tên: myS3Rule
+ Loại quy tắc: Chuyển tiếp
+ Tên miền: s3.us-east-1.amazonaws.com

![tạo quy tắc](/images/5-Workshop/5.4-S3-onprem/route53-4.png)

+ VPC: VPC tại chỗ
+ Điểm cuối gửi đi: VPCOnpremOutboundEndpoint

![tạo quy tắc](/images/5-Workshop/5.4-S3-onprem/route53-5.png)

+ Địa chỉ IP mục tiêu: Nhập cả hai địa chỉ IP từ trình soạn thảo văn bản của bạn (địa chỉ điểm cuối gửi đến) rồi nhấp vào Gửi

![tạo quy tắc](/images/5-Workshop/5.4-S3-onprem/route53-6.png)
Bạn đã tạo thành công quy tắc chuyển tiếp trình phân giải. 

![tạo quy tắc](/images/5-Workshop/5.4-S3-onprem/route53-7.png)

#### Kiểm tra mô phỏng DNS tại chỗ

1. Kết nối với **Phiên bản EC2 giao diện thử nghiệm** bằng **Trình quản lý phiên**

![tạo quy tắc](/images/5-Workshop/5.4-S3-onprem/test1.png)

2. Kiểm tra độ phân giải DNS. Lệnh dig sẽ trả về các địa chỉ IP được gán cho điểm cuối Giao diện VPC đang chạy trong VPC Cloud (IP của bạn sẽ khác): dig +short s3.us-east-1.amazonaws.com 

{{% notice note %}}
Địa chỉ IP được trả về là địa chỉ IP điểm cuối VPC, KHÔNG phải địa chỉ IP của Trình phân giải mà bạn đã dán từ trình soạn thảo văn bản của mình. Địa chỉ IP của điểm cuối Resolver và điểm cuối VPC trông giống nhau vì chúng đều thuộc khối VPC Cloud CIDR.
{{% /notice %}}

![tạo quy tắc](/images/5-Workshop/5.4-S3-onprem/dig.png)


3. Điều hướng đến menu VPC (phần Điểm cuối), chọn điểm cuối Giao diện S3. Nhấp vào tab Mạng con và xác minh rằng các địa chỉ IP được Dig trả về khớp với điểm cuối VPC:

![tạo quy tắc](/images/5-Workshop/5.4-S3-onprem/subnet.png)

4. Quay lại shell của bạn và sử dụng AWS CLI để kiểm tra việc liệt kê các nhóm S3 của bạn:

```
aws s3 ls --endpoint-url https://s3.us-east-1.amazonaws.com
```

![tạo quy tắc](/images/5-Workshop/5.4-S3-onprem/endpoint.png)

5. Chấm dứt phiên Trình quản lý phiên của bạn:

![tạo quy tắc](/images/5-Workshop/5.4-S3-onprem/terminal.png)

Trong phần này, bạn đã tạo điểm cuối Giao diện cho Amazon S3. Bạn có thể truy cập điểm cuối này từ tại chỗ thông qua VPN Site-to-Site hoặc AWS Direct Connect. Các điểm cuối gửi đi của Bộ giải quyết Route 53 mô phỏng việc chuyển tiếp các yêu cầu DNS từ tại chỗ đến Vùng lưu trữ riêng chạy trên đám mây. Điểm cuối gửi đến Tuyến 53 đã nhận được yêu cầu giải quyết và trả về phản hồi chứa địa chỉ IP của điểm cuối giao diện VPC. Việc sử dụng DNS để phân giải các địa chỉ IP điểm cuối sẽ mang lại tính khả dụng cao trong trường hợp vùng sẵn sàng bị ngừng hoạt động.
