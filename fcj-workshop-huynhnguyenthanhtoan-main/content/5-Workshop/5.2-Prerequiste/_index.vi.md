---
title: "Các bước chuẩn bị"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

#### Điều kiện cần trước khi làm lab

- Tài khoản AWS đang hoạt động.
- Khu vực triển khai: `ap-southeast-1`.
- Đã cài đặt sẵn:
  - AWS CLI
  - Docker
  - Postman
- Có sẵn mô hình AI chẩn đoán ảnh lá cây (`.pt` hoặc `.onnx`).

#### Quy ước tài nguyên

- Bucket ảnh gốc: `s3-raw-images`.
- Bucket ảnh xử lý (tuỳ chọn): `s3-processed-images`.
- DynamoDB table: `AI_Diagnosis_Results`.
- Queue: `ai-inference-queue`.
- Lambda functions:
  - `presign-lambda`
  - `inference-lambda`

#### IAM tối thiểu cần có

- Quyền tạo và cấu hình S3, SQS, Lambda, ECR, DynamoDB, API Gateway, Cognito, CloudWatch Logs.
- Role cho `inference-lambda`:
  - Đọc message từ SQS.
  - Đọc object từ S3 Raw.
  - Ghi kết quả vào DynamoDB.
  - Ghi log vào CloudWatch.

#### Kiểm tra môi trường nhanh

1. Kiểm tra thông tin AWS CLI:
   - `aws sts get-caller-identity`
2. Kiểm tra Docker đã chạy ổn định.
3. Chuẩn bị bộ ảnh test gồm ít nhất 3 ảnh lá cây để kiểm thử.
