---
title: "Bản đề xuất"
date: 2026-07-21
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# TSL-SignMap — Smart Traffic Sign Map & AI Platform
## Giải pháp Điện toán Đám mây AWS Serverless & Microservices cho Hệ thống Bản đồ Biển báo Giao thông Thông minh

### 1. Tóm tắt điều hành (Executive Summary)
**TSL-SignMap** là hệ thống quản lý và bản đồ hóa biển báo giao thông thông minh dựa trên dữ liệu cộng đồng (Crowdsourcing) tích hợp công nghệ Trí tuệ Nhân tạo (AI Computer Vision - YOLO). Hệ thống giúp người lái xe và người tham gia giao thông cập nhật vị trí, trạng thái biển báo theo thời gian thực trên bản đồ số, đồng thời nhận cảnh báo an toàn giao thông khi di chuyển.

Giải pháp tận dụng kiến trúc **Microservices** kết hợp **AWS Cloud Infrastructure & Serverless** (Amazon EKS/ECS Fargate, AWS API Gateway, Amazon S3 Data Lake, AWS Lambda, Amazon SageMaker, Amazon RDS, ElastiCache Redis, Amazon Cognito) để cung cấp khả năng mở rộng linh hoạt, xử lý dữ liệu AI theo thời gian thực và đảm bảo tính an toàn bảo mật cao cho hàng chục nghìn người dùng.

---

### 2. Tuyên bố vấn đề & Giải pháp (Problem Statement & Solution)

#### Vấn đề hiện tại
- **Dữ liệu biển báo thiếu cập nhật & sai lệch**: Hệ thống giao thông đô thị liên tục thay đổi (biển báo mới, biển bị che khuất, hỏng hóc), nhưng việc cập nhật của cơ quan quản lý thủ công tốn nhiều thời gian.
- **Nguy cơ mất an toàn giao thông**: Người lái xe thiếu thông tin cảnh báo sớm về các biển báo khu vực nguy hiểm, hạn chế tốc độ, đường cấm.
- **Hệ thống đơn khối (Monolith) khó mở rộng**: Các ứng dụng bản đồ truyền thống gặp khó khăn khi tăng đột biến lưu lượng người dùng và khối lượng dữ liệu hình ảnh AI lớn.

#### Giải pháp TSL-SignMap
- **Crowdsourcing & AI Detection**: Cho phép người dùng chụp ảnh/video biển báo qua Mobile App (Flutter). Mô hình AI YOLO tự động phát hiện, phân loại biển báo và gắn tọa độ GPS lên bản đồ số (OpenStreetMap / Mapbox).
- **Hệ thống Xác minh Cộng đồng (Voting Service)**: Cộng đồng cùng tham gia bình chọn (Upvote/Downvote) để xác minh tính chính xác của dữ liệu biển báo trước khi cập nhật chính thức.
- **Kiến trúc Microservices trên AWS**: Phân tách hệ thống thành các dịch vụ độc lập (TrafficSign, User, Voting, Payment, Notification, Feedback) được quản lý qua API Gateway và chạy containerized trên AWS EKS/ECS Fargate.

#### Lợi ích & Hoàn vốn đầu tư (ROI)
- Cung cấp nguồn dữ liệu biển báo chính xác, phục vụ nghiên cứu AI và hỗ trợ giao thông thông minh.
- Hệ thống Serverless & Microservices giúp tự động co giãn tài nguyên theo tải thực tế, tối ưu chi phí vận hành từ 40–60% so với máy chủ truyền thống.

---

### 3. Kiến trúc Giải pháp & Các Dịch vụ AWS Sử dụng (Architecture & AWS Services)

Hệ thống được thiết kế theo mô hình **Microservices Event-Driven** trên đám mây AWS:

