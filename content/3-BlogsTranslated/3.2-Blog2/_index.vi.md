---
title: "Blog 2"
date: 2026-04-30
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Thực hành tốt nhất về bảo mật AWS: Áp dụng nguyên tắc Đặc quyền tối thiểu (Least Privilege)

Bảo mật luôn là ưu tiên "Zero-day" tại AWS. Khi bạn bắt đầu xây dựng ứng dụng trên AWS, một trong những quyết định thiết kế quan trọng nhất là cách bạn quản lý danh tính và quyền truy cập thông qua **AWS Identity and Access Management (IAM)**. 

Trong bài blog này, tôi sẽ chia sẻ cách các đội ngũ kỹ thuật đám mây hiện đại thiết kế các chính sách IAM để tuân thủ nguyên tắc **Đặc quyền tối thiểu (Least Privilege)** – nghĩa là chỉ cấp đúng những quyền cần thiết để thực hiện một tác vụ, không dư không thiếu, nhằm giảm thiểu rủi ro bảo mật.

---

## Vấn đề với các chính sách IAM quá lỏng lẻo

Rất nhiều kỹ sư khi mới tiếp cận AWS thường có xu hướng sử dụng quyền `AdministratorAccess` hoặc dùng dấu hoa thị `*` (Wildcard) trong các chính sách IAM để tránh các lỗi `AccessDenied` cản trở tiến độ lập trình. 

> *Việc cấp quyền `s3:*` cho một môi trường ứng dụng có thể giúp ứng dụng chạy ngay lập tức, nhưng nó cũng đồng nghĩa với việc ứng dụng đó có quyền xóa toàn bộ bucket (s3:DeleteBucket) – một rủi ro thảm họa tiềm ẩn.*

---

## 3 Cấp độ kiểm soát truy cập trên AWS

Để đạt được môi trường bảo mật chặt chẽ, bạn cần kết hợp nhiều lớp bảo vệ khác nhau:

| Lớp bảo vệ | Trách nhiệm kiểm soát | Công cụ AWS sử dụng |
| :--- | :--- | :--- |
| **Cấp độ Tổ chức (Organization)** | Thiết lập ranh giới bảo mật tối đa cho toàn bộ các tài khoản con (Account). | Service Control Policies (SCPs) |
| **Cấp độ Ranh giới (Boundary)** | Ngăn chặn việc một Admin leo thang đặc quyền (Privilege Escalation). | IAM Permissions Boundaries |
| **Cấp độ Thực thi (Execution)** | Cấp quyền cụ thể cho một User hoặc một Dịch vụ AWS (như Lambda, EC2). | IAM Identity-based Policies |

---

## Cách xây dựng Chính sách Đặc quyền tối thiểu

Để viết các policy chặt chẽ, bạn nên sử dụng **IAM Access Analyzer**. Công cụ này theo dõi các dịch vụ mà Role của bạn thực sự gọi trong quá trình hoạt động, và tự động tạo ra một tệp JSON thu gọn chỉ chứa các quyền đã dùng.

### Ví dụ về chính sách hạn chế

Thay vì cấp quyền ghi lên toàn bộ S3 bucket, bạn nên giới hạn hành động chỉ được phép thực hiện trên một bucket cụ thể, và thậm chí là một thư mục cụ thể bên trong bucket đó:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:PutObject",
        "s3:GetObject"
      ],
      "Resource": "arn:aws:s3:::my-company-data-lake/processed-data/*"
    }
  ]
}