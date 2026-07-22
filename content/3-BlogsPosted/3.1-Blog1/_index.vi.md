---
title: "[AWS DevOps #1] Session Policies EKS Pod Identity"
date: 2026-07-21
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# [AWS DevOps #1] Session Policies trong Amazon EKS Pod Identity: Tối ưu hóa phân quyền Least Privilege cho Kubernetes Container

> **Link bài viết đã đăng trên Facebook:** [https://www.facebook.com/share/p/14mL1ERofZM/](https://www.facebook.com/share/p/14mL1ERofZM/)

Xin chào mọi người!

Khi triển khai các ứng dụng container trên Amazon EKS (Elastic Kubernetes Service), việc quản lý quyền truy cập IAM cho từng Pod luôn là một bài toán hóc chuẩn bảo mật. Trước đây, chúng ta thường sử dụng IRSA (IAM Roles for Service Accounts) hoặc cấp quyền rộng cho Worker Node. Tuy nhiên, tính năng **Session Policies trong Amazon EKS Pod Identity** vừa ra mắt đã mang lại một bước tiến vượt bậc giúp thu hẹp quyền IAM linh hoạt và chính xác hơn bao giờ hết.

---

### VÌ SAO EKS POD IDENTITY SESSION POLICIES LẠI QUAN TRỌNG?

Trong môi trường Kubernetes quy mô lớn với hàng trăm Pods chạy cùng lúc, việc tạo riêng mỗi IAM Role cho từng Pod gây ra tình trạng bùng nổ số lượng IAM Roles (Role Sprawl) và dễ chạm giới hạn Quota của AWS.

Giải pháp **Session Policies** cho phép bạn tái sử dụng một IAM Role chung nhưng vẫn đảm bảo mỗi Pod chỉ có đúng các quyền tối thiểu cần thiết để hoạt động (Nguyên tắc **Least Privilege**).

---

### CÁC ĐIỂM KỸ THUẬT CỐT LÕI CẦN NẮM

1. **Cơ chế Phân quyền Giao nhau (Intersection of Permissions)**
 Quyền hạn thực tế của Pod = **Giao (Intersection)** giữa IAM Role Policy và Session Policy.
 *Lưu ý quan trọng*: Session Policy chỉ có thể **thu hẹp** (restrict) quyền chứ không bao giờ có thể mở rộng quyền vượt quá IAM Role gốc.

2. **Tránh over-permissioning khi dùng chung IAM Role**
 Ví dụ: Nhiều Pods dịch vụ cùng dùng chung một IAM Role có quyền truy cập S3, nhưng nhờ Session Policy, Pod A chỉ có thể đọc dữ liệu từ `s3://bucket-a`, còn Pod B chỉ có thể ghi vào `s3://bucket-b`.

3. **Hỗ trợ Đa tài khoản (Cross-Account)**
 Hỗ trợ cấu hình phân quyền mượt mà giữa các tài khoản AWS khác nhau thông qua cơ chế IAM Role Chaining.

4. **Giảm tải quản trị & Tránh chạm Quota IAM**
 Giúp đội ngũ DevOps giảm tới 70% số lượng IAM Roles cần khởi tạo và bảo trì trong cụm EKS Cluster lớn.

---

### LỜI KHUYÊN KHI TRIỂN KHAI TRÊN AMAZON EKS

- **Bước 1**: Xây dựng các IAM Role có phạm vi quyền hợp lý theo nhóm dịch vụ (ví dụ: Database Access Role, Storage Access Role).
- **Bước 2**: Khi tạo hoặc cập nhật Pod Identity Association qua AWS CLI/Console/CDK, đính kèm Session Policy inline để giới hạn phạm vi tài nguyên cho từng Kubernetes ServiceAccount.
- **Bước 3**: Kiểm tra chỉ số kiểm toán log truy cập qua AWS CloudWatch & CloudTrail để đảm bảo Pod hoạt động đúng phân quyền.

Cảm ơn mọi người đã theo dõi bài viết! Cụm EKS của bạn đang dùng cơ chế phân quyền IAM nào? Hãy chia sẻ trải nghiệm ở bên dưới nhé!

 **Link bài đăng trên Facebook:** [Xem bài viết trên Facebook](https://www.facebook.com/share/p/14mL1ERofZM/)

`#AWS` `#AmazonEKS` `#EKS` `#PodIdentity` `#Kubernetes` `#IAM` `#DevOps` `#CloudSecurity` `#AWSCommunity` `#TechSharing`