---
title : "Prepare the environment"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.4.1 </b> "
---

Để chuẩn bị cho phần này của workshop, bạn sẽ cần:
+ Triển khai ngăn xếp CloudFormation 
+ Sửa đổi bảng lộ trình VPC. 

Các thành phần này phối hợp với nhau để mô phỏng quá trình phân giải tên và chuyển tiếp DNS tại chỗ.

#### Triển khai ngăn xếp CloudFormation

Mẫu CloudFormation sẽ tạo các dịch vụ bổ sung để hỗ trợ mô phỏng tại chỗ:
+ Một vùng lưu trữ riêng của Route 53 lưu trữ các bản ghi Bí danh cho điểm cuối PrivateLink S3
+ Một điểm cuối của Bộ giải quyết nội bộ Route 53 cho phép "VPC Cloud" giải quyết các yêu cầu phân giải DNS gửi đến Vùng lưu trữ riêng tư
+ Một điểm cuối của Bộ phân giải gửi đi Route 53 cho phép "VPC tại chỗ" chuyển tiếp các yêu cầu DNS cho S3 tới "VPC Cloud"

![sơ đồ tuyến đường 53](/images/5-Workshop/5.4-S3-onprem/route53.png)

1. Nhấp vào liên kết sau để mở [Bảng điều khiển AWS CloudFormation](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateURL=https://s3.amazonaws.com/reinvent-endpoints-builders-session/R53CF.yaml&stackName=PLOnpremSetup). Mẫu được yêu cầu sẽ được tải sẵn vào menu. Chấp nhận tất cả mặc định và nhấp vào Tạo ngăn xếp.

![Tạo ngăn xếp](/images/5-Workshop/5.4-S3-onprem/create-stack.png)

![Button](/images/5-Workshop/5.4-S3-onprem/create-stack-button.png)

Có thể mất vài phút để quá trình triển khai ngăn xếp hoàn tất. Bạn có thể tiếp tục bước tiếp theo mà không cần đợi quá trình triển khai kết thúc.

#### Cập nhật bảng lộ trình riêng tại chỗ

Hội thảo này sử dụng VPN StrongSwan chạy trên phiên bản EC2 để mô phỏng khả năng kết nối giữa trung tâm dữ liệu tại chỗ và đám mây AWS. Hầu hết các thành phần cần thiết đều được cung cấp trước khi bạn bắt đầu. Để hoàn thiện cấu hình VPN, bạn sẽ sửa đổi bảng định tuyến "VPC tại chỗ" để hướng lưu lượng truy cập dành cho đám mây tới phiên bản VPN strongSwan.

1. Mở bảng điều khiển Amazon EC2 

2. Chọn phiên bản có tên infra-vpngw-test. Từ tab Chi tiết, sao chép ID phiên bản và dán mã này vào trình soạn thảo văn bản của bạn

![ec2 id](/images/5-Workshop/5.4-S3-onprem/ec2-onprem-id.png)

3. Điều hướng đến menu VPC bằng cách sử dụng hộp Tìm kiếm ở đầu cửa sổ trình duyệt.

4. Nhấp vào Bảng định tuyến, chọn bảng lộ trình RT Private On-prem, chọn tab Tuyến và nhấp vào Chỉnh sửa tuyến.

![rt](/images/5-Workshop/5.4-S3-onprem/rt.png)

5. Nhấp vào Thêm tuyến đường.
+ Đích: phạm vi cidr Cloud VPC của bạn
+ Mục tiêu: ID của phiên bản infra-vpngw-test của bạn (bạn đã lưu trong trình chỉnh sửa ở bước 1)

![thêm tuyến](/images/5-Workshop/5.4-S3-onprem/add-route.png)

6. Nhấp vào Lưu thay đổi
