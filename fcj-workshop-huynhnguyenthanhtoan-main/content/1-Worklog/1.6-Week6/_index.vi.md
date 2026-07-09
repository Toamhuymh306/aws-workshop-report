---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

- Triển khai AI model đã container hóa lên AWS Lambda.
- Cấu hình tài nguyên Lambda cho tác vụ tính toán nặng.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tạo Lambda function mới bằng tùy chọn "Container Image" từ ECR | 25/05/2026 | 25/05/2026 | https://000026.awsstudygroup.com/ |
| 3 | - Cấu hình Lambda: tăng Timeout (5 phút) và Memory (3008 MB) | 26/05/2026 | 26/05/2026 | https://000027.awsstudygroup.com/ |
| 4 | - Cấp IAM quyền cho Lambda đọc S3 Raw và ghi S3 Processed | 27/05/2026 | 27/05/2026 | https://000028.awsstudygroup.com/ |
| 5 | - Cập nhật code Lambda: tải object từ S3, chạy inference, upload kết quả đã xử lý | 28/05/2026 | 28/05/2026 | https://000029.awsstudygroup.com/ |
| 6 | - Kiểm thử thủ công Inference Lambda qua AWS Console | 29/05/2026 | 29/05/2026 | https://000030.awsstudygroup.com/ |

### Kết quả đạt được tuần 6:

- Chạy thành công PyTorch AI model hoàn toàn trong môi trường serverless.
- Vượt qua vấn đề cold start và giới hạn bộ nhớ của Lambda.
