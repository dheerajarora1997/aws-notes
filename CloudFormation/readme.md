# AWS CloudFormation Learning Roadmap

A practical learning roadmap for building and managing AWS infrastructure using **AWS CloudFormation**.

## 📚 Learning Path

```text
CloudFormation
│
├── 1. Parameters / Outputs
│
├── 2. EC2
│   ├── Security Groups
│   ├── IAM Roles
│   └── UserData
│
├── 3. S3
│   ├── Versioning
│   ├── Encryption
│   └── Lifecycle
│
├── 4. Networking
│   ├── VPC
│   ├── Subnet
│   ├── Route Table
│   ├── Internet Gateway
│   └── NAT Gateway
│
├── 5. Databases
│   ├── RDS
│   └── DynamoDB
│
├── 6. Serverless
│   ├── Lambda
│   ├── API Gateway
│   ├── SQS
│   └── SNS
│
├── 7. Monitoring
│   ├── CloudWatch
│   └── Alarms
│
└── 8. Production
    ├── Load Balancer
    ├── Auto Scaling
    ├── Secrets Manager
    ├── WAF
    └── CloudFront
```

---

## 1. Parameters / Outputs

Learn how to make CloudFormation templates reusable and configurable.

### Topics

* Parameters
* Outputs
* `Ref`
* `GetAtt`
* Mappings
* Conditions
* Intrinsic functions

### Example use cases

* Choose EC2 instance type during deployment
* Pass environment names such as `dev`, `staging`, and `prod`
* Output resource IDs and endpoints

---

## 2. EC2

Learn how to provision and configure virtual servers.

### Topics

* EC2 Instances
* Security Groups
* IAM Roles
* Instance Profiles
* UserData
* EBS Volumes
* AMIs
* Key Pairs

### Example architecture

```text
CloudFormation
      │
      └── EC2
          ├── Security Group
          ├── IAM Role
          ├── Instance Profile
          ├── UserData
          └── EBS Volume
```

### Common use cases

* Web servers
* Application servers
* Development environments
* CI/CD runners
* Background workers

---

## 3. S3

Learn how to create and manage object storage.

### Topics

* S3 Buckets
* Versioning
* Encryption
* Lifecycle Policies
* Bucket Policies
* Public Access Blocking
* Event Notifications

### Example architecture

```text
S3
├── Versioning
├── Encryption
├── Lifecycle
└── Access Policies
```

### Common use cases

* Application files
* Backups
* Logs
* Static websites
* Data storage

---

## 4. Networking

Networking is one of the most important areas of AWS infrastructure.

### Topics

* VPC
* Subnets
* Route Tables
* Internet Gateway
* NAT Gateway
* Security Groups
* Network ACLs
* Elastic IPs

### Example architecture

```text
                    Internet
                       │
                Internet Gateway
                       │
                     VPC
                       │
             ┌─────────┴─────────┐
             │                   │
       Public Subnet       Private Subnet
             │                   │
        Load Balancer          EC2
             │                   │
             └─────────┬─────────┘
                       │
                  NAT Gateway
```

### Common use cases

* Public web applications
* Private application servers
* Database isolation
* Secure outbound internet access

---

## 5. Databases

Learn how to provision managed databases with CloudFormation.

### RDS

Topics:

* PostgreSQL
* MySQL
* Database Instances
* Subnet Groups
* Security Groups
* Backups
* Encryption

### DynamoDB

Topics:

* Tables
* Partition Keys
* Sort Keys
* On-demand billing
* Provisioned capacity
* Point-in-time recovery

### Example architecture

```text
Application
    │
    ├── RDS PostgreSQL
    │
    └── DynamoDB
```

---

## 6. Serverless

Learn how to build applications without managing servers directly.

### Lambda

Learn:

* Lambda Functions
* IAM Roles
* Environment Variables
* Event Sources

### API Gateway

Learn:

* HTTP APIs
* REST APIs
* Lambda integrations
* API authorization

### SQS

Learn:

* Queues
* Dead-letter queues
* Message visibility timeout
* Asynchronous processing

### SNS

Learn:

* Topics
* Subscriptions
* Notifications
* Fan-out architectures

### Example architecture

