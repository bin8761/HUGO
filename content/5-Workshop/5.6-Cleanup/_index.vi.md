---
title : "Clean up"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---
Chúc mừng bạn đã hoàn thành hội thảo này! 
Trong hội thảo này, bạn đã tìm hiểu các mẫu kiến ​​trúc để truy cập Amazon S3 mà không cần sử dụng Internet công cộng. 
+ Bằng cách tạo điểm cuối cổng, bạn đã kích hoạt giao tiếp trực tiếp giữa tài nguyên EC2 và Amazon S3 mà không cần thông qua Cổng Internet. 
+ Bằng cách tạo điểm cuối giao diện, bạn đã mở rộng khả năng kết nối S3 tới các tài nguyên đang chạy trong trung tâm dữ liệu tại chỗ của mình thông qua VPN Site-to-Site của AWS hoặc Direct Connect. 

#### dọn dẹp
1. Điều hướng đến Vùng được lưu trữ ở phía bên trái của bảng điều khiển Route 53. Nhấp vào tên của vùng *s3.us-east-1.amazonaws.com*. Nhấp vào Xóa và xác nhận xóa bằng cách gõ xóa. 

![Vùng được lưu trữ](/images/5-Workshop/5.6-Cleanup/delete-zone.png)

2. Tách quy tắc phân giải Route 53 - myS3Rule khỏi "VPC Onprem" và xóa nó. 

![Vùng được lưu trữ](/images/5-Workshop/5.6-Cleanup/vpc.png)

4. Mở bảng điều khiển CloudFormation và xóa hai Ngăn xếp CloudFormation mà bạn đã tạo cho phòng thí nghiệm này:
+ PLonpremCài đặt
+ PLCloudThiết lập

![xóa ngăn xếp](/images/5-Workshop/5.6-Cleanup/delete-stack.png)

5. Xóa nhóm S3
+ Mở bảng điều khiển S3
+ Chọn nhóm chúng tôi đã tạo cho lab, nhấp vào và xác nhận trống. Bấm xóa và xác nhận xóa.

![xóa s3](/images/5-Workshop/5.6-Cleanup/delete-s3.png)
