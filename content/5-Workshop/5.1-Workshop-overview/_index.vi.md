---
title : "Introduction"
date : 2024-01-01 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

#### Điểm cuối VPC
+ **Điểm cuối VPC** là các thiết bị ảo. Chúng là các thành phần VPC có quy mô theo chiều ngang, dự phòng và có tính sẵn sàng cao. Chúng cho phép liên lạc giữa tài nguyên điện toán của bạn và dịch vụ AWS mà không gây ra rủi ro về tính khả dụng.
+ Tài nguyên điện toán chạy trong VPC có thể truy cập **Amazon S3** bằng điểm cuối Cổng. Các tài nguyên điện toán chạy trong VPC hoặc tại chỗ có thể sử dụng điểm cuối giao diện PrivateLink.

#### Tổng quan hội thảo
Trong hội thảo này, bạn sẽ sử dụng hai VPC. 
+ **"VPC Cloud"** dành cho các tài nguyên đám mây như **Điểm cuối cổng** và phiên bản EC2 để thử nghiệm. 
+ **"VPC On-Prem"** mô phỏng môi trường tại chỗ như nhà máy hoặc trung tâm dữ liệu của công ty. Một phiên bản EC2 chạy phần mềm StrongSwan VPN đã được triển khai trong "VPC tại chỗ" và được đặt cấu hình tự động để thiết lập đường hầm VPN Site-to-Site với AWS Transit Gateway. VPN này mô phỏng kết nối từ vị trí tại chỗ đến đám mây AWS. Để giảm thiểu chi phí, chỉ có một phiên bản VPN được cung cấp để hỗ trợ hội thảo này. Khi lập kế hoạch kết nối VPN cho khối lượng công việc sản xuất của bạn, AWS khuyên bạn nên sử dụng nhiều thiết bị VPN để có tính sẵn sàng cao.

![tổng quan](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)
