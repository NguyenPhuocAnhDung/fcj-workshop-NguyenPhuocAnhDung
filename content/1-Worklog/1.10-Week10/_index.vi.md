---
title: "Worklog Tuần 10"
date: 2026-07-07
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:

* Thực hành cấu hình IAM Permission Boundary nhằm giới hạn quyền truy cập cho các nhóm người dùng.
* Nghiên cứu và triển khai hạ tầng dưới dạng mã (IaC) bằng AWS CDK sử dụng TypeScript.
* Thực hiện di chuyển cơ sở dữ liệu từ Amazon RDS MySQL sang Amazon RDS MariaDB bằng AWS DMS.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 3 | - Thực hành IAM Permission Boundary nâng cao:<br>&emsp; + Cấu hình Boundary cho Developer Group<br>&emsp; + Kiểm thử và xác nhận giới hạn quyền hoạt động đúng | 07/07/2026 | 07/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Triển khai hạ tầng bằng AWS CDK (TypeScript):<br>&emsp; + Mở rộng Stack với các Construct tùy chỉnh<br>&emsp; + Quản lý môi trường Dev/Prod bằng CDK Context | 08/07/2026 | 08/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Chuẩn bị môi trường di chuyển cơ sở dữ liệu:<br>&emsp; + Tạo RDS MySQL (Source) và RDS MariaDB (Target)<br>&emsp; + Cấu hình Security Group và Subnet Group | 09/07/2026 | 09/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Thực hiện Database Migration với AWS DMS:<br>&emsp; + Tạo Replication Instance<br>&emsp; + Cấu hình Source & Target Endpoints<br>&emsp; + Chạy Migration Task Full Load + CDC | 10/07/2026 | 10/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 2 | - Kiểm tra tính toàn vẹn dữ liệu sau di chuyển và tổng kết | 13/07/2026 | 13/07/2026 | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 10:

* Cấu hình thành công IAM Permission Boundary cho nhiều nhóm người dùng khác nhau.
* Triển khai hạ tầng phức tạp bằng AWS CDK TypeScript với quản lý đa môi trường.
* Di chuyển thành công cơ sở dữ liệu từ RDS MySQL sang RDS MariaDB bằng AWS DMS.
