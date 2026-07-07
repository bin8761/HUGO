---
title: "AWS First Cloud Journey Community Day"
date: 2026-06-06
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Event 1 - AWS First Cloud Journey Community Day

| Thông tin | Nội dung |
| --- | --- |
| Thời gian | Ngày 06/06/2026 |
| Địa điểm | Tầng 26, Tòa nhà Bitexco Financial Tower |
| Vai trò | Người tham dự chương trình First Cloud Journey |
| Hình thức tham gia | Tham gia trực tiếp |
| Chủ đề chính | Cloud Computing, DevOps, Security, AI, WebSocket, Teamwork và định hướng nghề nghiệp trong lĩnh vực công nghệ thông tin |
| Danh sách diễn giả | Tran Trung Vinh - System Administrator tại Central Retail Group; Bảo Huỳnh - Junior Cloud Native Developer, Endava Vietnam; Lê Hoàng Gia Đại; Nguyễn Quốc Bảo; Trương Huy Phước; Việt Phát |

## 1. Lý do tham gia

AWS First Cloud Journey Community Day là một sự kiện có nhiều diễn giả đang làm việc thực tế với cloud, nên ngay từ đầu đã tạo cảm giác rất gần với công việc thật. Thay vì chỉ nói về khái niệm, chương trình đưa ra những ví dụ cụ thể về AWS, Docker, machine learning, WebSocket, GraphRAG và DevOps trong môi trường triển khai thực tế.

Tôi tham gia để nhìn rộng hơn so với kiến thức học trên lớp. Điều tôi muốn nghe là cách người trong ngành nói về triển khai cloud, bảo mật hệ thống, ứng dụng thời gian thực và hướng phát triển nghề nghiệp. Sự kiện cũng hữu ích vì cho thấy cách các chuyên gia phân tích vấn đề, trình bày giải pháp và chia sẻ kinh nghiệm làm việc trong doanh nghiệp.

## 2. Nội dung các phiên chia sẻ

Chương trình được chia thành nhiều phần, mỗi phần đi vào một khía cạnh khác nhau của hành trình học cloud. Gộp lại, các chủ đề này tạo thành một bức tranh khá đầy đủ về những gì người học AWS cần có, từ nền tảng triển khai, bảo mật cho đến làm việc nhóm và tư duy nghề nghiệp.

### 2.1. Docker như một lớp đóng gói ứng dụng

Phần Docker nói về containerization và vì sao đây là một phần quan trọng của quy trình phát triển phần mềm hiện đại. Diễn giả so sánh container với virtual machine và chỉ ra rằng container nhẹ hơn, dễ di chuyển hơn, đồng thời phù hợp với workflow cloud-native.

Điều tôi rút ra là Docker không chỉ dùng để chạy ứng dụng trong container. Nó còn giúp đóng gói code, thư viện, cấu hình và môi trường chạy vào cùng một đơn vị, nhờ đó giảm tình trạng “chạy trên máy mình thì đúng” nhưng sang môi trường khác lại lỗi. Đây là lý do Docker xuất hiện rất nhiều trong DevOps và quy trình triển khai.

Với AWS, kiến thức này rất cần vì các dịch vụ như Amazon ECS, Amazon EKS và các pipeline CI/CD đều gắn rất chặt với mô hình container. Hiểu Docker giúp tôi có nền tảng chắc hơn khi tiếp cận những dịch vụ đó sau này.

### 2.2. AWS WAF và NIDS dựa trên Machine Learning

Phiên về bảo mật tập trung vào việc bảo vệ ứng dụng web và phát hiện tấn công mạng. AWS WAF được giới thiệu như một lớp phòng thủ cho ứng dụng HTTP/HTTPS, có thể chặn các kiểu tấn công phổ biến như SQL Injection, Cross-site Scripting, bot traffic, brute force và các request bất thường.

