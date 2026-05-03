---
title: "Worklog Tuần 3"
date: 2026-03-23
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Nghiên cứu chuyên sâu về các dịch vụ điện toán (Compute) và lưu trữ (Storage) nâng cao trên AWS.
* Nắm vững cơ chế hoạt động của Auto Scaling, quản lý image (AMI) và dịch vụ di chuyển máy chủ (MGN).
* Hoàn thành các bài lab thực hành triển khai mô hình kiến trúc VPC và EC2 nâng cao.
* Đa dạng hóa phương thức kết nối máy chủ ảo bằng các công cụ chuyên dụng như MobaXterm và PuTTY.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Xem và đọc các tài liệu về AWS EC2 nâng cao, Amazon Machine Image (AMI), và cách quản lý Key Pair <br> - Tìm hiểu về các loại lưu trữ block storage (EBS) | 23/03/2026 | 23/03/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Nghiên cứu về AWS Auto Scaling và AWS Lightsail <br> - Đọc tài liệu về các dịch vụ lưu trữ tệp tin (EFS/FSx) và dịch vụ Application Migration Service (MGN) | 24/03/2026 | 24/03/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Thực hành EC2 nâng cao:** <br>&emsp; + Tạo EC2 instance với các tùy chọn nâng cao (User data, IAM role) <br>&emsp; + Tạo Custom AMI từ instance đang chạy <br>&emsp; + Thực hành tạo, gắn (attach) và mở rộng EBS volume | 25/03/2026 | 25/03/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - **Thực hành Lab tổng hợp:** <br>&emsp; + Làm theo các bài lab có sẵn về mô hình kiến trúc kết hợp VPC và EC2 nâng cao <br>&emsp; + Kiểm tra luồng mạng và phân quyền truy cập | 26/03/2026 | 26/03/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Thực hành kết nối:** <br>&emsp; + Tải, cài đặt và cấu hình PuTTY (chuyển đổi định dạng file key từ .pem sang .ppk) <br>&emsp; + Sử dụng MobaXterm và PuTTY để kết nối SSH vào EC2 Linux | 27/03/2026 | 27/03/2026 | |

### Kết quả đạt được tuần 3:

* Hiểu sâu sắc và phân biệt được các dịch vụ lưu trữ của AWS (EBS cho block storage, EFS/FSx cho file storage).
* Nắm rõ cách thức hoạt động của Auto Scaling để tự động điều chỉnh tài nguyên, cũng như biết khi nào nên dùng Lightsail thay vì EC2 truyền thống.
* Nắm được khái niệm và ứng dụng của AWS MGN trong việc di chuyển máy chủ (migration) lên Cloud.
* Triển khai thành công các mô hình Lab phức tạp kết hợp giữa hạ tầng mạng (VPC) và máy chủ ảo (EC2).
* Quản lý thành thạo AMI và Key Pair.
* Thành thạo việc sử dụng các phần mềm Client thứ 3 (MobaXterm, PuTTY) để quản trị máy chủ EC2 Linux, bao gồm cả kỹ năng xử lý, chuyển đổi định dạng khóa bảo mật (PEM sang PPK).