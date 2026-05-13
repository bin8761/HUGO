---
title : "Create an S3 Interface endpoint"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

Trong phần này, bạn sẽ tạo và kiểm tra điểm cuối giao diện S3 bằng môi trường mô phỏng tại chỗ được triển khai như một phần của hội thảo này.

1. Quay lại menu Amazon VPC. Trong ngăn điều hướng, chọn Điểm cuối, sau đó bấm vào Tạo điểm cuối.

2. Trong bảng điều khiển Tạo điểm cuối:
+ Đặt tên cho điểm cuối giao diện
+ Trong danh mục Dịch vụ, chọn **dịch vụ aws** 

![name](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint1.png)

3.  Trong hộp Tìm kiếm, nhập S3 và nhấn Enter. Chọn điểm cuối có tên com.amazonaws.us-east-1.s3. Đảm bảo rằng cột Loại cho biết Giao diện.

![service](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint2.png)

4. Đối với VPC, chọn VPC Cloud từ trình đơn thả xuống.
+ Mở rộng **Cài đặt bổ sung** và đảm bảo rằng *không* chọn Bật tên DNS (chúng tôi sẽ sử dụng tùy chọn này trong phần tiếp theo của hội thảo)

![vpc](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint3.png)

5. Chọn 2 subnet trong các AZ sau: us-east-1a và us-east-1b

![mạng con](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint4.png)

6. Đối với nhóm Security chọn SGforS3Endpoint:

![sg](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint5.png)

7. Giữ chính sách mặc định - toàn quyền truy cập và nhấp vào Tạo điểm cuối

![thành công](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint-success.png)

Chúc mừng bạn đã tạo thành công endpoint giao diện S3. Trong bước tiếp theo, chúng tôi sẽ kiểm tra điểm cuối giao diện.
