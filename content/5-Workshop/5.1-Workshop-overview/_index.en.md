---
title : "Introduction"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Introduction to TSL-SignMap & AWS Architecture

+ **TSL-SignMap** (Project FCJ-Workshop-TrungTuan1) is a real-time traffic sign management & monitoring system for Vietnam, integrating an automated TSL Coin reward mechanism for user contributions.
+ The system is built on a modern **Microservices architecture** consisting of 11 core services and technical components deployed on **AWS Cloud** infrastructure (including Amazon S3, CloudFront CDN, Application Load Balancer, ECS Fargate, AWS Cloud Map, RDS for SQL Server, EventBridge, and Secrets Manager).

#### Workshop overview

In this workshop, you will explore and implement the end-to-end AWS cloud infrastructure for **TSL-SignMap**:
+ **"Frontend & CDN Layer"**: The React + Vite interface (`ADMIN.WEB`) hosted on **Amazon S3** and distributed via **AWS CloudFront CDN** for low latency.
+ **"API Gateway & Load Balancing"**: Traffic from users routes through **Application Load Balancer (ALB)** to the **Ocelot API Gateway Router** running in **AWS ECS Fargate**.
+ **"Microservices Cluster"**: 7 backend .NET Core services and 1 Python Data Scraper task running on serverless **AWS ECS Fargate**, communicating internally via **AWS Cloud Map DNS**.
+ **"Database Layer"**: Centralized storage of 1,286+ traffic signs with spatial `geography` data on **AWS RDS for SQL Server**.

<p align="center">
  <img src="https://raw.githubusercontent.com/NguyenPhuocAnhDung/fcj-workshop-NguyenPhuocAnhDung/main/static/images/5-Workshop/5.1-Workshop-overview/kientrucAWS.jpg" alt="TSL-SignMap AWS Architecture Diagram" style="border-radius: 8px; width: 100%; max-width: 900px; display: block; margin: 15px auto;">
</p>

**Download Draw.io Architecture Diagram:**  
📥 <a href="https://raw.githubusercontent.com/NguyenPhuocAnhDung/fcj-workshop-NguyenPhuocAnhDung/main/static/images/5-Workshop/5.1-Workshop-overview/tsl-signmap.aws.drawio" download="tsl-signmap.aws.drawio" target="_blank" style="font-weight: bold; color: #0066cc;">CLICK HERE TO DOWNLOAD TSL-SIGNMAP.AWS FILE (DRAW.IO DIAGRAM)</a>  
*(Note: You can also **right-click the link above -> select "Save link as..."** to download the `.drawio` file).*