```text
Client
  │
  ▼
API Gateway
  │
  ▼
Lambda
  │
  ├── DynamoDB
  │
  └── SQS
         │
         ▼
       Worker
```

---

## 7. Monitoring

Learn how to monitor AWS infrastructure and applications.

### CloudWatch

Topics:

* Metrics
* Logs
* Log Groups
* Dashboards
* Events
* Alarms

### Alarms

Example:

```text
EC2 CPU > 80%
      │
      ▼
CloudWatch Alarm
      │
      ▼
SNS Notification
```

### Common monitoring tasks

* EC2 CPU monitoring
* Application logs
* Lambda errors
* Database metrics
* Load balancer health
* Automated notifications

---

## 8. Production Architecture

Once the fundamentals are comfortable, move toward production-grade architectures.

### Load Balancer

Learn:

* Application Load Balancer
* Target Groups
* Listeners
* Health Checks

### Auto Scaling

Learn:

* Launch Templates
* Auto Scaling Groups
* Scaling Policies
* Minimum/maximum instances

### Secrets Manager

Learn:

* Database credentials
* API keys
* Application secrets
* Secret rotation

### WAF

Learn:

* Web ACLs
* IP rules
* Rate limiting
* Managed rules

### CloudFront

Learn:

* CDN
* Origins
* Caching
* HTTPS
* CloudFront + S3
* CloudFront + ALB

### Example production architecture

```text
                         Internet
                            │
                            ▼
                       CloudFront
                            │
                            ▼
                           WAF
                            │
                            ▼
                     Load Balancer
                            │
                  ┌─────────┴─────────┐
                  │                   │
              EC2 #1              EC2 #2
                  │                   │
                  └─────────┬─────────┘
                            │
                 ┌──────────┴──────────┐
                 │                     │
                RDS                   S3
                 │
          Secrets Manager

              CloudWatch
                  │
                  ▼
                 SNS
```

---

# 🎯 Recommended Project Order

Build these projects one by one:

```text
01. Basic EC2
       ↓
02. EC2 + Security Group
       ↓
03. EC2 + IAM Role + UserData
       ↓
04. S3 + Versioning + Encryption
       ↓
05. VPC + Public Subnet
       ↓
06. VPC + Public/Private Subnets
       ↓
07. EC2 + RDS
       ↓
08. Lambda + DynamoDB
       ↓
09. API Gateway + Lambda
       ↓
10. SQS + Lambda Worker
       ↓
11. CloudWatch + SNS
       ↓
12. ALB + EC2
       ↓
13. ALB + Auto Scaling
       ↓
14. Secrets Manager
       ↓
15. WAF + CloudFront
       ↓
16. Complete Production Architecture
```

# 🛠️ Suggested Repository Structure

```text
cloudformation/
│
├── README.md
│
├── 01-parameters-outputs/
│   └── template.yaml
│
├── 02-ec2/
│   ├── ec2.yaml
│   ├── security-group.yaml
│   └── iam-role.yaml
│
├── 03-s3/
│   ├── bucket.yaml
│   └── backup-bucket.yaml
│
├── 04-networking/
│   ├── vpc.yaml
│   ├── subnet.yaml
│   ├── routes.yaml
│   └── nat-gateway.yaml
│
├── 05-databases/
│   ├── rds.yaml
│   └── dynamodb.yaml
│
├── 06-serverless/
│   ├── lambda.yaml
│   ├── api-gateway.yaml
│   ├── sqs.yaml
│   └── sns.yaml
│
├── 07-monitoring/
│   ├── cloudwatch.yaml
│   └── alarms.yaml
│
└── 08-production/
    ├── alb.yaml
    ├── autoscaling.yaml
    ├── secrets-manager.yaml
    ├── waf.yaml
    └── cloudfront.yaml
```

# 🚀 Goal

By completing this roadmap, you should be able to take a typical AWS application and describe its infrastructure entirely as code:

```text
CloudFormation
      │
      ├── Networking
      ├── Compute
      ├── Storage
      ├── Database
      ├── Security
      ├── Serverless
      ├── Load Balancing
      ├── Auto Scaling
      └── Monitoring
```

The ultimate goal is to make AWS infrastructure **repeatable, version-controlled, reviewable, and easy to deploy across environments** such as `dev`, `staging`, and `production`.
