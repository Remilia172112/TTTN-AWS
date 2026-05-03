---
title: "Worklog Tuần 8"
date: 2026-04-27
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

* Hoàn thiện kiến trúc và triển khai dự án "Xây dựng Ứng dụng Web Serverless trên AWS".
* Tích hợp thành công khả năng Generative AI vào ứng dụng thực tế.
* Kiểm thử toàn diện và đóng gói tài liệu hướng dẫn triển khai.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Thiết lập môi trường Frontend với AWS Amplify <br> - Kết nối kho lưu trữ GitHub và cấu hình CI/CD tự động                                                                                 | 27/04/2026   | 27/04/2026      | [AWS Workshop](https://docs.aws.amazon.com) |
| 3   | - Cấu hình xác thực người dùng qua Amazon Cognito <br> - Thiết lập quyền truy cập Model (Model Access) cho Claude 3 Sonnet trên Amazon Bedrock                                              | 28/04/2026   | 28/04/2026      | [AWS Workshop](https://docs.aws.amazon.com) |
| 4   | - Xây dựng Serverless Backend với AWS Lambda <br> - Thiết kế bảng dữ liệu Amazon DynamoDB để lưu trữ thông tin <br> - Triển khai GraphQL API qua AWS AppSync                               | 29/04/2026   | 29/04/2026      | [AWS Workshop](https://docs.aws.amazon.com) |
| 5   | - Tích hợp Generative AI: Viết mã xử lý cho Lambda để gọi Amazon Bedrock <br> - Xử lý dữ liệu đầu vào và định dạng phản hồi từ mô hình ngôn ngữ lớn (LLM)                                   | 30/04/2026   | 30/04/2026      | [AWS Workshop](https://docs.aws.amazon.com) |
| 6   | - **Kiểm thử & Tối ưu:** <br>&emsp; + Kiểm tra luồng dữ liệu từ UI đến AI Backend <br>&emsp; + Tối ưu hóa hiệu năng và chi phí <br>&emsp; + Dọn dẹp tài nguyên thừa sau khi hoàn tất dự án | 01/05/2026   | 01/05/2026      | [AWS Workshop](https://docs.aws.amazon.com) |


### Kết quả đạt được tuần 8:

* Triển khai thành công ứng dụng Web hoàn chỉnh theo mô hình Serverless.
* Làm chủ quy trình CI/CD trên AWS Amplify để tự động hóa việc cập nhật mã nguồn từ GitHub.
* Tích hợp thành công Amazon Bedrock để tạo ra các nội dung thông minh (công thức nấu ăn) từ dữ liệu người dùng nhập vào.
* Hiểu rõ cách phối hợp giữa các dịch vụ AppSync (GraphQL), Lambda và DynamoDB trong một hệ thống thực tế.
* Đảm bảo tính bảo mật cho ứng dụng thông qua việc phân quyền IAM Least Privilege cho các hàm Lambda truy cập Bedrock.