```
[Mobile App (Flutter)] 
       │ (HTTPS / SignalR)
       ▼
[AWS API Gateway / YARP Router]
       │
 ┌─────┼──────────────┬──────────────┬──────────────┬──────────────┐
 ▼     ▼              ▼              ▼              ▼              ▼
[User] [TrafficSign]  [Voting]       [Payment]      [Notification] [Feedback]
(RDS)  (S3 / Lambda)  (RDS)          (RDS)          (SignalR Hub)  (RDS)
       └──────┬───────┘
              ▼
   [Amazon SageMaker / YOLO] ──► [Amazon ElastiCache Redis]
```

#### Các Dịch vụ AWS Cốt lõi Sử dụng:
1. **Amazon EKS / ECS Fargate**: Triển khai và quản lý các Microservices dưới dạng Container (Docker) với khả năng Auto-scaling.
2. **AWS API Gateway / ALB**: Cân bằng tải và điều hướng toàn bộ Yêu cầu (Request) từ Mobile App tới các Microservices nội bộ.
3. **Amazon S3 (Simple Storage Service)**: Lưu trữ Data Lake chứa hình ảnh/video biển báo thô, dữ liệu đã gắn nhãn và file huấn luyện mô hình AI.
4. **AWS Lambda**: Hàm Serverless tự động xử lý sự kiện (kích hoạt khi có hình ảnh mới upload lên S3, gọi AI Inference).
5. **Amazon SageMaker**: Huấn luyện (Training) và triển khai Endpoint suy luận (Inference) cho mô hình AI YOLO phát hiện biển báo.
6. **Amazon RDS (PostgreSQL / SQL Server)**: Cơ sở dữ liệu quan hệ lưu trữ thông tin người dùng, đóng góp, lịch sử giao dịch và phản hồi.
7. **Amazon ElastiCache (Redis)**: Caching dữ liệu vị trí biển báo và kết quả truy vấn bản đồ, giúp giảm độ trễ response xuống < 50ms.
8. **Amazon Cognito & AWS IAM**: Xác thực người dùng (JWT Token) và phân quyền bảo mật truy cập hạ tầng.
9. **AWS CloudWatch & X-Ray**: Giám sát nhật ký (Logging), chỉ số hiệu năng (Metrics) và truy vết phân tán (Distributed Tracing).
10. **AWS CDK (TypeScript)**: Định nghĩa và tự động hóa toàn bộ Hạ tầng dưới dạng Mã (Infrastructure as Code - IaC).

---

### 4. Chi tiết các Microservices Nội bộ (Microservices Specification)

| Microservice | Cổng (Port) | Chức năng chính | Dịch vụ AWS & DB liên kết |
| :--- | :--- | :--- | :--- |
| **API Gateway** | `5000 / 7000` | Điều hướng Request, Authentication middleware, Rate limiting | AWS API Gateway / YARP |
| **TrafficSignService** | `5003 / 7003` | Quản lý dữ liệu biển báo, gắn tọa độ GPS, xử lý upload ảnh & gọi AI YOLO nhận diện | Amazon S3, Lambda, SageMaker, RDS |
| **UserService** | `5001 / 7001` | Quản lý tài khoản, phân quyền (User/Mod/Admin), quản lý Ví Coins thưởng | Amazon Cognito, RDS, ElastiCache |
| **VotingService** | `5004 / 7004` | Quản lý bình chọn cộng đồng (Upvote/Downvote) để xác minh thông tin biển báo | Amazon RDS PostgreSQL |
| **PaymentService** | `5006 / 7006` | Xử lý giao dịch nạp coin, thưởng điểm đóng góp cho người dùng | Amazon RDS |
| **NotificationService**| `5005 / 7005` | Gửi thông báo thời gian thực (Real-time SignalR Hub) khi báo cáo được duyệt | AWS SNS, SignalR Hub |
| **FeedbackService** | `5007 / 7007` | Quản lý phản hồi, báo cáo sự cố ứng dụng và dữ liệu biển báo từ người dùng | Amazon RDS |
| **Mobile App (Flutter)**| App Client | Giao diện di động, bản đồ OpenStreetMap/Mapbox, camera chụp ảnh AI, cảnh báo giọng nói | AWS Mobile SDK, Amplify |

