---
title : "VPC Endpoint Policies"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

Khi tạo một giao diện hoặc điểm cuối cổng, bạn có thể đính kèm chính sách điểm cuối vào đó để kiểm soát quyền truy cập vào dịch vụ mà bạn đang kết nối. Chính sách điểm cuối VPC là chính sách tài nguyên IAM mà bạn đính kèm vào điểm cuối. Nếu bạn không đính kèm chính sách khi tạo điểm cuối, AWS sẽ đính kèm chính sách mặc định cho bạn để cho phép bạn có toàn quyền truy cập vào dịch vụ thông qua điểm cuối.

Bạn có thể tạo chính sách chỉ hạn chế quyền truy cập vào các nhóm S3 cụ thể. Điều này hữu ích nếu bạn chỉ muốn một số Nhóm S3 nhất định có thể truy cập được thông qua điểm cuối.

Trong phần này, bạn sẽ tạo chính sách điểm cuối VPC hạn chế quyền truy cập vào nhóm S3 được chỉ định trong chính sách điểm cuối VPC.

![sơ đồ điểm cuối](/images/5-Workshop/5.5-Policy/s3-bucket-policy.png)

#### Kết nối với phiên bản EC2 và xác minh kết nối với S3

1. Bắt đầu phiên Trình quản lý phiên AWS mới trên phiên bản có tên Test-Gateway-Endpoint. Từ phiên này, hãy xác minh rằng bạn có thể liệt kê nội dung của nhóm bạn đã tạo trong Phần 1: Truy cập S3 từ VPC:

```
aws s3 ls s3://\<your-bucket-name\>
```
![test](/images/5-Workshop/5.5-Policy/test1.png)

Nội dung nhóm bao gồm hai tệp 1 GB được tải lên trước đó.

2. Tạo nhóm S3 mới; hãy làm theo mẫu đặt tên bạn đã sử dụng ở Phần 1, nhưng thêm '-2' vào tên. Để các trường khác làm mặc định và nhấp vào tạo

![tạo nhóm](/images/5-Workshop/5.5-Policy/create-bucket.png)

Tạo nhóm thành công

![Thành công](/images/5-Workshop/5.5-Policy/create-bucket-success.png)

3. Điều hướng đến: Dịch vụ > VPC > Điểm cuối, sau đó chọn điểm cuối Gateway VPC mà bạn đã tạo trước đó. Nhấp vào tab Chính sách. Nhấp vào Chỉnh sửa chính sách.

![chính sách](/images/5-Workshop/5.5-Policy/policy1.png)

Chính sách mặc định cho phép truy cập vào tất cả Bộ chứa S3 thông qua điểm cuối VPC.

4. Trong bảng điều khiển Chỉnh sửa chính sách, hãy sao chép và dán chính sách sau, sau đó thay thế yourbucketname-2 bằng tên nhóm thứ 2 của bạn. Chính sách này sẽ cho phép truy cập thông qua điểm cuối VPC vào bộ chứa mới của bạn chứ không phải bất kỳ bộ chứa nào khác trong Amazon S3. Nhấp vào Lưu để áp dụng chính sách.

```
{
  "Id": "Policy1631305502445",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1631305501021",
      "Action": "s3:*",
      "Effect": "Allow",
      "Resource": [
      				"arn:aws:s3:::yourbucketname-2",
       				"arn:aws:s3:::yourbucketname-2/*"
       ],
      "Principal": "*"
    }
  ]
}
```

![chính sách tùy chỉnh](/images/5-Workshop/5.5-Policy/policy2.png)

Tùy chỉnh chính sách thành công

![thành công](/static/images/5-Workshop/5.5-Policy/success.png)

5. Từ phiên của bạn trên phiên bản Test-Gateway-Endpoint, hãy kiểm tra quyền truy cập vào nhóm S3 mà bạn đã tạo trong Phần 1: Truy cập S3 từ VPC
```
aws s3 ls s3://<yourbucketname>
```

Lệnh này sẽ trả về lỗi vì chính sách điểm cuối VPC mới của bạn không cho phép quyền truy cập vào nhóm này:

![error](/static/images/5-Workshop/5.5-Policy/error.png)

6. Quay trở lại thư mục chính trên phiên bản EC2 của bạn ` cd~ `

+ Tạo một tập tin ```fallocate -l 1G test-bucket2.xyz ```
+ Sao chép tệp vào nhóm thứ 2 ```aws s3 cp test-bucket2.xyz s3://<your-2nd-bucket-name>```

![thành công](/static/images/5-Workshop/5.5-Policy/test2.png)

Hoạt động này thành công vì nó được chính sách điểm cuối VPC cho phép.

![thành công](/static/images/5-Workshop/5.5-Policy/test2-success.png)

+ Sau đó, chúng tôi kiểm tra quyền truy cập vào nhóm đầu tiên bằng cách sao chép tệp vào nhóm thứ 1 `aws s3 cp test-bucket2.xyz s3://<your-1st-bucket-name>`

![fail](/static/images/5-Workshop/5.5-Policy/test2-fail.png)

Lệnh này sẽ trả về lỗi vì chính sách điểm cuối VPC mới của bạn không cho phép quyền truy cập vào bộ chứa này.

#### Tóm tắt phần 3:

Trong phần này, bạn đã tạo chính sách điểm cuối VPC cho Amazon S3 và sử dụng AWS CLI để kiểm tra chính sách. Các hành động AWS CLI nhắm mục tiêu đến bộ chứa S3 ban đầu của bạn không thành công vì bạn đã áp dụng chính sách chỉ cho phép truy cập vào bộ chứa thứ hai mà bạn đã tạo. Các hành động AWS CLI được nhắm mục tiêu cho nhóm thứ hai của bạn đã thành công vì chính sách đã cho phép các hành động đó. Các chính sách này có thể hữu ích trong trường hợp bạn cần kiểm soát quyền truy cập vào tài nguyên thông qua điểm cuối VPC.
