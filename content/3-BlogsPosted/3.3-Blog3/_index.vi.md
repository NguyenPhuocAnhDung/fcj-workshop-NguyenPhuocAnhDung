---
title: "[AWS DevOps #3] Từ ClickOps đến IaC"
date: 2026-07-21
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# [AWS DevOps #3] Từ "ClickOps" đến Infrastructure as Code (IaC): Vì sao làm Cloud thực chiến phải nói KHÔNG với click tay?

> **Link bài viết đã đăng trên Facebook:** [https://www.facebook.com/share/p/14mrD5o7RM2/](https://www.facebook.com/share/p/14mrD5o7RM2/)

Xin chào mọi người!

Khi mới bắt đầu học AWS, 99% chúng ta đều trải qua giai đoạn: Mở AWS Management Console lên và "click tay".
- Click tạo VPC -> Click tạo Subnet -> Click tạo Security Group -> Click bật EC2.

Cách làm này cực kỳ trực quan và giúp người mới dễ hình dung. Nhưng trong môi trường doanh nghiệp thực tế, việc quản lý hệ thống hoàn toàn bằng thao tác thủ công trên giao diện (thường được gọi vui là **ClickOps**) lại ẩn chứa rất nhiều rủi ro lớn.

---

### CÁC HẠN CHẾ CHẾT NGƯỜI CỦA "CLICK-OPS"

1. **Thiếu tính tái lập (Lack of Reproducibility)**  
   Giả sử bạn mất 3 ngày để click tạo xong một môi trường Development. Bây giờ Sếp yêu cầu dựng thêm một môi trường Staging và Production y hệt. Việc ngồi click lại hàng trăm bước thủ công không chỉ tốn thời gian mà còn chắc chắn xảy ra sai sót (Human Error).

2. **Không thể quản lý phiên bản (No Version Control)**  
   Một ngày đẹp trời, hệ thống bị lỗi kết nối Database. Ai đã chỉnh sửa Inbound Rule của Security Group? Sửa lúc nào? Giá trị cũ là gì? Với ClickOps, bạn hoàn toàn không có file `git diff` để biết ai đã thay đổi những gì trên hạ tầng.

3. **Khó khăn trong khôi phục thảm họa (Disaster Recovery)**  
   Nếu một Region gặp sự cố hoặc tài nguyên bị xóa nhầm, việc dựng lại toàn bộ hạ tầng bằng tay trong thời gian ngắn để ứng dụng hoạt động trở lại gần như là điều không thể.

---

### GIẢI PHÁP: INFRASTRUCTURE AS CODE (IaC)

Infrastructure as Code (IaC) là tư duy quản lý và khai báo toàn bộ hạ tầng Đám mây (VPC, EC2, S3, IAM, RDS...) dưới dạng các **file code**. Các công cụ phổ biến nhất hiện nay trên AWS bao gồm: **AWS CloudFormation, Terraform, và AWS CDK**.

**Lợi ích vượt trội mà IaC mang lại:**

1. **Tự động hóa & Đồng nhất 100%**: Chỉ cần chạy một câu lệnh `terraform apply` hoặc `cdk deploy`, toàn bộ mạng, máy chủ, database sẽ được khởi tạo chính xác trong vài phút. Môi trường Dev, Staging hay Prod đều giống nhau 100%.
2. **Quản lý hạ tầng như Quản lý Mã nguồn (Git)**: Hạ tầng của bạn được lưu trong kho Git. Mọi thay đổi đều phải qua quy trình Code Review, Pull Request và có thể Rollback (khôi phục) về phiên bản trước bất kỳ lúc nào nếu xảy ra lỗi.
3. **Tích hợp mượt mà vào CI/CD Pipeline**: Hạ tầng có thể được tự động kiểm tra (Linting/Security Scan) và triển khai tự động mỗi khi có thay đổi trong mã nguồn.

---

### LỜI KHUYÊN CHO NGƯỜI MỚI HỌC AWS

- **Bước 1**: Hãy dùng Console (ClickOps) để hiểu rõ bản chất và mối liên quan giữa các dịch vụ.
- **Bước 2**: Khi đã nắm cơ bản, hãy bắt tay ngay vào học một công cụ IaC (khuyên dùng Terraform hoặc AWS CDK).

Việc dịch chuyển từ "người click Console" sang "người viết code quản lý hạ tầng" chính là bước ngoặt lớn nhất đưa bạn trở thành một Cloud / DevOps Engineer chuyên nghiệp.

Cảm ơn mọi người đã theo dõi bài viết! Bạn đang dùng công cụ IaC nào cho dự án AWS của mình? Hãy chia sẻ trải nghiệm ở bên dưới nhé!

👉 **Link bài đăng trên Facebook:** [Xem bài viết trên Facebook](https://www.facebook.com/share/p/14mrD5o7RM2/)

`#AWS` `#InfrastructureAsCode` `#Terraform` `#AWSCDK` `#DevOps` `#CloudComputing` `#AWSCloudFormation` `#AWSCommunity` `#TechSharing`