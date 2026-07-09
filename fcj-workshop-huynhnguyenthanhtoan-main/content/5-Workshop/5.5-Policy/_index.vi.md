---
title: "Kiểm thử và Validation"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5.5 </b> "
---

#### Step 5: Kiểm thử và Validation

Thực hiện kiểm thử toàn bộ pipeline từ upload đến lưu kết quả:

1. Dùng Postman gọi endpoint lấy pre-signed URL (kèm JWT token).
2. Upload một ảnh lá cây qua HTTP `PUT` vào URL đã ký.
3. Kiểm tra S3 đã tạo object đúng thư mục Raw.
4. Quan sát CloudWatch Logs của `inference-lambda` để xác nhận:
   - Nhận message từ SQS.
   - Tải ảnh từ S3 thành công.
   - Chạy model inference không lỗi.
   - Ghi kết quả vào DynamoDB thành công.
5. Mở DynamoDB table `AI_Diagnosis_Results` và đối chiếu các trường kết quả.

#### Đóng góp cá nhân (Reflection)

- **Khó khăn**:
  - Lỗi `HTTP 413 Payload Too Large` khi cố gửi ảnh trực tiếp qua API Gateway.
  - Lambda timeout khi model AI khởi động lần đầu.
- **Cách giải quyết**:
  - Thiết kế lại luồng upload bằng pre-signed URL để client upload trực tiếp lên S3.
  - Dùng container image trên ECR để đóng gói model và thư viện AI đầy đủ, giảm giới hạn của Lambda ZIP.
- **Hướng phát triển**:
  - Tích hợp WebSocket API để đẩy kết quả inference theo thời gian thực về client, không cần refresh thủ công.
