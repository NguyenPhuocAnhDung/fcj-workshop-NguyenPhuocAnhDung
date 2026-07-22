---
title: "Workshop"
date: 2026-07-22
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Triển khai Hệ thống TSL-SignMap Microservices trên AWS Cloud

#### Tổng quan dự án FCJ-Workshop-TrungTuan1

Workshop này hướng dẫn quy trình triển khai toàn diện hệ thống **TSL-SignMap** - Hệ thống Quản lý & Giám sát Biển báo Giao thông Việt Nam thời gian thực theo kiến trúc **Microservices** trên hạ tầng đám mây **AWS Cloud**.

Hệ thống bao gồm **11 Dịch vụ & Thành phần kỹ thuật** vận hành trên các dịch vụ đám mây AWS chính thức:
+ **Frontend React Web (`ADMIN.WEB`)**: Triển khai trên **Amazon S3** và phân phối qua **AWS CloudFront CDN**.
+ **API Gateway & 7 Microservices .NET Core + Python Scraper**: Đóng gói Docker Containers và vận hành Serverless trên **AWS ECS Fargate**, điều hướng qua **Application Load Balancer (ALB)** và **AWS Cloud Map DNS**.
+ **Database Layer**: CSDL **AWS RDS for SQL Server 2022** lưu trữ 1,286+ biển báo GIS `geography`.

#### Nội dung bài lab

1. [Giới thiệu & Kiến trúc TSL-SignMap](5.1-Workshop-overview/)
2. [Các bước chuẩn bị & Phân quyền IAM](5.2-Prerequiste/)
3. [Triển khai Frontend Web trên S3 & CloudFront CDN](5.3-S3-vpc/)
4. [Triển khai Microservices Cluster trên ECS Fargate & RDS](5.4-S3-onprem/)
5. [Cấu hình Bảo mật, Secrets Manager & IAM Policies](5.5-Policy/)
6. [Dọn dẹp tài nguyên trên AWS Cloud](5.6-Cleanup/)
