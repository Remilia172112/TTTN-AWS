---
title : "Triển khai ứng dụng với AWS Amplify"
date : 2025-05-03 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

AWS Amplify cung cấp quy trình làm việc CI/CD dựa trên Git để xây dựng, triển khai và lưu trữ các ứng dụng web trang đơn (single-page web applications) hoặc các trang web tĩnh có backend. Khi được kết nối với kho lưu trữ Git, Amplify sẽ tự động xác định các cấu hình bản dựng (build settings) cho cả framework frontend và các tài nguyên backend đã được cấu hình, đồng thời tự động triển khai các bản cập nhật sau mỗi lần commit mã nguồn.

Trong bài thực hành này, bạn sẽ bắt đầu bằng cách tạo một ứng dụng React mới và đẩy (push) mã nguồn lên kho lưu trữ GitHub. Sau đó, bạn sẽ kết nối kho lưu trữ này với dịch vụ lưu trữ web AWS Amplify và triển khai ứng dụng lên mạng phân phối nội dung (CDN) khả dụng trên toàn cầu, được lưu trữ trên tên miền `amplifyapp.com`.

### Những gì bạn sẽ đạt được
Trong hướng dẫn này, bạn sẽ:
* Tạo một ứng dụng web mới.
* Thiết lập Amplify cho dự án của bạn.

### Triển khai

#### Bước 1: Tạo một ứng dụng React mới

#### Tạo ứng dụng
Mở một cửa sổ terminal hoặc command line mới, chạy lệnh sau để sử dụng Vite tạo một ứng dụng React:

```bash
npm create vite@latest ai-recipe-generator -- --template react-ts -y
cd ai-recipe-generator
npm install
npm run dev
```
![img](/images/5-Workshop/5.2-Static-web-hosting/img1.png)
#### Mở ứng dụng

Trong cửa sổ terminal, chọn và mở liên kết **Local** để xem ứng dụng Vite + React.
![img](/images/5-Workshop/5.2-Static-web-hosting/img2.png)


#### Bước 2: Khởi tạo kho lưu trữ GitHub

Trong bước này, bạn sẽ tạo một kho lưu trữ GitHub và commit mã nguồn của mình vào kho lưu trữ. Bạn sẽ cần một tài khoản GitHub để hoàn thành bước này, nếu bạn chưa có tài khoản, hãy đăng ký tại đây.

**Lưu ý:**
Nếu bạn chưa từng sử dụng GitHub trên máy tính của mình, hãy làm theo các bước sau trước khi tiếp tục để cho phép kết nối với tài khoản của bạn.

#### Đăng nhập vào GitHub
Đăng nhập vào GitHub tại [https://github.com/](https://github.com/).
![img](/images/5-Workshop/5.2-Static-web-hosting/img3.png)


#### Bắt đầu một kho lưu trữ mới
Trong phần **Start a new repository** (Bắt đầu kho lưu trữ mới), hãy đưa ra các lựa chọn sau:
- Đối với **Repository name** (Tên kho lưu trữ), hãy nhập `ai-recipe-generator`, và chọn nút radio **Public** (Công khai).
- Sau đó chọn **Create a new repository** (Tạo kho lưu trữ mới).
![img](/images/5-Workshop/5.2-Static-web-hosting/img4.png)

#### Khởi tạo Git
Mở một cửa sổ terminal mới, điều hướng đến thư mục gốc của dự án của bạn (`ai-recipe-generator`), và chạy các lệnh sau để khởi tạo git và đẩy ứng dụng lên kho lưu trữ GitHub mới:

**Lưu ý:**
Thay thế URL SSH GitHub trong lệnh bằng URL GitHub của bạn.

```bash
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:<your-username>/ai-recipe-generator.git
git branch -M main
git push -u origin main
```
![img](/images/5-Workshop/5.2-Static-web-hosting/img5.png)

#### Bước 3: Cài đặt các gói Amplify

#### Cài đặt Amplify
Mở một cửa sổ terminal mới, điều hướng đến thư mục gốc của ứng dụng (`ai-recipe-generator`) và chạy lệnh sau:
```bash
npm create amplify@latest -y
```
![img](/images/5-Workshop/5.2-Static-web-hosting/img6.png)

#### Xem thư mục
Việc chạy lệnh trước đó sẽ tạo ra một bộ khung dự án Amplify gọn nhẹ ngay trong thư mục của ứng dụng.
![img](/images/5-Workshop/5.2-Static-web-hosting/img7.png)

#### Bước 4: Triển khai ứng dụng của bạn với AWS Amplify

Đăng nhập vào **AWS Management Console** trong một cửa sổ trình duyệt mới, và mở bảng điều khiển AWS Amplify tại [https://console.aws.amazon.com/amplify/apps](https://console.aws.amazon.com/amplify/apps).

Chọn **Create new app** (Tạo ứng dụng mới).
![img](/images/5-Workshop/5.2-Static-web-hosting/img8.png)

#### Chọn GitHub để triển khai ứng dụng
Trên trang **Start building with Amplify** (Bắt đầu xây dựng với Amplify), ở phần **Deploy your app** (Triển khai ứng dụng của bạn), hãy chọn **GitHub**, và chọn **Next** (Tiếp theo).
![img](/images/5-Workshop/5.2-Static-web-hosting/img9.png)


#### Xác thực với GitHub
Khi được nhắc, hãy xác thực với GitHub. Bạn sẽ tự động được chuyển hướng trở lại bảng điều khiển Amplify.
Chọn kho lưu trữ và nhánh `main` mà bạn đã tạo trước đó. Sau đó chọn **Next** (Tiếp theo).
![img](/images/5-Workshop/5.2-Static-web-hosting/img10.png)

#### Chọn Tiếp theo
Giữ nguyên các cài đặt bản dựng (build settings) mặc định, và chọn **Next** (Tiếp theo).
![img](/images/5-Workshop/5.2-Static-web-hosting/img11.png)

#### Xem lại cấu hình
Xem lại các thông tin đầu vào đã chọn, và chọn **Save and deploy** (Lưu và triển khai).
![img](/images/5-Workshop/5.2-Static-web-hosting/img12.png)

#### Xem ứng dụng của bạn

AWS Amplify giờ đây sẽ build (xây dựng) mã nguồn của bạn và triển khai ứng dụng tại `https://...amplifyapp.com`, và trên mỗi lần `git push`, phiên bản triển khai của bạn sẽ được cập nhật. Có thể mất tối đa 5 phút để triển khai ứng dụng của bạn.

Sau khi quá trình build hoàn tất, hãy chọn nút **Visit deployed URL** (Truy cập URL đã triển khai) để xem ứng dụng web của bạn đang hoạt động trực tiếp.
![img](/images/5-Workshop/5.2-Static-web-hosting/img13.png)

## Kết luận

Bạn đã triển khai thành công một ứng dụng React lên AWS bằng cách tích hợp với GitHub và sử dụng AWS Amplify. Với AWS Amplify, bạn có thể liên tục triển khai ứng dụng của mình trên Đám mây (Cloud) và lưu trữ nó trên một mạng CDN có sẵn trên toàn cầu.