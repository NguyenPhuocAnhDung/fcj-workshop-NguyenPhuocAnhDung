---
title: "Workshop"
date: 2026-07-22
weight: 5
chapter: false
pre: " <b> 5. </b> "
---
# Deploying TSL-SignMap Microservices on AWS Cloud

#### Overview of Project FCJ-Workshop-TrungTuan1

This workshop provides a step-by-step guide to deploying **TSL-SignMap** - Vietnam Traffic Sign Management & Real-time Monitoring System using **Microservices architecture** on **AWS Cloud** infrastructure.

The system consists of **11 core services & technical components** running on official AWS Cloud services:
+ **Frontend React Web (`ADMIN.WEB`)**: Deployed on **Amazon S3** and distributed via **AWS CloudFront CDN**.
+ **API Gateway & 7 Microservices .NET Core + Python Scraper**: Packaged in Docker Containers running serverless on **AWS ECS Fargate**, routed via **Application Load Balancer (ALB)** and **AWS Cloud Map DNS**.
+ **Database Layer**: **AWS RDS for SQL Server 2022** storing 1,286+ spatial `geography` traffic signs.

#### Lab Modules

1. [Introduction & TSL-SignMap Architecture](5.1-Workshop-overview/)
2. [Prerequisites & IAM Permissions](5.2-Prerequiste/)
3. [Deploying Frontend Web App on S3 & CloudFront CDN](5.3-S3-vpc/)
4. [Deploying Microservices Cluster on ECS Fargate & RDS](5.4-S3-onprem/)
5. [Security Configuration, Secrets Manager & IAM Policies](5.5-Policy/)
6. [Cleaning up AWS Resources](5.6-Cleanup/)