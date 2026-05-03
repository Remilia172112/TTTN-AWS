---
title : "Quản lý người dùng"
date : 2025-05-03
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

## Tổng quan

Sau khi đã có ứng dụng web React, bạn sẽ cấu hình tài nguyên xác thực (authentication) cho ứng dụng bằng AWS Amplify Auth, được xây dựng trên Amazon Cognito. Cognito là dịch vụ quản lý người dùng mạnh mẽ, hỗ trợ đăng ký, đăng nhập, khôi phục tài khoản và nhiều tính năng khác.

Bạn cũng sẽ sử dụng AWS Management Console để bật quyền truy cập Amazon Bedrock và mô hình Claude 3 Sonnet, giúp ứng dụng có thể tạo công thức nấu ăn bằng AI.

---

## Mục tiêu

Trong hướng dẫn này, bạn sẽ:

- Cấu hình Amplify Authentication  
- Thiết lập quyền truy cập Claude 3 Sonnet từ Anthropic  

---

## Triển khai

### Bước 1: Cấu hình Amplify Auth

Ứng dụng sử dụng email làm phương thức đăng nhập mặc định. Khi người dùng đăng ký, họ sẽ nhận được email xác thực. Trong bước này, bạn sẽ tùy chỉnh nội dung email xác thực.

#### Chỉnh sửa file resource

Trên máy local, truy cập: ai-recipe-generator/amplify/auth/resource.ts và cập nhật nội dung file theo yêu cầu và lưu lại.
```
import { defineAuth } from "@aws-amplify/backend";

export const auth = defineAuth({
  loginWith: {
    email: {
      verificationEmailStyle: "CODE",
      verificationEmailSubject: "Welcome to the AI-Powered Recipe Generator!",
      verificationEmailBody: (createCode) =>
        `Use this code to confirm your account: ${createCode()}`,
    },
  },
});
```

![img 1](/images/5-Workshop/5.3-User-management/img1.png)

#### Xem email đã tùy chỉnh

Hình dưới là ví dụ email xác thực sau khi tùy chỉnh:

![img 2](/images/5-Workshop/5.3-User-management/img2.png)

---

### Bước 2: Thiết lập quyền truy cập Amazon Bedrock

Amazon Bedrock cho phép bạn yêu cầu quyền truy cập tới nhiều mô hình AI tạo sinh. Trong bài này, bạn sẽ cần quyền truy cập Claude 3 Sonnet của Anthropic.

#### Mở Bedrock Console

Đăng nhập AWS Console và truy cập:

https://console.aws.amazon.com/bedrock/

- Đảm bảo đang ở region **N. Virginia (us-east-1)**  
- Chọn **Get started**

![img 3](/images/5-Workshop/5.3-User-management/img3.png)

#### Chọn model Claude

Trong phần **Foundation models**, chọn Claude.

![img 4](/images/5-Workshop/5.3-User-management/img4.png)

#### Yêu cầu quyền truy cập Claude 3 Sonnet

- Cuộn xuống phần Claude models  
- Chọn tab **Claude 3 Sonnet**  
- Nhấn **Request model access**

> Nếu đã có quyền, nút sẽ là **Manage model access**

![img 5](/images/5-Workshop/5.3-User-management/img5.png)

#### Yêu cầu quyền truy cập

Trong mục **Base models**:

- Chọn **Available to request** cho Claude 3 Sonnet  
- Nhấn **Request model access**

![img 6](/images/5-Workshop/5.3-User-management/img6.png)

#### Nhấn Next

Trong màn hình **Edit model access**, chọn **Next**

![img 7](/images/5-Workshop/5.3-User-management/img7.png)

#### Gửi yêu cầu

Tại trang **Review and Submit**, chọn **Submit**

![img 8](/images/5-Workshop/5.3-User-management/img8.png)

---

## Kết luận

Bạn đã:

- Cấu hình Amplify Authentication  
- Tùy chỉnh email xác thực  
- Bật quyền truy cập Amazon Bedrock  
- Kích hoạt mô hình Claude 3 Sonnet  

Giờ đây ứng dụng của bạn đã sẵn sàng sử dụng AI để tạo nội dung.
