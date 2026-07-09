---
title: "Upload an toàn và Event-driven"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

#### Step 3: Thiết lập luồng upload an toàn

1. Tạo `presign-lambda`:
   - Dùng Boto3 gọi `generate_presigned_url` với action `put_object`.
   - Trả về URL có thời hạn ngắn để giảm rủi ro lộ link upload.
2. Tạo REST API trên API Gateway:
   - Endpoint để client lấy pre-signed URL.
   - Tích hợp Cognito Authorizer để yêu cầu JWT token hợp lệ.
3. Từ client, upload ảnh trực tiếp lên S3 bằng HTTP `PUT` qua URL đã ký.

#### Step 4: Kết nối luồng event-driven

1. Tạo Standard Queue trên Amazon SQS (`ai-inference-queue`).
2. Cấu hình S3 Event Notification:
   - Sự kiện: `s3:ObjectCreated:*`.
   - Đích: SQS queue.
3. Cấu hình SQS làm trigger cho `inference-lambda`.

#### Kết quả đạt được

- Luồng upload tách khỏi API backend, tránh lỗi payload lớn.
- Luồng xử lý ảnh hoạt động theo sự kiện, chịu tải tốt hơn khi có nhiều request đồng thời.
