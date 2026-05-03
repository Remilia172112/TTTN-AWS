---
title: "Worklog Tuần 2"
date: 2026-03-16
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* Nắm vững kiến thức nền tảng về hệ thống mạng và bảo mật trên AWS (VPC, VPN, Security Group, NACL).
* Tự tay triển khai và cấu hình thành công một hệ thống mạng Custom VPC hoàn chỉnh (bao gồm Public/Private Subnet, Route Table, IGW, NAT Gateway).
* Cài đặt và thực hiện kết nối SSH vào máy chủ ảo EC2 Linux thông qua môi trường VS Code.
* Thống nhất và chốt đề tài dự án thực hành (Project) với các thành viên trong nhóm.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Xem và đọc các tài liệu sẵn có về dịch vụ mạng cơ bản trên AWS <br> - Tìm hiểu lý thuyết về Virtual Private Cloud (VPC), Subnet (Public & Private) và Route Table | 16/03/2026 | 16/03/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Nghiên cứu sâu hơn về kết nối mạng và bảo mật <br> - Đọc tài liệu về Internet Gateway (IGW), NAT Gateway, VPN <br> - Tìm hiểu các lớp bảo mật mạng: Security Group (SG) và Network Access Control List (NACL) | 17/03/2026 | 17/03/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Thực hành thiết kế mạng:** <br>&emsp; + Tạo Custom VPC <br>&emsp; + Khởi tạo các Public Subnet và Private Subnet <br>&emsp; + Thiết lập Internet Gateway và NAT Gateway <br>&emsp; + Cấu hình Route Table để định tuyến luồng mạng | 18/03/2026 | 18/03/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - **Thực hành bảo mật và EC2:** <br>&emsp; + Tạo và cấu hình Security Group, NACL cho các luồng Inbound/Outbound <br>&emsp; + Khởi tạo EC2 instance (Linux) và đặt vào các Subnet tương ứng <br> - Setup môi trường Visual Studio Code trên máy cá nhân để chuẩn bị kết nối | 19/03/2026 | 19/03/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Thực hành kết nối:** Cấu hình file SSH config và tiến hành remote SSH vào EC2 Linux trực tiếp trên VS Code <br> - Tổ chức họp nhóm: Thảo luận, đánh giá tính khả thi và chốt đề tài Project cuối khóa | 20/03/2026 | 20/03/2026 | |

### Kết quả đạt được tuần 2:

* Hiểu rõ kiến trúc mạng trên AWS, phân biệt được sự khác nhau giữa các thành phần cốt lõi:
  * VPC (Mạng riêng ảo)
  * Public Subnet (Có truy cập internet) & Private Subnet (Kín, tính bảo mật cao)
  * Security Group (Bảo mật ở cấp độ Instance) & NACL (Bảo mật ở cấp độ Subnet)
  * NAT Gateway & Internet Gateway
* Tự tay thiết kế và cấu hình thành công một hệ thống mạng hoàn chỉnh, đảm bảo các máy ảo trong Private Subnet có thể ra internet tải gói tin (qua NAT Gateway) nhưng bên ngoài không thể truy cập ngược vào.
* Khởi tạo thành công các máy chủ ảo EC2 chạy hệ điều hành Linux trong đúng phân vùng mạng đã thiết kế.
* Cấu hình thành công kết nối SSH từ xa bằng phần mềm Visual Studio Code, giúp thao tác lập trình và quản trị server trực quan, tiện lợi hơn việc dùng terminal thuần.
* Nhóm đã thảo luận sôi nổi và thống nhất được định hướng cũng như đề tài cụ thể cho dự án thực hành.