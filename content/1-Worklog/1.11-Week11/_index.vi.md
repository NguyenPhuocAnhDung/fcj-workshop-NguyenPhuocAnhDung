---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
{{%  notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{%  /notice %}}


### Mục tiêu tuần 11:

* Tìm hiểu kiến trúc hướng sự kiện và hệ thống messaging với Amazon SQS, SNS.
* Nghiên cứu CloudWatch, AWS X-Ray và các công cụ giám sát ứng dụng.
* Tìm hiểu logging, metrics, alarms và distributed tracing.
* Tổng hợp giải pháp observability cho hệ thống serverless.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2   | - Tìm hiểu kiến trúc hướng sự kiện (Event-Driven):<br>&emsp; + Amazon SQS (Simple Queue Service) - hàng đợi tin nhắn<br>&emsp; + Amazon SNS (Simple Notification Service) - thông báo<br>&emsp; + Kết hợp SQS + SNS + Lambda Fan-out pattern | 14/07/2026   | 14/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Thực hành Amazon SQS và SNS:<br>&emsp; + Tạo Standard Queue và FIFO Queue<br>&emsp; + Cấu hình Dead Letter Queue (DLQ)<br>&emsp; + Tạo SNS Topic và Subscription | 15/07/2026   | 15/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Nghiên cứu giám sát ứng dụng với CloudWatch:<br>&emsp; + CloudWatch Metrics, Logs và Alarms<br>&emsp; + Tạo Custom Metrics từ ứng dụng<br>&emsp; + Cấu hình CloudWatch Dashboard | 16/07/2026   | 16/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Thực hành AWS X-Ray (Distributed Tracing):<br>&emsp; + Kích hoạt X-Ray tracing cho Lambda và API Gateway<br>&emsp; + Phân tích Service Map và Trace details | 17/07/2026   | 17/07/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Tổng hợp giải pháp Observability cho hệ thống Serverless:<br>&emsp; + Kết hợp CloudWatch + X-Ray + SNS Alerts<br>&emsp; + Thiết kế chiến lược giám sát toàn diện | 18/07/2026   | 20/07/2026      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 11:

* Nắm vững kiến trúc messaging với SQS, SNS và các pattern phổ biến (Fan-out, DLQ).
* Thiết lập hệ thống giám sát toàn diện với CloudWatch Metrics, Logs, Alarms và Dashboard.
* Thực hành distributed tracing với AWS X-Ray để phân tích hiệu năng ứng dụng.
