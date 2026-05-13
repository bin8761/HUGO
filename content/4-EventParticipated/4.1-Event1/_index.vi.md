---
title: "Sự kiện 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Báo cáo tóm tắt: “Hội thảo hiện đại hóa App-DB do GenAI cung cấp”

### Mục tiêu sự kiện

- Chia sẻ các phương pháp hay nhất trong thiết kế ứng dụng hiện đại
- Giới thiệu Thiết kế hướng miền (DDD) và kiến ​​trúc hướng sự kiện
- Cung cấp hướng dẫn về cách chọn dịch vụ điện toán phù hợp
- Trình bày các công cụ AI để hỗ trợ vòng đời phát triển

### Loa

- **Jignesh Shah** â€“ Giám đốc, Cơ sở dữ liệu nguồn mở
- **Erica Liu** â€“ Chuyên gia Sr. GTM, AppMod
- **Fabrianne Effendi** â€“ PGS. Chuyên gia SA, Dịch vụ web Amazon không có máy chủ

### Điểm nổi bật chính

#### Xác định những hạn chế của kiến ​​trúc ứng dụng cũ

- Chu kỳ phát hành sản phẩm dài †’ Mất doanh thu/bỏ lỡ cơ hội  
- Hoạt động kém hiệu quả †’ Năng suất giảm, chi phí cao hơn  
- Không tuân thủ các quy định về bảo mật †’ Vi phạm an ninh, mất uy tín  

#### Chuyển sang kiến ​​trúc ứng dụng hiện đại – Microservices

Di chuyển sang hệ thống mô-đun — mỗi chức năng là một **dịch vụ độc lập** giao tiếp qua **sự kiện**, được xây dựng trên ba trụ cột cốt lõi:

- **Quản lý hàng đợi**: Xử lý các tác vụ không đồng bộ  
- **Chiến lược bộ nhớ đệm**: Tối ưu hóa hiệu suất  
- **Xử lý tin nhắn**: Giao tiếp giữa các dịch vụ linh hoạt  

#### Thiết kế hướng tên miền (DDD)

- **Phương pháp bốn bước**: Xác định các sự kiện trong miền â†' sắp xếp dòng thời gian â†' xác định các tác nhân â†' xác định bối cảnh bị giới hạn  
- **Nghiên cứu điển hình về hiệu sách**: Trình bày ứng dụng DDD trong thế giới thực  
- **Ánh xạ ngữ cảnh**: 7 mẫu để tích hợp các ngữ cảnh bị giới hạn  

#### Kiến trúc hướng sự kiện

- **3 mẫu tích hợp**: Xuất bản/Đăng ký, Điểm-điểm, Truyền phát  
- **Lợi ích**: Khớp nối lỏng lẻo, khả năng mở rộng, khả năng phục hồi  
- **So sánh đồng bộ hóa và không đồng bộ**: Tìm hiểu sự cân bằng  

#### Tính toán tiến hóa

- **Mô hình chia sẻ trách nhiệm**: EC2 â†’ ECS â†’ Fargate â†’ Lambda  
- **Lợi ích không cần máy chủ**: Không cần quản lý máy chủ, tự động mở rộng quy mô, trả theo giá trị  
- **Chức năng và Vùng chứa**: Tiêu chí lựa chọn phù hợp  

#### Nhà phát triển Amazon Q

- **Tự động hóa SDLC**: Từ lập kế hoạch đến bảo trì  
- **Chuyển đổi mã**: Nâng cấp Java, hiện đại hóa .NET  
- **Tác nhân chuyển đổi AWS**: Di chuyển VMware, Mainframe, .NET  

### Bài học chính

#### Tư duy thiết kế

- **Phương pháp tiếp cận ưu tiên doanh nghiệp**: Luôn bắt đầu từ lĩnh vực kinh doanh, không phải công nghệ  
- **Ngôn ngữ phổ biến**: Tầm quan trọng của vốn từ vựng chung giữa các nhóm kinh doanh và công nghệ  
- **Bối cảnh bị giới hạn**: Xác định và quản lý độ phức tạp trong các hệ thống lớn  

#### Kiến trúc kỹ thuật

- **Kỹ thuật gây bão sự kiện**: Phương pháp thực tế để lập mô hình quy trình kinh doanh  
- Sử dụng **giao tiếp theo sự kiện** thay vì cuộc gọi đồng bộ  
- **Mẫu tích hợp**: Khi nào nên sử dụng đồng bộ hóa, không đồng bộ, pub/sub, phát trực tuyến  
- **Tính toán phổ**: Tiêu chí để lựa chọn giữa VM, container và serverless  

