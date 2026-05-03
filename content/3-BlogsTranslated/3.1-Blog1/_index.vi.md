---
title: "Blog 1"
date: 2026-04-03
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Xây dựng ứng dụng hướng sự kiện (Event-Driven) với Amazon EventBridge

Kiến trúc hướng sự kiện (Event-Driven Architecture - EDA) đang nhanh chóng trở thành tiêu chuẩn để xây dựng các ứng dụng microservices phân tán và có khả năng mở rộng cao trên đám mây. Thay vì các dịch vụ gọi nhau trực tiếp (synchronous), chúng giao tiếp bằng cách phát ra và phản hồi các "sự kiện" (trạng thái thay đổi). Điều này giúp các thành phần tách rời (decoupled) và hệ thống trở nên linh hoạt hơn.

Bài đăng trên blog này sẽ đi sâu vào cách sử dụng **Amazon EventBridge** – một bus sự kiện không máy chủ (serverless event bus) giúp bạn dễ dàng kết nối các ứng dụng với nhau bằng cách sử dụng dữ liệu từ các ứng dụng của riêng bạn, phần mềm dạng dịch vụ (SaaS) tích hợp sẵn, và các dịch vụ AWS.

---

## Tại sao nên chọn Kiến trúc hướng sự kiện?

Việc chuyển đổi từ kiến trúc nguyên khối (monolith) hoặc microservices kết nối chặt chẽ sang mô hình hướng sự kiện mang lại nhiều lợi ích:
- **Tách rời các dịch vụ (Decoupling):** Các dịch vụ phát ra sự kiện (Producers) không cần biết dịch vụ nào đang tiêu thụ sự kiện đó (Consumers).
- **Mở rộng độc lập:** Bạn có thể dễ dàng thêm các consumer mới để xử lý một sự kiện mà không cần sửa đổi producer.
- **Tăng cường khả năng phục hồi (Resilience):** Nếu một consumer gặp sự cố, sự kiện vẫn nằm trên bus hoặc hàng đợi (queue) và có thể được xử lý lại sau khi hệ thống phục hồi.

---

## Các thành phần cốt lõi của EventBridge

Giải pháp kiến trúc sự kiện với EventBridge bao gồm ba khái niệm chính mà bạn cần nắm vững:

> *Hình 1. Kiến trúc tổng thể; Sự kiện đi từ Nguồn (Source) qua Bus và đến Đích (Target).*

1. **Event Buses:** Là một đường ống nhận các sự kiện. AWS tài khoản của bạn có sẵn một *default event bus* nhận các sự kiện từ các dịch vụ AWS. Bạn cũng có thể tạo *custom event buses* cho các ứng dụng nội bộ.
2. **Rules (Quy tắc):** Các quy tắc định tuyến sự kiện đến một đích (target) dựa trên mẫu sự kiện (event pattern) hoặc theo lịch trình (schedule).
3. **Targets (Đích):** Nơi EventBridge gửi sự kiện đến sau khi khớp với quy tắc. Các đích phổ biến bao gồm AWS Lambda, Amazon SNS, Amazon SQS, hoặc AWS Step Functions.

---

## So sánh các dịch vụ Message/Event trên AWS

Khi thiết kế hệ thống, việc chọn đúng dịch vụ là rất quan trọng:

| Dịch vụ AWS | Mô hình giao tiếp | Phù hợp nhất cho |
| :--- | :--- | :--- |
| **Amazon SQS** | Point-to-point (Hàng đợi) | Tách rời các tác vụ xử lý nặng, đảm bảo message không bị mất (Buffered). |
| **Amazon SNS** | Pub/Sub (Phát tán) | Gửi cùng một message đến nhiều subcribers với độ trễ siêu thấp (Fanout). |
| **Amazon EventBridge** | Event Bus (Định tuyến thông minh) | Lọc nội dung sự kiện phức tạp, kết nối ứng dụng SaaS bên thứ 3, định tuyến đa dịch vụ. |

---

## Ví dụ: Lọc sự kiện với EventBridge Rule

Một trong những sức mạnh lớn nhất của EventBridge là khả năng lọc tải trọng (payload) của sự kiện trước khi gọi Target. 

Ví dụ, bạn chỉ muốn kích hoạt hàm AWS Lambda khi có một đơn hàng (Order) được tạo thành công với giá trị lớn hơn 100$:
```json
{
  "source": ["com.mycompany.orders"],
  "detail-type": ["OrderCreated"],
  "detail": {
    "status": ["SUCCESS"],
    "amount": [{ "numeric": [ ">", 100 ] }]
  }
}