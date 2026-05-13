---
title : "Create a gateway endpoint"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.3.1 </b> "
---

1. Mở [Bảng điều khiển Amazon VPC](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#Home:)
2. Trong ngăn điều hướng, chọn **Điểm cuối**, sau đó nhấp vào **Tạo điểm cuối**:

{{% notice note %}}
Bạn sẽ thấy **6 điểm cuối VPC hiện có** hỗ trợ **AWS Systems Manager (SSM)**. Những điểm cuối này được **Mẫu CloudFormation** triển khai tự động cho hội thảo này.
{{% /notice %}}

![endpoint](/images/5-Workshop/5.3-S3-vpc/endpoints.png)

3. Trong bảng điều khiển Tạo điểm cuối:
+ Chỉ định tên của điểm cuối: ```s3-gwe```
+ Trong danh mục dịch vụ, chọn **Dịch vụ AWS**

![điểm cuối](/images/5-Workshop/5.3-S3-vpc/create-s3-gwe1.png)

+ Trong **Dịch vụ**, nhập ```s3``` vào hộp tìm kiếm và chọn dịch vụ có loại **gateway**

![endpoint](/images/5-Workshop/5.3-S3-vpc/services.png)

+ Đối với VPC, chọn **VPC Cloud** từ trình đơn thả xuống.
+ Đối với **Định cấu hình bảng tuyến**, hãy chọn bảng tuyến đã được liên kết với **hai mạng con** (lưu ý: đây không phải là bảng tuyến chính cho VPC mà là bảng tuyến thứ hai do CloudFormation tạo).

![điểm cuối](/images/5-Workshop/5.3-S3-vpc/vpc.png)

+ **Đối với Chính sách**, hãy để tùy chọn mặc định, **Quyền truy cập đầy đủ**, để cho phép toàn quyền truy cập vào dịch vụ. Bạn sẽ triển khai **chính sách điểm cuối VPC** trong mô-đun phòng thí nghiệm sau này để chứng minh việc hạn chế quyền truy cập vào **nhóm S3** dựa trên chính sách.

![endpoint](/images/5-Workshop/5.3-S3-vpc/policy.png)

+ Không thêm thẻ vào điểm cuối VPC tại thời điểm này.
+ Nhấp vào **Tạo điểm cuối**, sau đó nhấp vào x sau khi nhận được thông báo tạo thành công.

![endpoint](/images/5-Workshop/5.3-S3-vpc/complete.png)
