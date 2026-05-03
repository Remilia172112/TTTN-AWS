---
title: "Worklog Tuần 5"
date: 2026-04-06
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Nắm vững các khái niệm cốt lõi về bảo mật trên AWS, bao gồm Share Responsibility Model và quản lý danh tính, quyền truy cập (IAM).
* Hiểu rõ cách thức hoạt động và cấu hình các dịch vụ bảo mật nâng cao như Amazon Cognito, AWS Organization, AWS Identity Center, AWS KMS, và AWS Security Hub.
* Thực hành triển khai các biện pháp kiểm soát truy cập chi tiết sử dụng Resource Tags và Permission Boundaries.
* Ứng dụng AWS Lambda để xây dựng giải pháp tối ưu hóa chi phí tự động cho hệ thống AWS.
* Thực hành mã hóa dữ liệu ở trạng thái lưu trữ (Data at rest) sử dụng AWS KMS.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Xem và đọc các tài liệu về Share Responsibility Model <br> - Nghiên cứu sâu về Identity and Access Management (IAM), bao gồm Users, Groups, Roles, và Policies <br> - Tìm hiểu Amazon Cognito cho việc xác thực người dùng ứng dụng | 06/04/2026 | 06/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Đọc tài liệu về AWS Organization và AWS Identity Center để quản lý đa tài khoản và Single Sign-On (SSO) <br> - Tìm hiểu Amazon Key Management Service (KMS) về cách tạo và quản lý khóa mã hóa <br> - Nghiên cứu AWS Security Hub | 07/04/2026 | 07/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Thực hành Quản lý truy cập & Tối ưu chi phí:** <br>&emsp; + Quản lý truy cập vào dịch vụ EC2 thông qua Resource Tag kết hợp với AWS IAM policies <br>&emsp; + Sử dụng Lambda function để tự động hóa việc tối ưu hóa chi phí (ví dụ: tắt/mở EC2 ngoài giờ làm việc) | 08/04/2026 | 08/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - **Thực hành Kiểm soát quyền hạn & Mã hóa:** <br>&emsp; + Giới hạn quyền của user bằng IAM Permission Boundary <br>&emsp; + Thực hành mã hóa dữ liệu ở trạng thái lưu trữ (ví dụ: EBS, S3) sử dụng khóa quản lý bởi AWS KMS | 09/04/2026 | 09/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Thực hành Giám sát bảo mật:** <br>&emsp; + Kích hoạt và cấu hình AWS Security Hub để theo dõi các tiêu chuẩn bảo mật <br> - Tổng hợp kiến thức (Hands-on and Additional research) | 10/04/2026 | 10/04/2026 | |

### Kết quả đạt được tuần 5:

* Hiểu rõ trách nhiệm bảo mật giữa khách hàng và AWS theo Share Responsibility Model.
* Thiết lập thành công các chính sách IAM phức tạp, sử dụng Resource Tags để kiểm soát truy cập mức độ chi tiết (fine-grained access control) vào tài nguyên EC2.
* Nắm được cách giới hạn quyền hạn tối đa của một IAM role/user bằng Permission Boundaries.
* Tự động hóa được quy trình tiết kiệm chi phí thông qua việc lập trình các hàm AWS Lambda để quản lý trạng thái tài nguyên.
* Triển khai thành công mã hóa dữ liệu ở trạng thái lưu trữ (data at rest) với AWS KMS, đảm bảo an toàn thông tin theo chuẩn bảo mật.
* Có khả năng triển khai AWS Security Hub để đánh giá và liên tục theo dõi tình trạng bảo mật của toàn bộ môi trường AWS.