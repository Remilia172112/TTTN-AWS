---
title: "Worklog Tuần 7"
date: 2026-04-20
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Hiểu rõ khái niệm và kiến trúc của Data Lake, phân biệt được Data Lake và Data Warehouse.
* Nắm vững cơ sở dữ liệu NoSQL hiệu suất cao với Amazon DynamoDB.
* Tìm hiểu và thực hành hệ sinh thái Analytics trên AWS (AWS Glue, Amazon Athena).
* Tích hợp các luồng dữ liệu để thực hiện phân tích và trực quan hóa (Data Visualization) thông qua Amazon QuickSight.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Đọc tài liệu về Data Lake Architecture trên AWS (S3, Lake Formation) <br> - Tìm hiểu các khái niệm cốt lõi của Cơ sở dữ liệu NoSQL và Amazon DynamoDB (Partition key, Sort key, RCU, WCU) | 20/04/2026 | 20/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Nghiên cứu hệ sinh thái Analytics trên AWS: <br>&emsp; + AWS Glue (ETL services, Data Catalog, Crawlers) <br>&emsp; + Amazon Athena (Truy vấn SQL trực tiếp trên S3) <br> - Đọc tài liệu về Amazon QuickSight | 21/04/2026 | 21/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Thực hành DynamoDB & Data Lake:** <br>&emsp; + Tạo bảng DynamoDB, thực hiện các lệnh thêm/sửa/xóa và Query/Scan dữ liệu <br>&emsp; + Khởi tạo S3 Bucket làm nền tảng lưu trữ cho Data Lake và upload dữ liệu mẫu (CSV/JSON) | 22/04/2026 | 22/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - **Thực hành AWS Analytics:** <br>&emsp; + Cấu hình AWS Glue Crawler để quét dữ liệu từ S3 Data Lake và tạo Data Catalog <br>&emsp; + Sử dụng Amazon Athena để viết các câu lệnh SQL truy vấn và phân tích dữ liệu trực tiếp từ S3 | 23/04/2026 | 23/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Thực hành Data Visualization:** <br>&emsp; + Đăng ký và thiết lập tài khoản Amazon QuickSight <br>&emsp; + Kết nối QuickSight với nguồn dữ liệu (S3/Athena) <br>&emsp; + Thực hiện phân tích và xây dựng Dashboard biểu diễn dữ liệu trực quan | 24/04/2026 | 24/04/2026 | |

### Kết quả đạt được tuần 7:

* Hiểu sâu sắc về kiến trúc Data Lake trên AWS và vai trò của S3 như một trung tâm lưu trữ dữ liệu không cấu trúc/bán cấu trúc.
* Thao tác thành thạo với Amazon DynamoDB, hiểu cách thiết kế khóa (Keys) để tối ưu hóa hiệu suất truy vấn cho CSDL NoSQL.
* Thiết lập thành công một quy trình phân tích dữ liệu (Data Pipeline) cơ bản: Dùng AWS Glue để thu thập schema và Amazon Athena để truy vấn dữ liệu mà không cần phải tải dữ liệu vào database truyền thống.
* Trực quan hóa thành công các bộ dữ liệu thô thành các biểu đồ (Dashboards) sinh động, dễ hiểu, phục vụ cho việc ra quyết định kinh doanh bằng Amazon QuickSight.