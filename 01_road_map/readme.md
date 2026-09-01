
# Phase 0 — Cloud Fundamentals

### ⏱️ 1 week

Before jumping deeply into AWS, understand these concepts:

* What is Cloud Computing?
* IaaS vs PaaS vs SaaS
* Region
* Availability Zone
* Scalability
* Elasticity
* High Availability
* Fault Tolerance
* Disaster Recovery
* Load Balancing
* Horizontal vs Vertical Scaling
* Stateless vs Stateful applications

### Important concept

Understand this architecture:

```text
                Internet
                   |
                Route 53
                   |
               CloudFront
                   |
             Load Balancer
              /         \
           EC2          EC2
            |             |
            +------ ------+
                   |
                 RDS
                   |
                  S3
```

Don't worry if this doesn't make complete sense yet. You'll build it piece by piece.

---

# Phase 1 — AWS Core Services

### ⏱️ 2 weeks

Start with these services.

### 1. IAM ⭐⭐⭐⭐⭐

Learn:

* Users
* Groups
* Roles
* Policies
* Permissions
* MFA
* Access keys
* Least privilege
* IAM role vs IAM user

**Very important:** Don't use the root account for normal development.

---

### 2. S3 ⭐⭐⭐⭐⭐

Learn:

* Bucket
* Object
* Bucket policy
* IAM policy
* Versioning
* Lifecycle rules
* Encryption
* Static website hosting
* Pre-signed URLs

### Mini project

Build:

> Upload profile pictures from your backend to S3.

---

### 3. EC2 ⭐⭐⭐⭐⭐

Learn:

* AMI
* Instance types
* Key pairs
* Security groups
* EBS
* Public/private IP
* User data
* SSH
* Instance lifecycle
* Auto Scaling basics

### Mini project

Deploy your existing backend application to EC2.

This is where your software-development experience becomes very useful.

---

# Phase 2 — Networking

### ⏱️ 2–3 weeks

This is probably the **most important AWS topic after IAM**.

Learn:

### VPC

```text
                    VPC
                     |
          +----------+----------+
          |                     |
     Public Subnet         Private Subnet
          |                     |
       EC2/LB                 RDS
          |
      Internet
       Gateway
```

Learn:

* VPC
* CIDR
* Subnets
* Public subnet
* Private subnet
* Route tables
* Internet Gateway
* NAT Gateway
* Security Groups
* Network ACL
* Elastic IP
* VPC endpoints
* DNS

### You should be able to explain:

> Why shouldn't my database be directly accessible from the internet?

and

> How does a private EC2 instance access the internet?

If you can explain those clearly, your networking foundation is becoming strong.

---

# Phase 3 — Databases

### ⏱️ 1–2 weeks

Since you're already a developer, don't spend too much time learning database fundamentals.

Focus on AWS database services.

## RDS ⭐⭐⭐⭐⭐

Learn:

* PostgreSQL/MySQL on RDS
* Automated backups
* Snapshots
* Multi-AZ
* Read replicas
* Parameter groups
* Security groups
* Encryption

Understand:

```text
Application
     |
     ↓
EC2 / ECS
     |
     ↓
Private Subnet
     |
     ↓
RDS PostgreSQL
```

Then learn:

## DynamoDB

Understand:

* NoSQL
* Partition key
* Sort key
* Query
* Scan
* GSI
* LSI
* DynamoDB Streams
* Capacity modes

Don't try to master DynamoDB before understanding relational databases well.

---

# Phase 4 — Load Balancing & Scaling

### ⏱️ 1 week

Learn:

## Elastic Load Balancer

Especially:

* Application Load Balancer
* Target Groups
* Health checks
* Listener
* Listener rules

Then:

## Auto Scaling

Understand:

```text
                 ALB
              /   |   \
             /    |    \
           EC2   EC2   EC2
             \    |    /
              Auto Scaling
```

Learn:

* Launch templates
* Auto Scaling groups
* Scaling policies
* Health checks

### Mini project

Deploy your backend to **multiple EC2 instances behind an ALB**.

---

# Phase 5 — AWS Developer Services

### ⏱️ 2–3 weeks