#### Chiến lược hiện đại hóa

- **Phương pháp tiếp cận theo từng giai đoạn**: Không vội vàng - tuân theo lộ trình rõ ràng  
- **Khung 7Rs**: Nhiều lộ trình hiện đại hóa tùy thuộc vào ứng dụng  
- **Đo lường ROI**: Giảm chi phí + tính linh hoạt trong kinh doanh  

### Nộp đơn xin việc

- **Áp dụng DDD** cho các dự án hiện tại: Các buổi sự kiện gây bão với đội ngũ kinh doanh  
- **Tái cấu trúc các vi dịch vụ**: Sử dụng ngữ cảnh giới hạn để xác định ranh giới dịch vụ  
- **Triển khai các mẫu hướng sự kiện**: Thay thế một số cuộc gọi đồng bộ hóa bằng tin nhắn không đồng bộ  
- **Áp dụng serverless**: Thí điểm AWS Lambda cho các trường hợp sử dụng phù hợp  
- **Dùng thử Amazon Q Developer**: Tích hợp vào quy trình làm việc của nhà phát triển để tăng năng suất  

### Trải nghiệm sự kiện

Việc tham dự hội thảo **“Hiện đại hóa App-DB do GenAI hỗ trợ”** là vô cùng quý giá, mang lại cho tôi cái nhìn toàn diện về việc hiện đại hóa ứng dụng và cơ sở dữ liệu bằng các phương pháp và công cụ tiên tiến. Những kinh nghiệm chính bao gồm:

#### Học từ những diễn giả có tay nghề cao
- Các chuyên gia từ AWS và các tổ chức công nghệ lớn đã chia sẻ **các biện pháp thực hành tốt nhất** trong thiết kế ứng dụng hiện đại.  
- Thông qua các nghiên cứu điển hình trong thế giới thực, tôi đã hiểu sâu hơn về việc áp dụng **DDD** và **Kiến trúc hướng sự kiện** cho các dự án lớn.  

#### Tiếp xúc kỹ thuật thực hành
- Việc tham gia vào các phiên **tập trung sự kiện** đã giúp tôi hình dung ra cách **mô hình hóa quy trình kinh doanh** thành các sự kiện trong miền.  
- Đã tìm hiểu cách **phân tách các vi dịch vụ** và xác định **ngữ cảnh bị giới hạn** để quản lý độ phức tạp của hệ thống lớn.  
- Hiểu được sự cân bằng giữa **giao tiếp đồng bộ và không đồng bộ** và các mô hình tích hợp như **pub/sub, point-to-point, streaming**.  

#### Tận dụng các công cụ hiện đại
- Đã khám phá **Amazon Q Developer**, một công cụ AI hỗ trợ SDLC từ khâu lập kế hoạch đến bảo trì.  
- Đã học cách **tự động chuyển đổi mã** và thí điểm serverless với **AWS Lambda** để cải thiện năng suất.  

#### Kết nối và thảo luận
- Hội thảo mang đến cơ hội trao đổi ý tưởng với các chuyên gia, đồng nghiệp và nhóm kinh doanh, nâng cao **ngôn ngữ phổ biến** giữa kinh doanh và công nghệ.  
- Các ví dụ thực tế đã củng cố tầm quan trọng của **cách tiếp cận ưu tiên doanh nghiệp** thay vì chỉ tập trung vào công nghệ.  

#### Bài học kinh nghiệm
- Việc áp dụng DDD và các mẫu theo hướng sự kiện giúp giảm **khớp nối** đồng thời cải thiện **khả năng mở rộng** và **khả năng phục hồi**.  
- Hiện đại hóa đòi hỏi **cách tiếp cận theo từng giai đoạn** với **đo lường ROI**; quá trình gấp rút có thể gặp rủi ro.  
- Các công cụ AI như Amazon Q Developer có thể **tăng năng suất** đáng kể khi được tích hợp vào quy trình làm việc hiện tại.  

#### Một số hình ảnh sự kiện
*Thêm ảnh sự kiện của bạn tại đây*  

> Nhìn chung, sự kiện không chỉ cung cấp kiến ​​thức kỹ thuật mà còn giúp tôi định hình lại tư duy về thiết kế ứng dụng, hiện đại hóa hệ thống và hợp tác giữa các nhóm.
