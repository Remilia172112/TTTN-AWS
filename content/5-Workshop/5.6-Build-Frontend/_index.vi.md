---
title : "Xây dựng Frontend"
date : 2025-05-03
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

## Tổng quan

Trong phần này, bạn sẽ cập nhật website đã tạo ở module trước để sử dụng thư viện UI của Amplify nhằm xây dựng hoàn chỉnh luồng xác thực người dùng (authentication flow). Người dùng có thể đăng ký, đăng nhập, đặt lại mật khẩu và gọi GraphQL API để tạo công thức nấu ăn từ danh sách nguyên liệu.

---

## Mục tiêu

Trong hướng dẫn này, bạn sẽ:

- Cài đặt thư viện Amplify client  
- Cấu hình ứng dụng React để tích hợp authentication và gọi GraphQL API  

---

## Triển khai

### Bước 1: Cài đặt thư viện Amplify

Bạn cần 2 thư viện:

- `aws-amplify`: cung cấp API phía client để kết nối frontend với backend  
- `@aws-amplify/ui-react`: cung cấp các component UI  

#### Cài đặt thư viện

Mở terminal, di chuyển vào thư mục project: ai-recipe-generator

Chạy lệnh:
```
npm install aws-amplify @aws-amplify/ui-react
```
![img](/images/5-Workshop/5.6-Build-Frontend/img1.png)


### Bước 2: Style giao diện
#### 1. Cập nhật index.css

Mở file: ai-recipe-generator/src/index.css
Cập nhật code để căn giữa giao diện và lưu lại.

```
:root {
  font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
  line-height: 1.5;
  font-weight: 400;

  color: rgba(255, 255, 255, 0.87);

  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

}

.card {
  padding: 2em;
}

.read-the-docs {
  color: #888;
}

.box:nth-child(3n + 1) {
  grid-column: 1;
}
.box:nth-child(3n + 2) {
  grid-column: 2;
}
.box:nth-child(3n + 3) {
  grid-column: 3;
}
```
![img](/images/5-Workshop/5.6-Build-Frontend/img2.png)

#### 2. Cập nhật App.css

Mở file: src/App.css

Cập nhật code để style form nhập nguyên liệu.
```
.app-container {

  margin: 0 auto;
  padding: 20px;
  text-align: center;
}

.header-container {
  padding-bottom: 2.5rem;
  margin:  auto;
  text-align: center;

  align-items: center;
  max-width: 48rem;
  
  
}

.main-header {
  font-size: 2.25rem;
  font-weight: bold;
  color: #1a202c;
}

.main-header .highlight {
  color: #2563eb;
}

@media (min-width: 640px) {
  .main-header {
    font-size: 3.75rem;
  }
}

.description {

  font-weight: 500;
  font-size: 1.125rem;
  max-width: 65ch;
  color: #1a202c;
}

.form-container {
  margin-bottom: 20px;
}

.search-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
  align-items: center;
}

.wide-input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.search-button {
  width: 100%; /* Make the button full width */
  max-width: 300px; /* Set a maximum width for the button */
  padding: 10px;
  font-size: 16px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.search-button:hover {
  background-color: #0056b3;
}

.result-container {
  margin-top: 20px;
  transition: height 0.3s ease-out;
  overflow: hidden;
}

.loader-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.result {
  background-color: #f8f9fa;
  border: 1px solid #e9ecef;
  border-radius: 4px;
  padding: 15px;
  white-space: pre-wrap;
  word-wrap: break-word;
  color: black;
  font-weight: bold;
  text-align: left; /* Align text to the left */
}
```
![img](/images/5-Workshop/5.6-Build-Frontend/img3.png)

---

### Bước 3: Xây dựng UI

#### 1. Thêm Authentication

Mở file: ai-recipe-generator/src/main.tsx

Cập nhật code.

```
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";
import "./index.css";
import { Authenticator } from "@aws-amplify/ui-react";

ReactDOM.createRoot(document.getElementById("root")!).render(
  <React.StrictMode>
    <Authenticator>
      <App />
    </Authenticator>
  </React.StrictMode>
);
```

![img](/images/5-Workshop/5.6-Build-Frontend/img4.png)

Đoạn code sử dụng component **Amplify Authenticator** để:

- Đăng ký (Sign up)  
- Đăng nhập (Sign in)  
- Reset mật khẩu  
- Xác thực đa yếu tố (MFA)  

---

#### 2. Cấu hình Amplify và gọi API

Mở file: ai-recipe-generator/src/App.tsx


