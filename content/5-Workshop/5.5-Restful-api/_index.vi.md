---
title : "Triển khai API Backend"
date : 2025-05-03
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

## Tổng quan

Trong phần này, bạn sẽ cấu hình một truy vấn (query) tùy chỉnh để sử dụng data source và resolver đã định nghĩa ở phần trước nhằm tạo công thức nấu ăn dựa trên danh sách nguyên liệu.

Query này sẽ sử dụng một custom type để định dạng dữ liệu phản hồi từ Amazon Bedrock.

---

## Mục tiêu

Trong hướng dẫn này, bạn sẽ:

- Định nghĩa GraphQL Query nhận đầu vào là một mảng chuỗi  
- Định nghĩa custom type để cấu trúc dữ liệu trả về  

---

## Triển khai

---

### Cấu hình Amplify Data

#### Bước 1: Cập nhật file resource.ts

Trên máy local, truy cập: ai-recipe-generator/amplify/data/resource.ts và cập nhật nội dung file theo code được cung cấp và lưu lại.
```
import { type ClientSchema, a, defineData } from "@aws-amplify/backend";

const schema = a.schema({
  BedrockResponse: a.customType({
    body: a.string(),
    error: a.string(),
  }),
  askBedrock: a
    .query()
    .arguments({ ingredients: a.string().array() })
    .returns(a.ref("BedrockResponse"))
    .authorization((allow) => [allow.authenticated()])
    .handler(
      a.handler.custom({
        entry: "./bedrock.js",
        dataSource: "bedrockDS"
      })
    ),
});

export type Schema = ClientSchema<typeof schema>;

export const data = defineData({
  schema,
  authorizationModes: {
    defaultAuthorizationMode: "apiKey",
    apiKeyAuthorizationMode: {
      expiresInDays: 30,
    },
  },
});
```
![img 1](/images/5-Workshop/5.5-Restful-api/img1.png)

Đoạn code này:

- Định nghĩa query `askBedrock` nhận đầu vào là mảng `ingredients` (chuỗi)  
- Trả về kiểu dữ liệu `BedrockResponse`  
- Sử dụng custom handler từ file `bedrock.js`  
- Kết nối với data source `bedrockDS`  

---

### Bước 2: Deploy tài nguyên

Mở terminal, di chuyển đến thư mục project: ai-recipe-generator

Chạy lệnh sau để deploy tài nguyên cloud trong môi trường sandbox:
```bash
npx ampx sandbox
```
Lệnh này sẽ deploy các tài nguyên cloud vào một môi trường phát triển riêng biệt để bạn có thể test nhanh.

![img 2](/images/5-Workshop/5.5-Restful-api/img2.png)

---
### Bước 3: Xem thông báo xác nhận

Sau khi môi trường cloud sandbox được deploy hoàn tất, terminal sẽ hiển thị thông báo xác nhận.

![img 3](/images/5-Workshop/5.5-Restful-api/img3.png)

---

### Bước 4: Kiểm tra file output

Xác nhận rằng file sau đã được tạo và thêm vào project của bạn: amplify_outputs.json


![img 4](/images/5-Workshop/5.5-Restful-api/img4.png)

File này chứa các thông tin cấu hình cần thiết để frontend có thể kết nối với backend.

---

## Kết luận

Bạn đã:

- Cấu hình GraphQL API  
- Tạo custom query kết nối tới Amazon Bedrock  
- Xây dựng chức năng sinh công thức từ danh sách nguyên liệu  

Hệ thống backend API của bạn hiện đã sẵn sàng để frontend sử dụng và tương tác với AI.