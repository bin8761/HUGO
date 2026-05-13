---
title: "Xưởng"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---
# Bảo mật quyền truy cập kết hợp vào S3 bằng cách sử dụng Điểm cuối VPC

#### Tổng quan

**AWS PrivateLink** cung cấp kết nối riêng tư tới các dịch vụ AWS từ VPC và mạng tại chỗ của bạn mà không làm lộ lưu lượng truy cập của bạn ra Internet Công cộng.

Trong phòng thực hành này, bạn sẽ tìm hiểu cách tạo, đặt cấu hình và kiểm tra các điểm cuối VPC cho phép khối lượng công việc của bạn tiếp cận các dịch vụ AWS mà không cần truyền qua Internet công cộng.

Bạn sẽ tạo hai loại điểm cuối để truy cập Amazon S3: điểm cuối Gateway VPC và điểm cuối Interface VPC. Hai loại điểm cuối VPC này mang lại những lợi ích khác nhau tùy thuộc vào việc bạn đang truy cập Amazon S3 từ đám mây hay vị trí tại chỗ của mình
+ **Cổng** - Tạo điểm cuối cổng để gửi lưu lượng truy cập đến Amazon S3 hoặc DynamoDB bằng địa chỉ IP riêng. Bạn định tuyến lưu lượng truy cập từ VPC đến điểm cuối cổng bằng bảng lộ trình.
+ **Giao diện** - Tạo điểm cuối giao diện để gửi lưu lượng truy cập đến các dịch vụ điểm cuối sử dụng Network Load Balancer để phân phối lưu lượng truy cập. Lưu lượng truy cập dành cho dịch vụ điểm cuối được giải quyết bằng DNS.

#### Nội dung

1. [Tổng quan về hội thảo](5.1-Tổng quan về hội thảo)
2. [Điều kiện tiên quyết](5.2-Điều kiện tiên quyết/)
3. [Truy cập S3 từ VPC](5.3-S3-vpc/)
4. [Truy cập S3 từ tại chỗ](5.4-S3-onprem/)
5. [Chính sách điểm cuối VPC (Tiền thưởng)](5.5-Chính sách/)
6. [Dọn dẹp](5.6-Dọn dẹp/)