Now start learning services that make you a strong AWS developer.

## Lambda ⭐⭐⭐⭐⭐

Learn:

* Function
* Runtime
* Handler
* Environment variables
* IAM execution role
* Layers
* Timeout
* Memory
* Concurrency

---

## API Gateway

Learn:

* REST API
* HTTP API
* Routes
* Stages
* Authorization
* Integration with Lambda

Architecture:

```text
Client
   |
   ↓
API Gateway
   |
   ↓
Lambda
   |
   ↓
DynamoDB
```

---

## SQS ⭐⭐⭐⭐⭐

Very important for backend developers.

Understand:

```text
Order API
    |
    ↓
   SQS
    |
    ↓
Worker
    |
    ↓
Database
```

Learn:

* Queue
* Producer
* Consumer
* Visibility timeout
* Dead-letter queue
* Long polling
* FIFO queue

---

## SNS

Learn:

* Pub/Sub
* Topics
* Subscribers
* Fan-out

Understand the difference:

**SQS = queue**

**SNS = notification/pub-sub**

---

# Phase 6 — Containers

### ⏱️ 2 weeks

This is especially important if you're a modern backend developer.

Learn:

### Docker first

You should be comfortable with:

```text
Dockerfile
Image
Container
Registry
Port mapping
Environment variables
Volumes
Networks
```

Then AWS:

## ECR

Container image registry.

## ECS

Learn:

* Cluster
* Task
* Task definition
* Service
* Container
* Fargate
* ECS + ALB

Architecture:

```text
                  ALB
                   |
             ECS Service
             /         \
        Container    Container
             \         /
                ECR
                  |
             Docker Image
```

### Priority

**Docker → ECR → ECS → Fargate**

You don't need to jump into Kubernetes immediately.

---

# Phase 7 — CI/CD

### ⏱️ 1–2 weeks

This is where you start becoming a **Cloud/DevOps-capable developer**.

Learn:

* Git
* GitHub Actions
* AWS CodePipeline basics
* CodeBuild basics
* CodeDeploy basics

A typical pipeline:

```text
Developer
   |
   ↓
Git Push
   |
   ↓
GitHub
   |
   ↓
CI/CD
   |
   ↓
Docker Build
   |
   ↓
ECR
   |
   ↓
ECS
   |
   ↓
Production
```

Your goal should be:

> `git push` → application automatically deployed to AWS.

---

# Phase 8 — Monitoring & Logging

### ⏱️ 1 week

Learn:

## CloudWatch ⭐⭐⭐⭐⭐

* Logs
* Metrics
* Alarms
* Dashboards
* Log groups
* Log streams

Also understand:

* CloudTrail
* AWS X-Ray basics

You should know how to answer:

> My API is returning 500 errors in production. How do I investigate?

---

# Phase 9 — Security

### ⏱️ 1–2 weeks

Now go deeper into AWS security.

Learn:

* IAM
* IAM roles
* KMS
* Secrets Manager
* Parameter Store
* Encryption
* Security Groups
* VPC security
* CloudTrail
* WAF basics
* GuardDuty basics

Very important:

**Never put database passwords/API keys directly into your Git repository.**

Learn:

```text
Application
     |
     ↓
Secrets Manager
     |
     ↓
Database credentials
```

---

# Phase 10 — DNS, CDN & Static Applications

### ⏱️ 1 week

Learn:

## Route 53

* Hosted zones
* DNS records
* A record
* CNAME
* Alias
* Routing policies

## CloudFront

Learn:

* CDN
* Cache
* Origins
* Behaviors
* HTTPS
* CloudFront + S3
* CloudFront + ALB

Typical architecture:

```text
             User
               |
               ↓
           Route 53
               |
               ↓
          CloudFront
           /       \
          /         \
       S3           ALB
                     |
                   ECS
```

---

# Phase 11 — Advanced AWS Architecture

### ⏱️ 3–4 weeks

Only after completing the previous phases.

Learn:

### ElastiCache

* Redis
* Caching
* Session storage

### EventBridge

* Event-driven architecture
* Event buses
* Rules
* Targets

### Step Functions

* Workflow orchestration

### Kinesis

* Streaming

