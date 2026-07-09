---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Proposal: Serverless AI Inference Platform

## 1. Tổng quan dự án

Xây dựng hệ thống serverless tự động nhận diện và chẩn đoán bệnh trên lá cây thông qua ảnh upload từ người dùng cuối. Hệ thống được thiết kế để xử lý theo sự kiện, không cần vận hành server 24/7 nhưng vẫn đảm bảo hiệu năng khi tải tăng cao.

## 2. Vấn đề cần giải quyết

Trong thực tế nông nghiệp, việc nhầm lẫn giữa các loại bệnh trên lá xảy ra rất phổ biến. Ví dụ, vết thương do nhện đỏ trên lá cacao có thể bị chẩn đoán nhầm sang bệnh nấm VSD hoặc Thán thư nếu chỉ quan sát thủ công. Bài toán cần một nền tảng cloud ổn định để người dùng tải ảnh và nhận kết quả AI gần thời gian thực.

## 3. Kiến trúc đề xuất

Kiến trúc theo hướng event-driven và hoàn toàn serverless:

- Amazon API Gateway
- AWS Lambda (Presign Lambda và Inference Lambda)
- Amazon S3 (lưu ảnh Raw/Processed)
- Amazon SQS (đệm tải, tách rời thành phần)
- Amazon ECR (lưu container image của mô hình AI)
- Amazon DynamoDB (lưu kết quả inference)

## 4. Lý do chọn dịch vụ

- API Gateway + Presign Lambda: tạo pre-signed URL để client upload trực tiếp lên S3, tránh giới hạn payload khi gửi ảnh qua API.
- S3: lưu trữ ảnh đầu vào và đầu ra, dễ mở rộng, tối ưu chi phí với Lifecycle Policy.
- SQS: chống quá tải cho inference Lambda khi nhiều ảnh được upload cùng lúc.
- Lambda + ECR: đóng gói model AI lớn bằng container image, giải quyết giới hạn của Lambda dạng ZIP.
- DynamoDB: ghi/đọc kết quả nhanh, phù hợp dữ liệu NoSQL theo từng ảnh.

## 5. Rủi ro và phương án xử lý

- Rủi ro chính: mô hình AI dung lượng lớn vượt ngưỡng tài nguyên Lambda truyền thống.
- Giải pháp: đóng gói model thành container image và triển khai Lambda từ Amazon ECR.

## 6. Kết quả kỳ vọng

- Người dùng upload ảnh dễ dàng qua URL ký sẵn.
- Pipeline xử lý ảnh hoạt động tự động theo sự kiện.
- Kết quả chẩn đoán được lưu nhất quán trong DynamoDB để truy xuất nhanh.
