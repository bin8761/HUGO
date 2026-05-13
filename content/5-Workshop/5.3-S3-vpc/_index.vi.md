---
title : "Access S3 from VPC"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Sử dụng điểm cuối Gateway

Trong phần này, bạn sẽ tạo **điểm cuối Gateway** để truy cập **Amazon S3** từ **phiên bản EC2**. **Điểm cuối của Cổng** sẽ cho phép tải một đối tượng lên bộ chứa S3 mà không cần sử dụng **Internet công cộng**. Để tạo điểm cuối, bạn phải chỉ định VPC mà bạn muốn tạo điểm cuối và dịch vụ (trong trường hợp này là S3) mà bạn muốn thiết lập kết nối.

![tổng quan](/images/5-Workshop/5.3-S3-vpc/diagram2.png)

#### Nội dung

- [Tạo điểm cuối cổng](3.1-create-gwe/)
- [Điểm cuối cổng kiểm tra](3.2-test-gwe/)
