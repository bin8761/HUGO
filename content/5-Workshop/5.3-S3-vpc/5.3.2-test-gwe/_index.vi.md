---
title : "Test the Gateway Endpoint"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.3.2 </b> "
---

#### Tạo nhóm S3

1. Điều hướng tới **Bảng điều khiển quản lý S3**
2. Trong bảng điều khiển Nhóm, chọn **Tạo nhóm**

![Tạo nhóm](/images/5-Workshop/5.3-S3-vpc/create-bucket.png)

3. Trong **bảng điều khiển Tạo nhóm**
+ **Đặt tên cho nhóm**: chọn tên chưa được đặt cho bất kỳ nhóm nào trên toàn cầu (gợi ý: số phòng thí nghiệm và tên của bạn)

![Tên nhóm](/images/5-Workshop/5.3-S3-vpc/bucket-name.png)

+ Để nguyên các trường khác (mặc định)
+ Cuộn xuống và chọn **Tạo nhóm**

![Tạo](/images/5-Workshop/5.3-S3-vpc/create-button.png) 

+ Tạo thành công nhóm S3.

![Thành công](/images/5-Workshop/5.3-S3-vpc/bucket-success.png)

#### Kết nối với EC2 bằng trình quản lý phiên

+ Đối với hội thảo này, bạn sẽ sử dụng **Trình quản lý phiên AWS** để truy cập một số phiên bản **EC2**. **Trình quản lý phiên** là chức năng **AWS Systems Manager** được quản lý toàn phần, cho phép bạn quản lý **phiên bản Amazon EC2** và máy ảo (VM) tại chỗ thông qua trình bao tương tác dựa trên trình duyệt chỉ bằng một cú nhấp chuột. Trình quản lý phiên cung cấp khả năng quản lý phiên bản an toàn và có thể kiểm tra mà không cần mở cổng vào, duy trì máy chủ pháo đài hoặc quản lý khóa SSH.

+ Hành trình đám mây đầu tiên [Lab](https://000058.awsstudygroup.com/1-introduce/) để hiểu sâu hơn về Trình quản lý phiên.

1. Trong **Bảng điều khiển quản lý AWS**, bắt đầu nhập ```Systems Manager``` vào hộp tìm kiếm nhanh và nhấn **Enter**:

![quản lý hệ thống](/images/5-Workshop/5.3-S3-vpc/sm.png)

2. Từ menu **Trình quản lý hệ thống**, tìm **Quản lý nút** ở menu bên trái và nhấp vào **Trình quản lý phiên**:

![quản lý hệ thống](/images/5-Workshop/5.3-S3-vpc/sm1.png)

3. Nhấp vào **Bắt đầu phiên** và chọn **phiên bản EC2** có tên **Test-Gateway-Endpoint**. 
{{% notice info %}}
Phiên bản EC2 này hiện đang chạy trong "VPC Cloud" và sẽ được dùng để kiểm tra khả năng kết nối với Amazon S3 thông qua điểm cuối Gateway mà bạn vừa tạo (s3-gwe). {{% /notice %}}

![Bắt đầu phiên](/images/5-Workshop/5.3-S3-vpc/start-session.png)

**Trình quản lý phiên** sẽ mở một tab trình duyệt mới với dấu nhắc shell: sh-4.2 $

![Thành công](/images/5-Workshop/5.3-S3-vpc/start-session-success.png)

Bạn đã bắt đầu phiên thành công - kết nối với phiên bản EC2 trên đám mây VPC. Trong bước tiếp theo, chúng ta sẽ tạo vùng lưu trữ S3 và một tệp trong đó. 

#### Tạo một tập tin và tải lên thùng s3

1. Thay đổi thư mục chính của ssm-user bằng cách gõ ```cd ~``` trong CLI

![Thay đổi thư mục của người dùng](/images/5-Workshop/5.3-S3-vpc/cli1.png)

2. Tạo một tệp mới để sử dụng cho việc kiểm tra bằng lệnh ```fallocate -l 1G testfile.xyz```, lệnh này sẽ tạo một tệp có kích thước 1GB có tên là "testfile.xyz".

![Tạo tập tin](/images/5-Workshop/5.3-S3-vpc/cli-file.png)

3. Tải tệp lên vùng lưu trữ S3 bằng lệnh ```aws s3 cp testfile.xyz s3://your-bucket-name```. Thay thế your-bucket-name bằng tên của nhóm S3 mà bạn đã tạo trước đó.

![Đã tải lên](/images/5-Workshop/5.3-S3-vpc/uploaded.png)

Bạn đã tải thành công tệp lên nhóm S3 của mình. Bây giờ bạn có thể chấm dứt phiên.

#### Kiểm tra đối tượng trong nhóm S3

1. Điều hướng đến bảng điều khiển S3.  
2. Nhấp vào tên nhóm s3 của bạn
3. Trong bảng điều khiển Bucket, bạn sẽ thấy tệp bạn đã tải lên bộ chứa S3 của mình

![Kiểm tra S3](/images/5-Workshop/5.3-S3-vpc/check-s3-bucket.png)

#### Phần tóm tắt

Chúc mừng bạn đã hoàn thành quyền truy cập vào S3 từ VPC. Trong phần này, bạn đã tạo điểm cuối Cổng cho Amazon S3 và sử dụng AWS CLI để tải đối tượng lên. Quá trình tải lên thành công vì điểm cuối của Cổng cho phép liên lạc với S3 mà không cần Cổng Internet được gắn vào "VPC Cloud". Điều này thể hiện chức năng của điểm cuối Gateway như một đường dẫn an toàn đến S3 mà không cần truy cập Internet Công cộng.