Cập nhật code.
```
import { FormEvent, useState } from "react";
import { Loader, Placeholder } from "@aws-amplify/ui-react";
import "./App.css";
import { Amplify } from "aws-amplify";
import { Schema } from "../amplify/data/resource";
import { generateClient } from "aws-amplify/data";
import outputs from "../amplify_outputs.json";
import "@aws-amplify/ui-react/styles.css";
Amplify.configure(outputs);
const amplifyClient = generateClient<Schema>({
 authMode: "userPool",
});
function App() {
 const [result, setResult] = useState<string>("");
 const [loading, setLoading] = useState(false);
 const onSubmit = async (event: FormEvent<HTMLFormElement>) => {
 event.preventDefault();
 setLoading(true);
 try {
 const formData = new FormData(event.currentTarget);
 const { data, errors } = await
amplifyClient.queries.askBedrock({
 ingredients: [formData.get("ingredients")?.toString() || ""],
 });
 if (!errors) {
 setResult(data?.body || "No data returned");
 } else {
 console.log(errors);
 }
 } catch (e) {
 alert(`An error occurred: ${e}`);
 } finally {
 setLoading(false);
 }
 };
 return (
 <div className="app-container">
 <div className="header-container">
 <h1 className="main-header">
 Meet Your Personal
 <br />
 <span className="highlight">Recipe AI</span>
 </h1>
 <p className="description">
 Simply type a few ingredients using the format ingredient1,
 ingredient2, etc., and Recipe AI will generate an all-new
recipe on
 demand...
 </p>
 </div>
 <form onSubmit={onSubmit} className="form-container">
 <div className="search-container">
 <input
 type="text"
 className="wide-input"
 id="ingredients"
 name="ingredients"
 placeholder="Ingredient1, Ingredient2, Ingredient3,...etc"
 />
 <button type="submit" className="search-button">
 Generate
 </button>
 </div>
 </form>
 <div className="result-container">
 {loading ? (
 <div className="loader-container">
 <p>Loading...</p>
 <Loader size="large" />
 <Placeholder size="large" />
 <Placeholder size="large" />
 <Placeholder size="large" />
 </div>
 ) : (
 result && <p className="result">{result}</p>
 )}
 </div>
 </div>
 );
}
export default App;
```
![img](/images/5-Workshop/5.6-Build-Frontend/img5.png)

Chức năng chính:

- Cấu hình Amplify bằng file `amplify_outputs.json`  
- Tạo client với `generateClient()`  
- Hiển thị form nhập nguyên liệu  
- Gọi query `askBedrock` để tạo công thức  
- Hiển thị kết quả cho người dùng  

---

#### 3. Chạy ứng dụng

Mở một cửa sổ terminal mới, điều hướng đến thư mục gốc của dự án của bạn (ai-recipe-generator), và chạy lệnh sau để khởi chạy ứng dụng:

```
npm run dev
```

#### 4. Mở ứng dụng

Chọn link Localhost để mở ứng dụng.
![img](/images/5-Workshop/5.6-Build-Frontend/img6.png)
#### 5. Tạo tài khoản
Chọn tab Create Account
Nhập email và mật khẩu
Nhấn Create Account
![img](/images/5-Workshop/5.6-Build-Frontend/img7.png)
#### 6. Nhập mã xác thực
Kiểm tra email
Nhập mã xác thực để đăng nhập
![img](/images/5-Workshop/5.6-Build-Frontend/img8.png)
#### 7. Tạo công thức

Sau khi đăng nhập, nhập nguyên liệu và tạo công thức.
![img](/images/5-Workshop/5.6-Build-Frontend/img9.png)
#### 8. Push code lên GitHub

Chạy lệnh:
```
git add .
git commit -m 'connect to bedrock'
git push origin main
```

![img](/images/5-Workshop/5.6-Build-Frontend/img10.png)
#### 9. Xem ứng dụng trên AWS

Truy cập:

https://console.aws.amazon.com/amplify/apps

Amplify sẽ tự động build và deploy ứng dụng tại:

https://...amplifyapp.com

Chọn Visit deployed URL để xem ứng dụng.

![img](/images/5-Workshop/5.6-Build-Frontend/img11.png)

## Kết luận

Bạn đã:

- Kết nối frontend với Amplify backend
- Xây dựng luồng xác thực người dùng
- Tích hợp API để sinh công thức từ nguyên liệu

Ứng dụng của bạn hiện đã hoàn chỉnh từ frontend đến backend và sẵn sàng hoạt động.