---
title: "Tuần 10 Worklog"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
### Khoảng thời gian:

* Từ 22/06/2026 đến 28/06/2026

### Mục tiêu tuần 10:

* Hoàn thiện kiến trúc AWS cho dự án để luồng triển khai rõ ràng và dễ theo dõi hơn.
* Triển khai ứng dụng lên AWS và rà soát các vấn đề phát sinh trong lần deploy đầu tiên.
* Kiểm thử lại dự án sau khi deploy để xác nhận hệ thống hoạt động đúng như mong đợi.

Tuần này là giai đoạn triển khai thực tế đầu tiên của dự án lên AWS. Sau khi kiến trúc đã được thảo luận ở các tuần trước, trọng tâm chuyển sang đưa hệ thống lên cloud, kiểm tra hành vi thực tế khi chạy và điều chỉnh lại cấu hình dựa trên kết quả kiểm thử.

### Các công việc cần thực hiện trong tuần này:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Phác thảo lại kiến trúc AWS chi tiết hơn và bắt đầu triển khai dự án lên AWS.<br>- Rà soát các dịch vụ chính sẽ tham gia vào luồng triển khai.<br>- Thực hiện bước deploy đầu tiên và kiểm tra các vấn đề về cấu hình. | 22/06/2026 | 23/06/2026 | AWS Console |
| 2 | Kiểm tra lại phần triển khai ban đầu và điều chỉnh môi trường nếu cần thiết.<br>- Kiểm tra cấu hình tài nguyên, kết nối và các phụ thuộc giữa dịch vụ.<br>- Ghi lại những điểm còn thiếu có thể ảnh hưởng đến bước kiểm thử tiếp theo. | 23/06/2026 | 24/06/2026 | Thảo luận nhóm |
| 3 | Test dự án sau khi triển khai lên AWS.<br>- Xác minh ứng dụng có thể chạy đúng trong môi trường AWS.<br>- Quan sát hành vi sau khi deploy và ghi nhận các lỗi cần xử lý thêm. | 24/06/2026 | 25/06/2026 | AWS Console |
| 4 | Sửa và tinh chỉnh dự án dựa trên kết quả kiểm thử sau deploy.<br>- Điều chỉnh kiến trúc hoặc cấu hình ở những phần phát hiện vấn đề.<br>- Kiểm tra lại luồng chạy chính sau mỗi lần cập nhật. | 25/06/2026 | 26/06/2026 | Thảo luận nhóm |
| 5 | Kiểm thử lại phần triển khai đã cập nhật để xác nhận các thay đổi hoạt động đúng.<br>- Chạy lại các luồng kiểm tra chính trên AWS sau khi áp dụng sửa lỗi.<br>- So sánh hành vi trước và sau khi điều chỉnh. | 27/06/2026 | 27/06/2026 | AWS Console |
| 6 | Tổng kết cuối tuần và chuẩn bị nội dung báo cáo.<br>- Rà soát trạng thái deploy cuối cùng và ghi lại các ghi chú quan trọng cho báo cáo.<br>- Sắp xếp các đầu việc còn lại cho những tuần sau. | 28/06/2026 | 28/06/2026 | Thảo luận nhóm |

### Kết quả đạt được:

* Hoàn tất bước deploy đầu tiên của dự án lên AWS và xác định được các điểm cấu hình quan trọng.
* Kiểm tra được ứng dụng sau khi triển khai và xác nhận luồng chạy chính trên AWS.
* Cải thiện cấu hình triển khai dựa trên kết quả kiểm thử và chuẩn bị các ghi chú cần thiết cho báo cáo.
* Hiểu rõ hơn mối liên hệ giữa kiến trúc AWS và ứng dụng sau khi triển khai thực tế.

### Khó khăn và cách xử lý:

* Khó khăn: Một số cấu hình triển khai cần được điều chỉnh sau lần chạy đầu tiên trên AWS.
* Cách xử lý: Rà soát từng bước cấu hình, kiểm tra các phụ thuộc giữa dịch vụ và sửa lại setup trước khi test tiếp.
* Khó khăn: Cần xác nhận hành vi ứng dụng một cách cẩn thận sau mỗi lần thay đổi.
* Cách xử lý: Kiểm thử lại luồng chính sau từng lần chỉnh sửa và so sánh kết quả với phiên bản trước đó.
