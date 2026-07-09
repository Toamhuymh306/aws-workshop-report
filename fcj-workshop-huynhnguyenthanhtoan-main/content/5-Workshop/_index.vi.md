---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Serverless AI Inference Platform

#### Tổng quan

Workshop này triển khai một hệ thống AI inference theo kiến trúc serverless trên AWS. Người dùng xác thực danh tính, gọi API để lấy pre-signed URL, upload ảnh lá cây lên S3, sau đó hệ thống tự động đẩy sự kiện vào SQS để kích hoạt Lambda chạy mô hình AI và lưu kết quả vào DynamoDB.

Luồng xử lý chính:

- Client gọi API Gateway + Cognito Authorizer để lấy pre-signed URL.
- Client upload ảnh trực tiếp lên S3 Raw.
- S3 phát sinh sự kiện tạo object và gửi thông điệp vào SQS.
- Inference Lambda (container image từ ECR) đọc message SQS, tải ảnh, chạy model và lưu kết quả vào DynamoDB.

#### Nội dung

1. [Tổng quan kiến trúc](5.1-Workshop-overview/)
2. [Điều kiện chuẩn bị](5.2-Prerequiste/)
3. [Khởi tạo Storage và Deploy AI](5.3-S3-vpc/)
4. [Thiết lập upload an toàn và event-driven](5.4-S3-onprem/)
5. [Kiểm thử và đánh giá kỹ thuật](5.5-Policy/)
6. [Dọn dẹp tài nguyên](5.6-Cleanup/)
