---
title: "Khởi tạo Storage và Deploy AI"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

#### Step 1: Khởi tạo Storage và Database

1. Tạo S3 bucket lưu ảnh đầu vào:
   - Tên gợi ý: `s3-raw-images`.
   - Bật mã hoá mặc định (SSE-S3 hoặc SSE-KMS).
2. Tạo Lifecycle Policy:
   - Chuyển object cũ sang Glacier Archive sau 30 ngày để tối ưu chi phí.
3. Tạo DynamoDB table:
   - Tên bảng: `AI_Diagnosis_Results`.
   - Partition key: `ImageID` (String).

#### Step 2: Đóng gói và deploy AI model

1. Tạo repository trên Amazon ECR.
2. Build Docker image chứa:
   - Runtime Python.
   - Thư viện AI (ví dụ PyTorch/ONNX Runtime).
   - Model inference.
3. Push image lên ECR.
4. Tạo `inference-lambda` từ container image:
   - Timeout: 5 phút.
   - Memory: 3008 MB.
   - IAM role: cho phép đọc SQS, đọc S3, ghi DynamoDB, ghi CloudWatch Logs.

#### Kết quả đạt được

- Đã có lớp lưu trữ ảnh và kết quả inference tách biệt.
- Đã có hạ tầng AI inference chạy trên Lambda container để xử lý model lớn.
