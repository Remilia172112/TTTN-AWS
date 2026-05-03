---
title: "Workshop"
date: 2026-05-03
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Xây dựng Ứng dụng Web Serverless trên AWS

#### Tổng quan

**AWS Serverless Computing** cho phép bạn xây dựng và chạy các ứng dụng và dịch vụ mà không cần phải suy nghĩ về việc quản lý máy chủ. Ứng dụng của bạn vẫn chạy trên các máy chủ, nhưng tất cả việc quản lý máy chủ đều do AWS thực hiện.

Trong bài workshop này, chúng ta sẽ học cách xây dựng một ứng dụng web Serverless từ đầu đến cuối có tên là **Wild Rydes** (ứng dụng gọi xe kỳ lân). Ứng dụng này sẽ cho phép người dùng đăng ký tài khoản, đăng nhập, và yêu cầu một chuyến đi. 

Chúng ta sẽ sử dụng các dịch vụ cốt lõi của AWS để hoàn thiện từng thành phần của ứng dụng:
+ **Lưu trữ Web (Web Hosting)** - Sử dụng **AWS Amplify** để lưu trữ các tài nguyên web tĩnh (HTML, CSS, JavaScript) cho giao diện người dùng.
+ **Quản lý danh tính (User Management)** - Sử dụng **Amazon Cognito** để tạo một User Pool giúp quản lý việc đăng ký, xác thực và cấp quyền cho người dùng.
+ **Hệ thống Backend (Serverless Backend)** - Sử dụng **Amazon DynamoDB** để tạo bảng cơ sở dữ liệu lưu trữ các yêu cầu gọi xe và **AWS Lambda** để thực thi mã tính toán mỗi khi có yêu cầu mới.
+ **Cổng API (RESTful API)** - Sử dụng **Amazon API Gateway** để định tuyến các HTTP request từ giao diện web ở Frontend đến các hàm Lambda ở Backend một cách an toàn.


#### Nội dung

1. [Tổng quan về kiến trúc ứng dụng](5.1-Architecture-overview/)
2. [Lưu trữ trang web tĩnh](5.2-Static-web-hosting/)
3. [Quản lý người dùng](5.3-User-management/)
4. [Xây dựng Backend không máy chủ](5.4-Serverless-backend/)
5. [Triển khai API Backend](5.5-Restful-api/)
6. [Xây dựng Frontend](5.6-Build-Frontend/)
7. [Dọn dẹp tài nguyên](5.7-Cleanup/)