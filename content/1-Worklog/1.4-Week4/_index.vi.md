---
title: "Worklog Tuần 4"
date: 2026-03-23
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Nắm vững kiến thức toàn diện về dịch vụ lưu trữ đối tượng (Object Storage) cốt lõi của AWS, đặc biệt là Amazon S3.
* Hiểu rõ các phương thức kiểm soát quyền truy cập, tối ưu hóa hiệu suất và quản lý vòng đời dữ liệu (S3 Glacier).
* Tìm hiểu các giải pháp sao lưu (AWS Backup), lưu trữ lai (Storage Gateway) và vận chuyển dữ liệu quy mô lớn (Snow Family).
* Thực hành tích hợp các dịch vụ (EC2, S3, Lambda, SNS) để xây dựng một quy trình sao lưu và cảnh báo hoàn toàn tự động.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc                                                                                                                                                                                                            | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Xem và đọc các tài liệu về Amazon S3 (Buckets, Objects) <br> - Tìm hiểu S3 Access Point, cách cấu hình lưu trữ trang web tĩnh (Static Website) và xử lý lỗi CORS (Cross-Origin Resource Sharing)                   | 23/03/2026   | 23/03/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Nghiên cứu về Control Access trong S3 (IAM Policies, Bucket Policies, ACLs) <br> - Đọc tài liệu về cách đặt tên Object Key để tối ưu Performance <br> - Tìm hiểu các lớp lưu trữ lạnh (S3 Glacier, Glacier Deep) | 24/03/2026   | 24/03/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu các giải pháp di chuyển dữ liệu vật lý: AWS Snow Family (Snowcone, Snowball, Snowmobile) <br> - Đọc tài liệu về AWS Storage Gateway (lưu trữ lai) và kiến trúc AWS Backup tổng thể                        | 25/03/2026   | 25/03/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Thực hành khởi tạo dịch vụ:** <br>&emsp; + Tạo EC2 instance và S3 bucket <br>&emsp; + Thiết lập IAM Role cho phép EC2 có quyền đọc/ghi dữ liệu lên S3 <br>&emsp; + Tạo Topic và Subscriptions trên Amazon SNS    | 26/03/2026   | 26/03/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành tự động hóa (Serverless Backup):** <br>&emsp; + Viết hàm AWS Lambda bằng Python/Node.js để tự động hóa việc sao lưu dữ liệu (từ EC2 lên S3 hoặc tạo EBS Snapshot) <br>&emsp; + Tích hợp Lambda với SNS | 27/03/2026   | 27/03/2026      |                                           |

### Kết quả đạt được tuần 4:

* Hiểu sâu sắc về kiến trúc lưu trữ của Amazon S3, biết cách thiết lập S3 thành một web server tĩnh để host các trang web frontend.
* Nắm được chiến lược phân quyền bảo mật chặt chẽ trên S3 và cách thiết kế tiền tố (prefix) của Object Key để đạt hiệu suất I/O cao nhất.
* Phân biệt được các use case thực tế: Khi nào nên dùng Storage Gateway (kết nối on-premise với cloud) và khi nào dùng Snow Family (chuyển petabyte dữ liệu vật lý).
* Cấu hình thành công luồng thông báo qua email/SMS sử dụng Amazon SNS.
* Xây dựng thành công một kiến trúc Serverless thực tế: Sử dụng AWS Lambda để tự động kích hoạt tiến trình backup và gửi thông báo trạng thái (thành công/thất bại) qua SNS.