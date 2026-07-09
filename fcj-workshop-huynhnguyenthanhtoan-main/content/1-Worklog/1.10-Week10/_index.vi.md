---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:

- Tích hợp hệ thống và kiểm thử end-to-end.
- Xác thực toàn bộ luồng kiến trúc đã thiết kế.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Mapping toàn bộ luồng: Client -> Cognito -> API Gateway -> Lambda -> S3 -> SQS -> ECR Lambda -> DB | 22/06/2026 | 22/06/2026 | https://000046.awsstudygroup.com/ |
| 3 | - Chạy nhiều lượt kiểm thử E2E mô phỏng người dùng thực tế | 23/06/2026 | 23/06/2026 | https://000047.awsstudygroup.com/ |
| 4 | - Debug các edge case (ảnh lỗi định dạng, JWT token hết hạn) | 24/06/2026 | 24/06/2026 | https://000048.awsstudygroup.com/ |
| 5 | - Kiểm tra CloudWatch Logs để phát hiện cảnh báo/điểm nghẽn tiềm ẩn | 25/06/2026 | 25/06/2026 | https://000049.awsstudygroup.com/ |
| 6 | - Tinh chỉnh IAM Role theo nguyên tắc least privilege | 26/06/2026 | 26/06/2026 | https://000050.awsstudygroup.com/ |

### Kết quả đạt được tuần 10:

- Xác nhận toàn bộ pipeline Serverless AI vận hành ổn định, an toàn, có khả năng chịu lỗi.
- Kiểm chứng dữ liệu đi đúng theo kiến trúc đã thiết kế.
