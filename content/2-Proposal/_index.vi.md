---
title: "Bản đề xuất"
date: 2026-05-03
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Healthcare Data Lake & Analytics Platform
## Hệ thống AWS Data Lake bảo mật hỗ trợ phân tích và đánh giá dữ liệu y tế (ICU)

### 1. Tóm tắt điều hành (Executive Summary)
Dự án **Healthcare Data Lake** được thiết kế nhằm xây dựng một hạ tầng dữ liệu y tế tập trung, bảo mật và hiệu suất cao trên nền tảng AWS. Hệ thống này giải quyết bài toán thu thập, di dời (migrate), và làm sạch lượng lớn dữ liệu lâm sàng của bệnh nhân. Mục tiêu cốt lõi là tạo ra một luồng dữ liệu (Data Pipeline) chuẩn mực để phục vụ cho việc theo dõi trực quan (Dashboard) và cung cấp bộ dữ liệu sạch (Dataset) cho các mô hình Học sâu (Deep Learning) đánh giá mức độ sinh tồn của bệnh nhân tại khu vực Hồi sức tích cực (ICU).

### 2. Tuyên bố vấn đề & Đề xuất giải pháp
*Vấn đề hiện tại:*
Dữ liệu y tế (chỉ số sinh tồn, lịch sử bệnh án, kết quả xét nghiệm) thường lưu trữ rải rác ở các hệ thống cơ sở dữ liệu quan hệ cũ (On-premise), cấu trúc dữ liệu không đồng nhất và khó mở rộng. Việc truy xuất khối lượng dữ liệu khổng lồ này để huấn luyện các mô hình học máy gặp nhiều giới hạn về hiệu năng tính toán và tiềm ẩn rủi ro lộ lọt thông tin nhạy cảm.

*Giải pháp đề xuất:*
Nền tảng sử dụng hệ sinh thái AWS với trọng tâm là bảo mật và dữ liệu lớn:
- **Di dời dữ liệu (Migration):** Dùng AWS Database Migration Service (DMS) và Schema Conversion Tool (SCT) để đưa CSDL cũ lên Amazon RDS.
- **Lưu trữ cốt lõi (Data Lake):** Đổ toàn bộ dữ liệu thô vào Amazon S3. Sử dụng AWS KMS để mã hóa dữ liệu ở trạng thái lưu trữ (Data at rest) nhằm đáp ứng chuẩn bảo mật y tế.
- **Xử lý & Phân tích (Analytics):** Dùng AWS Glue để dọn dẹp dữ liệu (ETL) và Amazon Athena để truy vấn SQL trực tiếp.
- **Trực quan hóa:** Sử dụng Amazon QuickSight để vẽ biểu đồ theo dõi các chỉ số sinh tồn và tỷ lệ rủi ro của bệnh nhân ICU.

*Giá trị mang lại (ROI):*
Giải pháp hiện đại hóa hoàn toàn kiến trúc dữ liệu y tế. Dữ liệu sau khi đi qua AWS Glue sẽ được làm sạch, loại bỏ các giá trị nhiễu, tạo thành một nền tảng vững chắc để *feed* trực tiếp vào các mô hình Deep Learning trong tương lai. Chi phí được tối ưu bằng kiến trúc Serverless (chỉ trả tiền khi truy vấn).

### 3. Kiến trúc giải pháp
Nền tảng áp dụng kiến trúc Data Lake kết hợp kiểm soát bảo mật đa lớp.

![Healthcare Data Lake Architecture](/images/2-Proposal/healthcare_datalake_architecture.png)

*Danh sách Dịch vụ AWS ứng dụng:*
- **Amazon VPC & Security Groups:** Thiết lập mạng riêng ảo cô lập hoàn toàn CSDL khỏi public internet.
- **Amazon RDS (PostgreSQL/MySQL):** Lưu trữ dữ liệu bệnh án có cấu trúc sau khi migrate.
- **Amazon S3:** Phân lớp lưu trữ Data Lake (Raw zone, Cleansed zone, Curated zone).
- **AWS KMS & IAM:** Quản lý khóa mã hóa dữ liệu y tế và giới hạn quyền truy cập (Permission Boundaries) nghiêm ngặt.
- **AWS Glue (Crawlers & ETL jobs):** Lập chỉ mục dữ liệu và tự động làm sạch các bản ghi lỗi.
- **Amazon Athena:** Truy vấn dữ liệu Serverless.
- **Amazon QuickSight:** Xây dựng Dashboard cho bác sĩ/nghiên cứu viên.

