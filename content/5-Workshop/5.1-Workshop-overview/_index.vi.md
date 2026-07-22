---
title : "Giới thiệu"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Giới thiệu về TSL-SignMap & Kiến trúc AWS

+ Hệ thống **TSL-SignMap** (Dự án FCJ-Workshop-TrungTuan1) là giải pháp quản lý & giám sát biển báo giao thông thời gian thực trên toàn quốc tích hợp cơ chế phần thưởng TSL Coin tự động khi người dùng đóng góp biển báo mới.
+ Hệ thống được xây dựng theo kiến trúc **Microservices** hiện đại bao gồm 11 dịch vụ & thành phần kỹ thuật triển khai trên hạ tầng đám mây **AWS Cloud** (như Amazon S3, CloudFront CDN, Application Load Balancer, ECS Fargate, AWS Cloud Map, RDS for SQL Server, EventBridge và Secrets Manager).

#### Tổng quan về workshop

Trong workshop này, bạn sẽ tìm hiểu và triển khai mô hình kiến trúc hạ tầng AWS hoàn chỉnh cho hệ thống **TSL-SignMap**:
+ **"Frontend & CDN Layer"**: Giao diện React + Vite (`ADMIN.WEB`) được lưu trữ tại **Amazon S3** và phân phối qua **AWS CloudFront CDN** giúp nạp trang siêu tốc.
+ **"API Gateway & Load Balancing"**: Traffic từ người dùng qua **Application Load Balancer (ALB)** điều hướng đến **Ocelot API Gateway Router** chạy trong **AWS ECS Fargate**.
+ **"Microservices Cluster"**: 7 dịch vụ backend .NET Core và 1 tác vụ Python Data Scraper chạy trên cụm Serverless **AWS ECS Fargate**, giao tiếp nội bộ thông qua **AWS Cloud Map DNS**.
+ **"Database Layer"**: Lưu trữ dữ liệu tập trung hơn 1,286+ biển báo giao thông chuẩn GIS `geography` trên **AWS RDS for SQL Server**.

<p align="center">
  <img src="https://raw.githubusercontent.com/NguyenPhuocAnhDung/fcj-workshop-NguyenPhuocAnhDung/main/static/images/5-Workshop/5.1-Workshop-overview/kientrucAWS.jpg" alt="Sơ đồ Kiến trúc AWS TSL-SignMap" style="border-radius: 8px; width: 100%; max-width: 900px; display: block; margin: 15px auto;">
</p>

**Tải tệp sơ đồ kiến trúc Draw.io:**  
📥 <a href="https://raw.githubusercontent.com/NguyenPhuocAnhDung/fcj-workshop-NguyenPhuocAnhDung/main/static/images/5-Workshop/5.1-Workshop-overview/tsl-signmap.aws.drawio" download="tsl-signmap.aws.drawio" target="_blank" style="font-weight: bold; color: #0066cc;">BẤM VÀO ĐÂY ĐỂ TẢI TỆP TSL-SIGNMAP.AWS (DRAW.IO DIAGRAM)</a>  
*(Lưu ý: Bạn cũng có thể **nhấp chuột phải vào link phía trên -> chọn "Lưu liên kết thành..." (Save link as...)** để tải tệp `.drawio` về máy).*


