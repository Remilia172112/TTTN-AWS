---
title: "Worklog Tuần 6"
date: 2026-04-13
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Ôn tập và nắm vững các khái niệm cơ bản về Cơ sở dữ liệu (Database Concepts) khi đưa lên môi trường điện toán đám mây.
* Hiểu rõ kiến trúc, tính năng và ứng dụng thực tế của Amazon RDS, Amazon Aurora, Amazon Redshift và Amazon ElastiCache.
* Thực hành triển khai, kết nối và quản trị một hệ quản trị cơ sở dữ liệu quan hệ trên Amazon RDS.
* Nắm vững quy trình và thực hành công cụ để chuyển đổi lược đồ (Schema Conversion) và di dời cơ sở dữ liệu (Database Migration) lên AWS một cách an toàn.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Xem và ôn tập lại các khái niệm về Database (Relational, NoSQL, In-memory) <br> - Đọc tài liệu về Amazon RDS: Các DB Engine được hỗ trợ, cơ chế Multi-AZ và Read Replicas | 13/04/2026 | 13/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Nghiên cứu sâu về kiến trúc hiệu năng cao của Amazon Aurora <br> - Tìm hiểu giải pháp Data Warehouse với Amazon Redshift và In-memory caching với Amazon ElastiCache (Redis/Memcached) | 14/04/2026 | 14/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Thực hành Amazon RDS:** <br>&emsp; + Khởi tạo một RDS Database instance (MySQL hoặc PostgreSQL) trong Private Subnet <br>&emsp; + Thiết lập Security Group cho phép EC2 kết nối vào Database <br>&emsp; + Sử dụng DB Client (DBeaver, MySQL Workbench) hoặc CLI để kết nối và thao tác | 15/04/2026 | 15/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Đọc tài liệu và nghiên cứu về các công cụ di dời dữ liệu của AWS: <br>&emsp; + AWS Schema Conversion Tool (SCT) <br>&emsp; + AWS Database Migration Service (DMS) | 16/04/2026 | 16/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Thực hành Migration:** <br>&emsp; + Sử dụng AWS SCT để phân tích và chuyển đổi lược đồ từ CSDL nguồn sang CSDL đích <br>&emsp; + Cấu hình AWS DMS để tạo các Endpoint và Task nhằm di dời dữ liệu lên Amazon RDS | 17/04/2026 | 17/04/2026 | |

### Kết quả đạt được tuần 6:

* Phân biệt rõ ràng các loại dịch vụ cơ sở dữ liệu trên AWS và biết cách chọn đúng dịch vụ (RDS, Aurora, Redshift, ElastiCache) cho từng bài toán cụ thể.
* Khởi tạo, cấu hình và bảo mật thành công Amazon RDS instance, đảm bảo CSDL nằm ở phân vùng mạng kín nhưng vẫn có thể giao tiếp với Application server.
* Nắm được phương pháp đánh giá mức độ tương thích giữa các loại Database Engine khác nhau thông qua AWS SCT.
* Triển khai thành công một quy trình chuyển đổi lược đồ và di dời cơ sở dữ liệu hoàn chỉnh sử dụng AWS DMS mà không làm thất thoát dữ liệu.