Diễn giả cũng chỉ ra hạn chế của cách bảo mật chỉ dựa trên luật cố định. Rule truyền thống hiệu quả với kiểu tấn công đã biết, nhưng sẽ yếu hơn khi gặp kỹ thuật mới, zero-day hoặc hành vi bất thường chưa từng được mô tả trước đó. Từ đó, phần trình bày đưa ra hướng kết hợp AWS WAF với Machine Learning để xây dựng NIDS có khả năng học từ dữ liệu mạng và phát hiện tín hiệu bất thường.

Điểm tôi nhớ nhất là bảo mật cloud không phải chỉ là dựng firewall rồi dừng lại. Cách làm tốt hơn là ghép nhiều lớp bảo vệ cùng nhau, trong đó phát hiện dựa trên hành vi đang ngày càng quan trọng.

### 2.3. Từ IT Helpdesk đến Senior Sysadmin

Phiên chia sẻ về hành trình từ IT Helpdesk đến Senior Sysadmin rất thực tế. Diễn giả nói về việc bắt đầu từ hỗ trợ người dùng, rồi dần phát triển sang Linux, networking, hạ tầng hệ thống, làm lab cá nhân và tiến tới vai trò quản trị hệ thống.

Điểm đáng nhớ là tư duy vận hành. Làm hạ tầng không chỉ là biết kỹ thuật mà còn phải có thói quen xử lý sự cố bình tĩnh, ghi chép rõ ràng, theo dõi hệ thống đều đặn và tránh thử trực tiếp trên production khi chưa có phương án an toàn. Ngoài ra, việc chuyển từ on-premise sang cloud cũng kéo theo cách nghĩ mới về mở rộng linh hoạt, trả phí theo mức dùng, dịch vụ quản lý sẵn và Infrastructure as Code.

Phiên này giúp tôi nối rõ hơn mối quan hệ giữa Sysadmin, Cloud và DevOps. Đường đi vào cloud không chỉ là học tên dịch vụ, mà còn phải có nền tảng về hệ điều hành, mạng, bảo mật và tự động hóa.

### 2.4. Multiplayer trên cloud

Phiên Multiplayer in the Cloud cho thấy cách kết nối các client Godot qua AWS WebSocket. Diễn giả so sánh nhiều mô hình giao tiếp như UDP/ENet, WebSocket và HTTP Polling, rồi giải thích khi nào nên chọn từng cách.

Kiến trúc được trình bày dùng API Gateway WebSocket để giữ kết nối client, AWS Lambda để xử lý sự kiện, DynamoDB để lưu trạng thái kết nối và CloudWatch để ghi log, theo dõi hệ thống. Ví dụ này làm serverless trở nên cụ thể hơn vì nó cho thấy một hệ thống thời gian thực có thể vận hành mà không cần tự quản lý máy chủ theo cách truyền thống.

Phần này hữu ích vì nó nối backend, kiến trúc cloud và mô hình ứng dụng real-time lại với nhau. Tôi hiểu rõ hơn AWS có thể đứng ở đâu trong các bài toán như chat, lobby game, matchmaking hay những hệ thống cần trao đổi dữ liệu liên tục.

### 2.5. Teamwork trong công việc kỹ thuật

Phiên về teamwork tập trung vào những thói quen giúp việc cộng tác hiệu quả hơn. Diễn giả nhấn mạnh bốn yếu tố: mục tiêu chung rõ ràng, giao việc đúng người, giao tiếp cởi mở với sự lắng nghe chủ động và tinh thần trách nhiệm cá nhân.

Các công cụ như ClickUp, Trello, Slack, Google Workspace và Discord không phải là trọng tâm chính, nhưng chúng cho thấy cách một nhóm giữ công việc minh bạch, chia nhỏ nhiệm vụ, cập nhật tiến độ và lưu trữ thông tin mà không phụ thuộc vào trí nhớ.

Với tôi, phần này rất hợp với thực tế thực tập vì project công nghệ hiếm khi là việc của một người. Kết quả tốt thường đến từ việc cả nhóm giao tiếp rõ và mỗi người làm đúng phần mình.

### 2.6. GraphRAG với Bedrock và Neptune

