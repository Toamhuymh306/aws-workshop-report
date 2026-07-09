---
title: "Giới thiệu"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

#### Tổng quan bài toán

Hệ thống "Serverless AI Inference Platform" được xây dựng để hỗ trợ chẩn đoán bệnh trên lá cây bằng hình ảnh. Điểm quan trọng của kiến trúc là tách luồng upload và luồng xử lý AI thành các thành phần độc lập để tăng khả năng mở rộng, giảm lỗi nghẽn cổ chai và tối ưu chi phí vận hành.

#### Kiến trúc tổng thể

- **Amazon Cognito**: xác thực người dùng và kiểm soát truy cập API.
- **API Gateway + Presign Lambda**: cấp pre-signed URL cho client upload ảnh trực tiếp lên S3.
- **Amazon S3**: lưu trữ ảnh đầu vào (`Raw`) và dữ liệu đã xử lý (`Processed`).
- **Amazon SQS**: đóng vai trò buffer, nhận sự kiện upload và phân phối đến Inference Lambda.
- **Inference Lambda (ECR Image)**: thực thi model AI và tạo kết quả dự đoán.
- **Amazon DynamoDB**: lưu kết quả inference để tra cứu nhanh.

#### Luồng xử lý

1. Người dùng đăng nhập và lấy JWT token từ Cognito.
2. Client gọi API Gateway để lấy pre-signed URL.
3. Client upload ảnh lên S3 Raw bằng phương thức `PUT`.
4. S3 phát sự kiện tạo object sang SQS.
5. Inference Lambda đọc message, xử lý ảnh bằng model AI.
6. Kết quả được ghi vào DynamoDB theo từng `ImageID`.
