---
title : "Test the Interface Endpoint"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.4.3 </b> "
---

#### Lấy tên DNS khu vực của điểm cuối giao diện S3
1. Từ menu Amazon VPC, chọn Điểm cuối.

2. Nhấp vào tên của điểm cuối mới tạo: s3-interface-endpoint. Nhấp vào chi tiết và lưu tên DNS khu vực của điểm cuối (tên đầu tiên) vào trình soạn thảo văn bản của bạn để sử dụng sau. 

![tên dns](/images/5-Workshop/5.4-S3-onprem/dns.png)


#### Kết nối với phiên bản EC2 trong "VPC tại chỗ"

1. Điều hướng đến **Trình quản lý phiên** bằng cách nhập "trình quản lý phiên" vào hộp tìm kiếm 

2. Nhấp vào **Bắt đầu phiên** và chọn phiên bản EC2 có tên **Test-Interface-Endpoint**. Phiên bản EC2 này đang chạy trong "VPC tại chỗ" và sẽ được dùng để kiểm tra khả năng kết nối với Amazon S3 thông qua điểm cuối Giao diện mà chúng tôi vừa tạo. Trình quản lý phiên sẽ mở một tab trình duyệt mới với dấu nhắc shell: **sh-4.2 $**

![Bắt đầu phiên](/images/5-Workshop/5.4-S3-onprem/start-session.png)

3. Thay đổi thư mục chính của người dùng ssm bằng lệnh "cd ~"

4. Tạo một tệp có tên testfile2.xyz
```
fallocate -l 1G testfile2.xyz
```

![user](/images/5-Workshop/5.4-S3-onprem/cli1.png)


5. Sao chép tệp vào cùng nhóm S3 mà chúng tôi đã tạo trong phần 3.2

```
aws s3 cp --endpoint-url https://bucket.<Regional-DNS-Name> testfile2.xyz s3://<your-bucket-name>
``` 
+ Lệnh này yêu cầu tham số --endpoint-url vì bạn cần sử dụng tên DNS dành riêng cho điểm cuối để truy cập S3 bằng điểm cuối Giao diện.
+ Không bao gồm ' * ' ở đầu khi sao chép/dán tên DNS khu vực.
+ Cung cấp tên nhóm S3 của bạn đã tạo trước đó

![sao chép tập tin](/images/5-Workshop/5.4-S3-onprem/cli2.png)


Bây giờ tệp đã được thêm vào nhóm S3 của bạn. Hãy kiểm tra nhóm S3 của bạn trong bước tiếp theo.

#### Kiểm tra đối tượng trong nhóm S3

1. Điều hướng đến bảng điều khiển S3
2. Nhấp vào nhóm
3. Nhấp vào tên nhóm của bạn và bạn sẽ thấy testfile2.xyz đã được thêm vào nhóm của bạn

![kiểm tra nhóm](/images/5-Workshop/5.4-S3-onprem/check-bucket.png)
