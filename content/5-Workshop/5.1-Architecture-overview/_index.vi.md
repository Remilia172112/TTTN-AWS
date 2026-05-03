---
title : "Tổng quan về kiến trúc"
date : 2026-05-03
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Tổng quan về ứng dụng Wild Rydes

Trong hướng dẫn này, bạn sẽ tạo một ứng dụng web phi máy chủ (serverless) đơn giản cho phép người dùng yêu cầu các chuyến đi bằng "kỳ lân" (thực chất là đặt xe grab,...) từ đội xe **Wild Rydes**. 

Ứng dụng cung cấp cho người dùng giao diện dựa trên HTML/JavaScript để chọn vị trí đón. Ở phía Backend, ứng dụng sẽ giao tiếp với một dịch vụ web RESTful để gửi yêu cầu và điều phối một con kỳ lân gần đó đến vị trí khách hàng. Ứng dụng cũng tích hợp đầy đủ tính năng đăng ký và đăng nhập trước khi người dùng có thể sử dụng dịch vụ.

#### Kiến trúc ứng dụng

Kiến trúc của ứng dụng này tận dụng tối đa các dịch vụ quản lý của AWS để loại bỏ việc vận hành máy chủ, bao gồm: **AWS Lambda**, **Amazon API Gateway**, **Amazon DynamoDB**, **Amazon Cognito** và **AWS Amplify**.

![Architecture Diagram](/images/5-Workshop/5.1-Architecture-overview/diagram1.png)

#### Các thành phần cốt lõi

+ **Lưu trữ web tĩnh (Static Web Hosting):** **AWS Amplify** cung cấp tính năng triển khai liên tục (CI/CD) và lưu trữ các tài nguyên tĩnh như HTML, CSS, JavaScript và hình ảnh. Trình duyệt của người dùng sẽ tải các tài nguyên này để hiển thị giao diện.
+ **Quản lý người dùng (User Management):** **Amazon Cognito** cung cấp các chức năng xác thực, đăng ký và quản lý người dùng để bảo mật cho API backend. Chỉ những người dùng đã đăng nhập mới có quyền gọi xe.
+ **Backend phi máy chủ (Serverless Backend):** **AWS Lambda** xử lý logic nghiệp vụ và **Amazon DynamoDB** đóng vai trò là lớp lưu trữ dữ liệu bền vững, nơi các yêu cầu chuyến đi được ghi lại.
+ **API RESTful:** JavaScript chạy trong trình duyệt giao tiếp với Backend thông qua **Amazon API Gateway**. Đây là cửa ngõ tiếp nhận các HTTP request và kích hoạt hàm Lambda tương ứng.

#### Thông tin Workshop

| Đặc điểm | Chi tiết |
| :--- | :--- |
| **Trải nghiệm AWS** | Mới bắt đầu (Beginner) |
| **Thời gian hoàn thành** | Khoảng 2 giờ |
| **Chi phí ước tính** | Miễn phí (Nếu nằm trong AWS Free Tier) hoặc dưới 0.25 USD |
| **Trình duyệt đề xuất** | Google Chrome (phiên bản mới nhất) |

#### Các mô-đun thực hiện

Hội thảo này được chia làm 5 mô-đun chính. Mỗi mô-đun sẽ hướng dẫn bạn từng bước triển khai và xác minh từng thành phần của kiến trúc:

1. **Lưu trữ trang web tĩnh (15 phút):** Cấu hình AWS Amplify để lưu trữ giao diện web với tính năng triển khai liên tục.
2. **Quản lý người dùng (30 phút):** Tạo Amazon Cognito User Pool để quản lý tài khoản khách hàng.
3. **Xây dựng backend phi máy chủ (30 phút):** Xây dựng hàm Lambda và bảng DynamoDB để xử lý yêu cầu gọi xe.
4. **Triển khai API RESTful (15 phút):** Sử dụng API Gateway để công khai hàm Lambda dưới dạng một API RESTful.
5. **Dọn dẹp tài nguyên (10 phút):** Xóa các tài nguyên đã tạo để tránh phát sinh chi phí không mong muốn.

---
**Lưu ý:** Nếu tài khoản AWS của bạn mới được tạo trong vòng 24 giờ qua, bạn có thể cần chờ một thời gian để hệ thống kích hoạt đầy đủ quyền truy cập vào các dịch vụ cần thiết cho bài lab này.