### 4. Triển khai kỹ thuật
*Các giai đoạn triển khai:*
1. **Thiết lập hạ tầng mạng & Bảo mật:** Khởi tạo VPC, Public/Private Subnets. Tạo các IAM Roles với đặc quyền tối thiểu (Least Privilege) và bật AWS Security Hub.
2. **Migration & Storage:** Tạo Amazon RDS. Mô phỏng dữ liệu y tế cũ và dùng AWS DMS để đẩy dữ liệu lên S3 (Raw Zone).
3. **Xây dựng Analytics Pipeline:** Viết kịch bản AWS Glue (Python) để chuyển đổi dữ liệu thô thành định dạng Parquet tối ưu, lưu vào S3 (Curated Zone). Thiết lập Athena để truy vấn.
4. **Data Visualization:** Cấu hình Amazon QuickSight kết nối với Athena, thiết kế biểu đồ tương quan giữa các chỉ số sinh tồn (huyết áp, nhịp tim) và tình trạng bệnh nhân.

### 5. Lộ trình & Mốc triển khai
- **Tuần 1-2:** Hoàn thiện VPC, bảo mật (KMS, IAM) và thiết lập môi trường CSDL (RDS).
- **Tuần 3-4:** Cấu hình AWS DMS để đồng bộ dữ liệu. Thiết lập cấu trúc Amazon S3 Data Lake.
- **Tuần 5-6:** Triển khai AWS Glue ETL jobs, chạy Crawler để nhận diện Schema và kiểm thử truy vấn SQL bằng Athena.
- **Tuần 7-8:** Tích hợp QuickSight, xây dựng Dashboard hoàn chỉnh, tối ưu chi phí và viết báo cáo tổng kết.

### 6. Ước tính ngân sách

*Tóm tắt chi phí hạ tầng Cloud (Hàng tháng):*
- **Amazon RDS (t2.micro - Multi-AZ):** ~15.00 USD (Miễn phí nếu trong Free Tier).
- **Amazon S3 (Standard):** ~0.25 USD (Lưu trữ khoảng 10 GB dữ liệu y tế text/JSON/CSV).
- **AWS KMS:** ~1.00 USD (Cho 1 khóa mã hóa Custom Key quản lý dữ liệu).
- **AWS Glue & Athena:** ~2.00 USD (Tùy thuộc vào thời gian chạy ETL và số lượng data được quét).
- **Amazon QuickSight:** ~9.00 USD (Tài khoản Author).
**=> Tổng chi phí AWS:** Khoảng **27.25 USD/tháng**. *(Lưu ý: Hầu hết có thể tận dụng AWS Free Tier trong thời gian thực tập).*

### 7. Đánh giá rủi ro
*Ma trận rủi ro & Chiến lược giảm thiểu:*
- **Lộ lọt dữ liệu nhạy cảm:** Tác động Rất Cao. *Giảm thiểu:* Bắt buộc mã hóa toàn bộ S3 Buckets bằng AWS KMS, không cấp quyền Public Access, quản lý qua IAM Role.
- **Thất thoát dữ liệu khi Migration:** Tác động Cao. *Giảm thiểu:* Bật tính năng Validation trên AWS DMS và dùng AWS Backup để tạo bản Snapshot định kỳ cho RDS.
- **Chi phí truy vấn Athena tăng vọt:** Xác suất Trung bình. *Giảm thiểu:* AWS Glue chuyển đổi dữ liệu sang định dạng Parquet (định dạng cột nén) và phân chia vùng (Partitioning) để giảm thiểu lượng dữ liệu quét mỗi lần truy vấn.

### 8. Kết quả kỳ vọng
Dự án không chỉ là một bài toán thực hành hạ tầng Cloud mà còn mang lại giá trị to lớn cho lĩnh vực Y tế số. Việc sở hữu một Data Lake được quy hoạch bài bản trên AWS giúp loại bỏ tình trạng "rác dữ liệu" (Data Silos), cho phép trích xuất thông tin nhanh chóng và cung cấp bộ dữ liệu (dataset) chất lượng cao để triển khai các thuật toán Deep Learning dự đoán y khoa tiên tiến nhất.