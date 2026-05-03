---
title: "Các bài blogs đã dịch"
date: 2026-05-03
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

###  [Blog 1 - Xây dựng ứng dụng hướng sự kiện (Event-Driven) với Amazon EventBridge](3.1-Blog1/)
Blog này giới thiệu về Kiến trúc hướng sự kiện (Event-Driven Architecture - EDA) và cách áp dụng nó để xây dựng các ứng dụng microservices phân tán trên nền tảng AWS. Bài viết giải thích chi tiết lợi ích của việc tách rời các dịch vụ (decoupling) để tăng khả năng mở rộng và phục hồi. Bạn cũng sẽ tìm hiểu sâu về các thành phần cốt lõi của Amazon EventBridge, cách phân biệt nó với Amazon SQS/SNS, và xem xét một ví dụ thực tế về việc lọc sự kiện (event filtering) để tối ưu hóa chi phí gọi hàm Lambda.

###  [Blog 2 - Thực hành tốt nhất về bảo mật AWS: Áp dụng nguyên tắc Đặc quyền tối thiểu](3.2-Blog2/)
Blog này đi sâu vào cách quản lý danh tính và quyền truy cập an toàn trên AWS thông qua dịch vụ IAM. Bài viết phân tích những rủi ro của việc cấp quyền quá lỏng lẻo (như sử dụng wildcard `*`) trong quá trình phát triển và hướng dẫn thiết lập 3 cấp độ kiểm soát truy cập toàn diện. Ngoài ra, bạn sẽ học cách sử dụng IAM Access Analyzer để thu gọn quyền hạn, cách viết các chính sách đặc quyền tối thiểu (Least Privilege), và ứng dụng phương pháp kiểm soát truy cập dựa trên thuộc tính (ABAC) thông qua Tags.