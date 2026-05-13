---
title : "Access S3 from on-premises"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Tổng quan

+ Trong phần này, bạn sẽ tạo điểm cuối Giao diện để truy cập Amazon S3 từ môi trường mô phỏng tại chỗ. Điểm cuối Giao diện sẽ cho phép bạn định tuyến đến Amazon S3 qua kết nối VPN từ môi trường mô phỏng tại chỗ của bạn.

+ Tại sao nên sử dụng **Điểm cuối giao diện**: 
    + Điểm cuối cổng chỉ hoạt động với các tài nguyên đang chạy trong VPC nơi chúng được tạo. Điểm cuối giao diện hoạt động với các tài nguyên chạy trong VPC cũng như các tài nguyên chạy trong môi trường tại chỗ. Khả năng kết nối từ môi trường tại chỗ của bạn đến đám mây có thể được cung cấp bởi VPN Site-to-Site của AWS hoặc AWS Direct Connect.
    + Điểm cuối giao diện cho phép bạn kết nối với các dịch vụ được cung cấp bởi AWS PrivateLink. Các dịch vụ này bao gồm một số dịch vụ AWS, dịch vụ được lưu trữ bởi các khách hàng và đối tác AWS khác trong VPC của chính họ (được gọi là Dịch vụ điểm cuối PrivateLink) và các dịch vụ Đối tác AWS Marketplace được hỗ trợ. Đối với hội thảo này, chúng tôi sẽ tập trung vào việc kết nối với Amazon S3.

![Kiến trúc điểm cuối giao diện](/images/5-Workshop/5.4-S3-onprem/diagram3.png)