---

### 5. Lộ trình Triển khai & Các Mốc chính (Roadmap & Milestones)

- **Giai đoạn 1: Nghiên cứu & Thiết kế Kiến trúc (Tháng 1)**
  - Phân tích yêu cầu hệ thống, vẽ sơ đồ kiến trúc Microservices và thiết kế cơ sở dữ liệu.
  - Xây dựng mô hình AI YOLO nhận diện biển báo giao thông Việt Nam.
- **Giai đoạn 2: Lập trình Microservices & Mobile App (Tháng 2)**
  - Lập trình các dịch vụ Backend bằng .NET 8 Web API và Mobile App bằng Flutter.
  - Tích hợp AWS S3, Lambda, Rekognition/SageMaker và API Gateway.
- **Giai đoạn 3: Tự động hóa Hạ tầng bằng AWS CDK & CI/CD (Tháng 3)**
  - Viết kịch bản AWS CDK (TypeScript) để khởi tạo toàn bộ hạ tầng AWS.
  - Xây dựng CI/CD Pipeline (GitHub Actions / AWS CodePipeline) tự động test và deploy lên ECS Fargate.
- **Giai đoạn 4: Kiểm thử, Tối ưu & Đưa vào Vận hành (Tháng 4)**
  - Kiểm thử tải (Load Testing), tối ưu bộ nhớ đệm ElastiCache Redis và đánh giá bảo mật Security Hub.

---

### 6. Ước tính Ngân sách Hạ tầng AWS (Budget Estimation)

Dựa trên công cụ **AWS Pricing Calculator** cho hệ thống quy mô 10.000 người dùng hàng ngày:

- **Amazon ECS Fargate (2 Tasks)**: ~ 15.00 USD/tháng
- **Amazon RDS PostgreSQL (db.t4g.micro)**: ~ 14.50 USD/tháng
- **Amazon S3 (Data Lake 50GB + Transfers)**: ~ 2.50 USD/tháng
- **AWS Lambda & API Gateway (500k requests)**: ~ 1.20 USD/tháng
- **Amazon ElastiCache Redis (cache.t4g.micro)**: ~ 12.00 USD/tháng
- **Amazon Cognito & CloudWatch**: ~ 2.00 USD/tháng
- **Tổng chi phí ước tính**: **~ 47.20 USD / tháng** (~ 566 USD / năm)

---

### 7. Đánh giá Rủi ro & Chiến lược Giảm thiểu (Risk Matrix & Mitigation)

- **Rủi ro 1: Tải xử lý ảnh AI tăng đột biến gây trễ hệ thống**  
  *Giảm thiểu*: Sử dụng AWS S3 Presigned URL để upload trực tiếp từ Mobile, kết hợp AWS Lambda xử lý bất đồng bộ qua hàng đợi Amazon SQS.
- **Rủi ro 2: Dữ liệu đóng góp sai lệch từ người dùng**  
  *Giảm thiểu*: Áp dụng thuật toán tính trọng số bình chọn (Voting Weight) dựa trên uy tín tài khoản trong VotingService.
- **Rủi ro 3: Vượt ngân sách Đám mây**  
  *Giảm thiểu*: Thiết lập AWS Budgets gửi cảnh báo qua Email/SMS khi chi phí chạm 80% hạn mức.

---

### 8. Kết quả Kỳ vọng (Expected Outcomes)
- Xây dựng thành công hệ thống bản đồ biển báo giao thông thông minh thời gian thực trên AWS Cloud.
- Tự động hóa 100% quy trình triển khai hạ tầng với AWS CDK và CI/CD.
- Sẵn sàng mở rộng hệ thống đáp ứng lượng người dùng lớn với chi phí vận hành tối ưu nhất.