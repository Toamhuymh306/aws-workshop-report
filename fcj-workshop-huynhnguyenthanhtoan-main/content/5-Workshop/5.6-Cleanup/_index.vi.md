---
title: "Dọn dẹp tài nguyên"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

#### Dọn dẹp tài nguyên

Sau khi hoàn thành workshop, cần xoá toàn bộ tài nguyên để tránh phát sinh chi phí ngoài ý muốn.

#### Checklist clean-up

1. **S3**
   - Xoá toàn bộ object trong bucket Raw/Processed.
   - Xoá các bucket đã tạo trong workshop.

2. **SQS**
   - Xoá queue `ai-inference-queue`.

3. **API Gateway + Cognito**
   - Xoá API cho pre-signed URL.
   - Xoá hoặc tắt các cấu hình user pool dùng cho bài lab (nếu không còn sử dụng).

4. **Lambda**
   - Xoá `presign-lambda` và `inference-lambda`.
   - Kiểm tra và xoá event source mapping từ SQS.

5. **ECR**
   - Xoá image tag và repository đã tạo.

6. **DynamoDB**
   - Xoá bảng `AI_Diagnosis_Results`.

7. **CloudWatch Logs**
   - Xoá log groups của các Lambda nếu không cần lưu lại.

#### Kết luận

Hoàn tất clean-up giúp môi trường AWS gọn gàng, tránh chi phí rò rỉ và sẵn sàng cho lần triển khai tiếp theo.
