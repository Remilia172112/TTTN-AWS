---
title : "Xây dựng Backend không máy chủ"
date : 2025-05-03
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

## Tổng quan

Trong phần này, bạn sẽ cấu hình một serverless function sử dụng AWS Amplify và AWS Lambda. Hàm này nhận đầu vào là các nguyên liệu (ingredients) để tạo prompt. Sau đó, nó gửi prompt này đến Amazon Bedrock thông qua HTTP POST request tới mô hình Claude 3 Sonnet.

Phần body của request sẽ chứa chuỗi prompt trong một mảng `messages`.

---

## Mục tiêu

Trong hướng dẫn này, bạn sẽ:

- Thêm Amazon Bedrock làm nguồn dữ liệu (data source)  
- Cấu hình logic xử lý nghiệp vụ (business logic)  

---

## Triển khai

### Bước 1: Tạo Lambda function để xử lý request

#### Tạo file function

Trên máy local, truy cập thư mục: ai-recipe-generator/amplify/data và tạo file mới có tên: bedrock.js


![img 1](/images/5-Workshop/5.4-Serverless-backend/img1.png)

#### Thêm code cho function

Cập nhật nội dung file `bedrock.js` với đoạn code:
```
export function request(ctx) {
    const { ingredients = [] } = ctx.args;
  
    // Construct the prompt with the provided ingredients
    const prompt = `Suggest a recipe idea using these ingredients: ${ingredients.join(", ")}.`;
  
    // Return the request configuration
    return {
      resourcePath: `/model/anthropic.claude-3-sonnet-20240229-v1:0/invoke`,
      method: "POST",
      params: {
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          anthropic_version: "bedrock-2023-05-31",
          max_tokens: 1000,
          messages: [
            {
              role: "user",
              content: [
                {
                  type: "text",
                  text: `\n\nHuman: ${prompt}\n\nAssistant:`,
                },
              ],
            },
          ],
        }),
      },
    };
  }
  
  export function response(ctx) {
    // Parse the response body
    const parsedBody = JSON.parse(ctx.result.body);
    // Extract the text content from the response
    const res = {
      body: parsedBody.content[0].text,
    };
    // Return the response
    return res;
  }
```

Đoạn code này:

- Định nghĩa hàm `request` để tạo HTTP request gọi tới Claude 3 Sonnet trên Amazon Bedrock  
- Định nghĩa hàm `response` để xử lý dữ liệu trả về và tạo công thức nấu ăn  

---

### Bước 2: Thêm Amazon Bedrock làm data source

#### Cập nhật backend

Mở file: amplify/backend.ts và cập nhật nội dung file theo code sau đó lưu lại:
```
import { defineBackend } from "@aws-amplify/backend";
import { data } from "./data/resource";
import { PolicyStatement } from "aws-cdk-lib/aws-iam";
import { auth } from "./auth/resource";

const backend = defineBackend({
  auth,
  data,
});

const bedrockDataSource = backend.data.resources.graphqlApi.addHttpDataSource(
  "bedrockDS",
  "https://bedrock-runtime.us-east-1.amazonaws.com",
  {
    authorizationConfig: {
      signingRegion: "us-east-1",
      signingServiceName: "bedrock",
    },
  }
);

bedrockDataSource.grantPrincipal.addToPrincipalPolicy(
  new PolicyStatement({
    resources: [
      "arn:aws:bedrock:us-east-1::foundation-model/anthropic.claude-3-sonnet-20240229-v1:0",
    ],
    actions: ["bedrock:InvokeModel"],
    
  })
);
```

![img 2](/images/5-Workshop/5.4-Serverless-backend/img2.png)

Đoạn cấu hình này sẽ:

- Thêm HTTP data source cho Amazon Bedrock  
- Cấp quyền để gọi mô hình Claude  

---

## Kết luận

Bạn đã:

- Tạo Lambda function bằng AWS Amplify  
- Viết logic xử lý request/response  
- Kết nối Amazon Bedrock làm data source  

Backend serverless của bạn giờ đã sẵn sàng để xử lý yêu cầu và tương tác với AI.