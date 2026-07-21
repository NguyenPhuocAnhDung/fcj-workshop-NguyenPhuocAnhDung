---
title: "Proposal"
date: 2026-07-21
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# TSL-SignMap — Smart Traffic Sign Map & AI Platform
## Unified AWS Serverless & Microservices Solution for Smart Traffic Sign Management

### 1. Executive Summary
**TSL-SignMap** is a crowdsourced smart traffic sign management and mapping system integrated with Artificial Intelligence (AI Computer Vision - YOLO). The system empowers drivers and commuters to receive real-time traffic sign updates, location mapping, and safety alerts directly on mobile devices.

The solution leverages **Microservices Architecture** combined with **AWS Cloud Infrastructure & Serverless** (Amazon EKS/ECS Fargate, AWS API Gateway, Amazon S3 Data Lake, AWS Lambda, Amazon SageMaker, Amazon RDS, ElastiCache Redis, Amazon Cognito) to ensure seamless scalability, real-time AI processing, and enterprise-grade security for tens of thousands of active users.

---

### 2. Problem Statement & Solution

#### Problem Statement
- **Outdated & Inaccurate Signage Data**: Urban traffic infrastructure changes rapidly (new signs, damaged signs, obscured signs), making manual municipal updates slow and costly.
- **Traffic Safety Hazards**: Commuters lack real-time warnings regarding hazardous zones, speed limits, and restricted roads.
- **Monolithic Scalability Bottlenecks**: Traditional mapping software struggles under sudden traffic spikes and heavy AI image processing workloads.

#### The TSL-SignMap Solution
- **Crowdsourcing & AI Detection**: Enables users to capture sign photos/videos via a Flutter Mobile App. The YOLO AI model automatically detects, classifies, and geocodes traffic signs onto an interactive map (OpenStreetMap / Mapbox).
- **Community Verification (Voting Service)**: Community members participate in upvoting/downvoting submissions to verify accuracy before official map publishing.
- **AWS Microservices Architecture**: Decouples business logic into independent services (TrafficSign, User, Voting, Payment, Notification, Feedback) routed through an API Gateway and containerized on AWS EKS/ECS Fargate.

#### ROI & Value Proposition
- Delivers high-precision traffic data for AI research and smart transportation initiatives.
- Serverless & Microservices infrastructure auto-scales dynamically, lowering operational costs by 40–60% compared to traditional on-premise servers.

---

### 3. Architecture & Core AWS Services

The architecture follows an **Event-Driven Microservices** pattern hosted on AWS Cloud:

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

#### Core AWS Services Used:
1. **Amazon EKS / ECS Fargate**: Manages containerized microservices (Docker) with automated horizontal scaling.
2. **AWS API Gateway / ALB**: Handles request routing, SSL termination, and load balancing for incoming mobile traffic.
3. **Amazon S3 (Simple Storage Service)**: Serves as Data Lake storage for raw sign images/videos, labeled datasets, and AI model weights.
4. **AWS Lambda**: Serverless event handlers triggered upon image uploads to invoke AI inference asynchronously.
5. **Amazon SageMaker**: Trains and hosts inference endpoints for the YOLO computer vision model.
6. **Amazon RDS (PostgreSQL / SQL Server)**: Relational databases storing user accounts, contributions, votes, and payment records.
7. **Amazon ElastiCache (Redis)**: Caches geospatial traffic sign queries, reducing API latency to < 50ms.
8. **Amazon Cognito & AWS IAM**: Provides secure user authentication (JWT Tokens) and role-based access control.
9. **AWS CloudWatch & X-Ray**: Enables centralized logging, performance metrics, and distributed tracing across microservices.
10. **AWS CDK (TypeScript)**: Defines and provisions all AWS infrastructure as code (IaC).

---

### 4. Microservices Specification

| Microservice | Port | Core Responsibilities | AWS & Database Integrations |
| :--- | :--- | :--- | :--- |
| **API Gateway** | `5000 / 7000` | Request routing, authentication middleware, rate limiting | AWS API Gateway / YARP |
| **TrafficSignService** | `5003 / 7003` | Traffic sign CRUD, GPS geocoding, S3 uploads & AI YOLO invocation | Amazon S3, Lambda, SageMaker, RDS |
| **UserService** | `5001 / 7001` | Account management, role authorization (User/Mod/Admin), Wallet/Coins | Amazon Cognito, RDS, ElastiCache |
| **VotingService** | `5004 / 7004` | Community verification (Upvote/Downvote logic & weight calculation) | Amazon RDS PostgreSQL |
| **PaymentService** | `5006 / 7006` | Handles coin top-ups, reward points, and transaction history | Amazon RDS |
| **NotificationService**| `5005 / 7005` | Real-time push notifications via SignalR Hub when contributions are approved | AWS SNS, SignalR Hub |
| **FeedbackService** | `5007 / 7007` | User feedback submission, issue reporting, and admin management | Amazon RDS |
| **Mobile App (Flutter)**| App Client | Cross-platform mobile UI, OpenStreetMap/Mapbox navigation, AI camera capture | AWS Mobile SDK, Amplify |

---

### 5. Implementation Roadmap & Milestones

- **Phase 1: Architecture & AI Research (Month 1)**
  - Requirements analysis, Microservices schema design, and dataset annotation.
  - Train baseline YOLO model for traffic sign detection.
- **Phase 2: Microservices & Mobile App Development (Month 2)**
  - Develop .NET 8 Web API microservices and Flutter mobile client.
  - Integrate S3, Lambda, SageMaker inference, and API Gateway.
- **Phase 3: IaC Automation with AWS CDK & CI/CD (Month 3)**
  - Write AWS CDK (TypeScript) scripts for automated cloud provisioning.
  - Setup CI/CD pipelines (GitHub Actions / AWS CodePipeline) for container deployment to ECS Fargate.
- **Phase 4: Load Testing, Optimization & Operations (Month 4)**
  - Execute stress testing, optimize ElastiCache Redis, and perform Security Hub audit.

---

### 6. Infrastructure Budget Estimation

Estimated monthly cost based on **AWS Pricing Calculator** for 10,000 daily active users:

- **Amazon ECS Fargate (2 Tasks)**: ~ $15.00 / month
- **Amazon RDS PostgreSQL (db.t4g.micro)**: ~ $14.50 / month
- **Amazon S3 (Data Lake 50GB + Transfers)**: ~ $2.50 / month
- **AWS Lambda & API Gateway (500k requests)**: ~ $1.20 / month
- **Amazon ElastiCache Redis (cache.t4g.micro)**: ~ $12.00 / month
- **Amazon Cognito & CloudWatch**: ~ $2.00 / month
- **Total Estimated Cost**: **~ $47.20 / month** (~ $566 / year)

---

### 7. Risk Evaluation & Mitigation Strategy

- **Risk 1: High AI processing workload causing API lag**  
  *Mitigation*: Use S3 Presigned URLs for direct mobile uploads, coupled with AWS Lambda async processing via SQS queues.
- **Risk 2: Spam or inaccurate user submissions**  
  *Mitigation*: Implement reputation-weighted voting algorithms in VotingService.
- **Risk 3: Cloud budget overruns**  
  *Mitigation*: Configure AWS Budgets alerts to trigger notifications at 80% threshold.

---

### 8. Expected Outcomes
- Successfully deploy a real-time smart traffic sign mapping platform on AWS Cloud.
- Achieve 100% Infrastructure as Code automation using AWS CDK and CI/CD pipelines.
- Ensure high availability, low latency, and cost-optimized operations.