### CloudFormation / CDK / Terraform

I recommend learning **Terraform** after you understand AWS manually.

---

# 🏗️ Your Projects

Don't just watch AWS courses.

Build projects.

## Project 1 — Simple Deployment

Build:

```text
Frontend
   |
   ↓
S3 + CloudFront

Backend
   |
   ↓
EC2

Database
   |
   ↓
RDS
```

---

## Project 2 — Production-style Backend

Build:

```text
Route 53
    |
CloudFront
    |
   ALB
    |
 ECS/Fargate
    |
 RDS
```

Add:

* IAM
* Secrets Manager
* CloudWatch
* S3

---

## Project 3 — Event-driven Application

For example, an **order processing system**:

```text
              API
               |
               ↓
            Lambda
               |
               ↓
              SQS
               |
               ↓
            Worker
               |
          +----+----+
          |         |
         RDS       S3
```

Add SNS notifications.

This project will teach you much more than watching 50 hours of videos.

---

# 📚 The Order I Recommend

Don't learn AWS randomly.

Follow this sequence:

```text
1. Cloud Fundamentals
        ↓
2. IAM
        ↓
3. S3
        ↓
4. EC2
        ↓
5. VPC
        ↓
6. RDS
        ↓
7. Load Balancer
        ↓
8. Auto Scaling
        ↓
9. Lambda
        ↓
10. API Gateway
        ↓
11. SQS + SNS
        ↓
12. Docker
        ↓
13. ECR
        ↓
14. ECS + Fargate
        ↓
15. CloudWatch
        ↓
16. Route 53 + CloudFront
        ↓
17. Security
        ↓
18. CI/CD
        ↓
19. Terraform
        ↓
20. Advanced Architecture
```

---

# ⏰ 4-Month Study Plan

If you can study **1.5–2 hours/day**, I'd structure it like this:

| Month       | Focus                                                      |
| ----------- | ---------------------------------------------------------- |
| **Month 1** | IAM, S3, EC2, VPC, Networking                              |
| **Month 2** | RDS, ALB, Auto Scaling, Lambda, API Gateway                |
| **Month 3** | SQS, SNS, Docker, ECR, ECS/Fargate, CloudWatch             |
| **Month 4** | CI/CD, Security, Route53, CloudFront, Terraform + projects |

### Your weekly routine

Don't do:

> 2 hours watching AWS videos ❌

Instead:

**30 min** — Learn theory
**30 min** — Follow hands-on example
**45 min** — Build yourself
**15 min** — Write notes / review

That's much more effective for someone with development experience.

---

# 🎯 Certifications

Don't make certification your primary goal.

For your background, I'd eventually target:

### First

**AWS Certified Solutions Architect – Associate (SAA-C03)**

This gives you a strong understanding of AWS architecture.

### Then, depending on your career

**Developer path:**

AWS Certified Developer – Associate

**DevOps path:**

AWS Certified DevOps Engineer – Professional

But I'd recommend **SAA first**, even though you're a developer, because it forces you to understand networking, security, storage, databases, availability, scaling, and architecture.

---

# 🚀 One Important Adjustment for You

Because you already have **2 years of software development experience**, your roadmap should be:

**Developer → AWS Developer → Cloud Engineer → Cloud/DevOps/Backend Engineer**

rather than:

**AWS beginner → memorize services → certification**

Your existing programming, Git, APIs, databases, debugging, and application architecture knowledge are an advantage.

The most important skill is being able to look at a requirement and say:

> "I need this AWS architecture, and I understand why each service is there."

For example:

**"Users upload images, the API processes orders asynchronously, the application needs high availability, and the database must not be public."**

You should eventually be able to design:

```text
                  Route 53
                     |
                 CloudFront
                     |
                    ALB
                     |
              ECS / Fargate
               /          \
              /            \
            RDS           SQS
                            |
                         Lambda
                            |
                    +-------+-------+
                    |               |
                   S3              SNS
```

and explain **why** every component exists.

**If you tell me whether your current development stack is Java/Spring Boot, Node.js, Python/Django/FastAPI, or .NET, I can turn this into a concrete 12-week AWS study plan with daily topics and projects.**
