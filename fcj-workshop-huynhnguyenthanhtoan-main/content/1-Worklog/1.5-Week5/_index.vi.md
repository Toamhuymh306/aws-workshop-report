---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

- Đóng gói ứng dụng AI bằng container để vượt giới hạn kích thước triển khai Lambda.
- Làm chủ Amazon Elastic Container Registry (ECR).

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu Docker cơ bản và nguyên lý container hóa<br>- Cài Docker trên máy local | 18/05/2026 | 18/05/2026 | https://000021.awsstudygroup.com/ |
| 3 | - Viết Dockerfile với base image `public.ecr.aws/lambda/python`<br>- Tích hợp PyTorch, OpenCV và model weights | 19/05/2026 | 19/05/2026 | https://000022.awsstudygroup.com/ |
| 4 | - Build và test Docker image local bằng AWS Lambda Runtime Interface Emulator | 20/05/2026 | 20/05/2026 | https://000023.awsstudygroup.com/ |
| 5 | - Tạo private repository trên Amazon ECR | 21/05/2026 | 21/05/2026 | https://000024.awsstudygroup.com/ |
| 6 | - Xác thực Docker CLI với ECR và push AI container image | 22/05/2026 | 22/05/2026 | https://000025.awsstudygroup.com/ |

### Kết quả đạt được tuần 5:

- Đóng gói thành công workload ML dung lượng lớn.
- Đẩy container image lên Amazon ECR, sẵn sàng cho thực thi serverless.
