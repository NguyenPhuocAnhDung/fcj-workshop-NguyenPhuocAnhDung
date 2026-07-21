---
title: "Event 1"
date: 2026-06-06
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài thu hoạch “GenAI-powered App-DB Modernization workshop”

### Mục Đích Của Sự Kiện

- Chia sẻ best practices trong thiết kế ứng dụng hiện đại
- Giới thiệu phương pháp DDD và event-driven architecture
- Hướng dẫn lựa chọn compute services phù hợp
- Giới thiệu công cụ AI hỗ trợ development lifecycle

### Thời Gian & Địa Điểm

- **Thời gian:** 09:00, Ngày 06/06/2026
- **Địa điểm:** Tầng 26, Tòa nhà Bitexco, Số 02 Đường Hải Triều, Phường Sài Gòn, TP. Hồ Chí Minh
- **Vai trò:** Người tham dự

### Danh Sách Diễn Giả

- **Jignesh Shah** - Director, Open Source Databases
- **Erica Liu** - Sr. GTM Specialist, AppMod
- **Fabrianne Effendi** - Assc. Specialist SA, Serverless Amazon Web Services

### Nội Dung Nổi Bật

#### Đưa ra các ảnh hưởng tiêu cực của kiến trúc ứng dụng cũ

- Thời gian release sản phẩm lâu → Mất doanh thu/bỏ lỡ cơ hội
- Hoạt động kém hiệu quả → Mất năng suất, tốn kém chi phí
- Không tuân thủ các quy định về bảo mật → Mất an ninh, uy tín

#### Chuyển đổi sang kiến trúc ứng dụng mới - Microservice Architecture

Chuyển đổi thành hệ thống modular – từng chức năng là một **dịch vụ độc lập** giao tiếp với nhau qua **sự kiện** với 3 trụ cột cốt lõi:

- **Queue Management**: Xử lý tác vụ bất đồng bộ
- **Caching Strategy:** Tối ưu performance
- **Message Handling:** Giao tiếp linh hoạt giữa services

#### Domain-Driven Design (DDD)

- **Phương pháp 4 bước**: Xác định domain events → sắp xếp timeline → identify actors → xác định bounded contexts
- **Case study bookstore**: Minh họa cách áp dụng DDD thực tế
- **Context mapping**: 7 patterns tích hợp bounded contexts

#### Event-Driven Architecture

- **3 patterns tích hợp**: Publish/Subscribe, Point-to-point, Streaming
- **Lợi ích**: Loose coupling, scalability, resilience
- **So sánh sync vs async**: Hiểu rõ trade-offs (sự đánh đổi)

#### Compute Evolution

- **Shared Responsibility Model**: Từ EC2 → ECS → Fargate → Lambda
- **Serverless benefits**: No server management, auto-scaling, pay-for-value
- **Functions vs Containers**: Criteria lựa chọn phù hợp

#### Amazon Q Developer

- **SDLC automation**: Từ planning đến maintenance
- **Code transformation**: Java upgrade, .NET modernization
- **AWS Transform agents**: VMware, Mainframe, .NET migration

### Những Gì Học Được

#### Tư Duy Thiết Kế

- **Business-first approach**: Luôn bắt đầu từ business domain, không phải technology
- **Ubiquitous language**: Importance của common vocabulary giữa business và tech teams
- **Bounded contexts**: Cách identify và manage complexity trong large systems

#### Kiến Trúc Kỹ Thuật

- **Event storming technique**: Phương pháp thực tế để mô hình hóa quy trình kinh doanh
- Sử dụng **Event-driven communication** thay vì synchronous calls
- **Integration patterns**: Hiểu khi nào dùng sync, async, pub/sub, streaming
- **Compute spectrum**: Criteria chọn từ VM → containers → serverless

#### Chiến Lược Hiện Đại Hóa

- **Phased approach**: Không rush, phải có roadmap rõ ràng
- **7Rs framework**: Nhiều con đường khác nhau tùy thuộc vào đặc điểm của mỗi ứng dụng
- **ROI measurement**: Cost reduction + business agility

### Ứng Dụng Vào Công Việc

- **Áp dụng DDD** cho project hiện tại: Event storming sessions với business team
- **Refactor microservices**: Sử dụng bounded contexts để identify service boundaries
- **Implement event-driven patterns**: Thay thế một số sync calls bằng async messaging
- **Serverless adoption**: Pilot AWS Lambda cho một số use cases phù hợp
- **Try Amazon Q Developer**: Integrate vào development workflow để boost productivity

### Trải nghiệm trong event

Tham gia workshop **“GenAI-powered App-DB Modernization”** vào ngày 06/06/2026 là một trải nghiệm rất bổ ích, giúp tôi có cái nhìn toàn diện về cách hiện đại hóa ứng dụng và cơ sở dữ liệu bằng các phương pháp và công cụ hiện đại. Một số trải nghiệm nổi bật:

#### Học hỏi từ các diễn giả có chuyên môn cao
- Các diễn giả đến từ AWS và các tổ chức công nghệ lớn đã chia sẻ **best practices** trong thiết kế ứng dụng hiện đại.
- Qua các case study thực tế, tôi hiểu rõ hơn cách áp dụng **Domain-Driven Design (DDD)** và **Event-Driven Architecture** vào các project lớn.

#### Trải nghiệm kỹ thuật thực tế
- Tham gia các phiên trình bày về **event storming** giúp tôi hình dung cách **mô hình hóa quy trình kinh doanh** thành các domain events.
- Học cách **phân tách microservices** và xác định **bounded contexts** để quản lý sự phức tạp của hệ thống lớn.
- Hiểu rõ trade-offs giữa **synchronous và asynchronous communication** cũng như các pattern tích hợp như **pub/sub, point-to-point, streaming**.

#### Ứng dụng công cụ hiện đại
- Trực tiếp tìm hiểu về **Amazon Q Developer**, công cụ AI hỗ trợ SDLC từ lập kế hoạch đến maintenance.
- Học cách **tự động hóa code transformation** và pilot serverless với **AWS Lambda**, từ đó nâng cao năng suất phát triển.

#### Minh chứng Video khi tham gia sự kiện

Dưới đây là video minh chứng ghi lại trải nghiệm tham gia sự kiện Event 1 vào ngày **06/06/2026**:

<video controls width="100%" style="border-radius: 8px; margin-top: 15px; max-height: 480px;">
  <source src="/images/4-EventParticipated/event1_video.mp4" type="video/mp4">
  <source src="/images/4-EventParticipated/event1_proof.mp4" type="video/mp4">
  Trình duyệt của bạn không hỗ trợ xem video minh chứng.
</video>

> Tổng thể, sự kiện không chỉ cung cấp kiến thức kỹ thuật mà còn giúp tôi thay đổi cách tư tư duy về thiết kế ứng dụng, hiện đại hóa hệ thống và phối hợp hiệu quả hơn giữa các team.
