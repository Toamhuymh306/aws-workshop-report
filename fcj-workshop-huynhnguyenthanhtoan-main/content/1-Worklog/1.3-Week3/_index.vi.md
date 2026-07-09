---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

- Thiết kế luồng upload tệp an toàn.
- Triển khai S3 pre-signed URL để vượt giới hạn payload của API Gateway.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Nghiên cứu giới hạn payload của API Gateway (10 MB) và Lambda<br>- Tìm hiểu cơ chế S3 pre-signed URL | 04/05/2026 | 04/05/2026 | https://000011.awsstudygroup.com/ |
| 3 | - Viết Lambda (Python/Boto3) để tạo `put_object` pre-signed URL | 05/05/2026 | 05/05/2026 | https://000012.awsstudygroup.com/ |
| 4 | - Gán IAM role cho phép Lambda tạo URL cho bucket S3 chỉ định | 06/05/2026 | 06/05/2026 | https://000013.awsstudygroup.com/ |
| 5 | - Kết nối Lambda tạo URL vào endpoint API Gateway đã bảo mật | 07/05/2026 | 07/05/2026 | https://000014.awsstudygroup.com/ |
| 6 | - Kiểm thử end-to-end upload trực tiếp từ client lên S3 bằng URL đã tạo | 08/05/2026 | 08/05/2026 | https://000015.awsstudygroup.com/ |

### Kết quả đạt được tuần 3:

- Giải quyết nút thắt upload tệp lớn bằng cách upload trực tiếp lên S3.
- Tạo thành công liên kết upload tạm thời, an toàn bằng Lambda và Boto3.