Phiên cuối về GraphRAG giới thiệu một hướng mới trong AI, nơi Retrieval-Augmented Generation được kết hợp với cấu trúc đồ thị. RAG truyền thống giúp mô hình ngôn ngữ lấy thông tin từ nguồn ngoài để trả lời chắc hơn, còn GraphRAG hữu ích hơn khi câu hỏi cần suy luận qua nhiều thực thể và mối quan hệ giữa chúng.

Diễn giả mô tả cách xây dựng ứng dụng GraphRAG bằng Amazon Bedrock và Amazon Neptune. Bedrock đảm nhiệm phần mô hình AI sinh sinh, còn Neptune lưu trữ và xử lý dữ liệu đồ thị. Sự kết hợp này giúp hệ thống vừa tìm theo nội dung, vừa tìm theo quan hệ để suy luận tốt hơn.

Điều này cho tôi một góc nhìn rộng hơn về AWS trong AI. Cloud không chỉ cung cấp máy chủ, mạng hay lưu trữ, mà còn có thể hỗ trợ xây dựng các hệ thống thông minh phục vụ hỏi đáp, tìm kiếm tri thức và phân tích dữ liệu phức tạp.

## 3. Bài học rút ra

Sau sự kiện, tôi rút ra được cả bài học kỹ thuật lẫn bài học về nghề nghiệp. Về kỹ thuật, tôi hiểu rõ hơn vai trò của Docker trong triển khai ứng dụng, cách AWS hỗ trợ kiến trúc serverless, tầm quan trọng của bảo mật nhiều lớp và tiềm năng của AI trên nền tảng AWS. Các chủ đề như WebSocket, machine-learning-based NIDS và GraphRAG cho thấy hệ sinh thái AWS có thể đi vào nhiều hướng khác nhau, từ bảo mật, game, backend thời gian thực cho đến AI.

Về định hướng nghề nghiệp, phiên chia sẻ từ IT Helpdesk đến Senior Sysadmin nhắc tôi rằng con đường phát triển trong ngành công nghệ phải bắt đầu từ nền tảng chắc và sự học hỏi liên tục. Những kỹ năng như networking, Linux, troubleshooting, monitoring, automation và documentation đều rất quan trọng với người làm cloud hoặc DevOps.

Về kỹ năng mềm, phần teamwork cho tôi thấy làm việc nhóm hiệu quả cần có mục tiêu chung, phân công rõ ràng, giao tiếp thường xuyên và tinh thần trách nhiệm. Những điều này cần thiết không chỉ trong thực tập mà cả trong môi trường doanh nghiệp sau này.

## 4. Đóng góp cá nhân

Trong lúc tham gia sự kiện, tôi chủ động nghe và ghi chú lại các nội dung liên quan đến AWS, Docker, bảo mật, serverless và AI để đưa vào báo cáo thực tập. Tôi cũng đối chiếu những gì nghe được với kiến thức đã học trong chương trình AWS Study Group để củng cố nền tảng và xác định phần nào cần học sâu hơn.

Bên cạnh đó, tôi xem sự kiện như một dấu mốc để chỉnh lại kế hoạch học của mình. Sau buổi event, tôi thấy rõ rằng mình cần tiếp tục luyện Docker, tìm hiểu sâu hơn về dịch vụ serverless của AWS, tăng cường kiến thức bảo mật cloud và thực hành thêm các mô hình triển khai ứng dụng thực tế.

## 5. Kết luận

AWS First Cloud Journey Community Day mang lại cho tôi một bức tranh thực tế hơn về mối liên hệ giữa cloud, DevOps, bảo mật và AI. Sự kiện cũng cho thấy phát triển nghề nghiệp trong ngành công nghệ không chỉ dựa vào kiến thức kỹ thuật, mà còn cần sự bền bỉ, kỹ năng giao tiếp và khả năng học hỏi từ những người đang làm việc trong ngành.

## Hình ảnh sự kiện

Một số hình ảnh được ghi lại trong quá trình tham gia sự kiện:

![AWS First Cloud Journey Community Day](/HUGO/images/4-EventParticipated/4.1-Event1/z7976498940486_4005b6c6d8361abe3f1b76bdf4dd74ef.jpg)
