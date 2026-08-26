# AWS Dev Environment

## Project Structure

```text
aws-dev-environment/
├── README.md
├── provider.tf
├── variables.tf
├── main.tf
├── outputs.tf
├── terraform.tfvars.example
└── .gitignore
```

# AWS Infrastructure Evolution Roadmap

This project evolves an AWS infrastructure stack from a basic deployment into a production-ready, automated Kubernetes platform.

## V1 — VPC + EC2 + S3

Build the foundational AWS infrastructure:

* VPC and networking
* Public/private subnets
* Internet Gateway
* Route tables
* EC2 instances
* S3 bucket

## V2 — Terraform Modules

Refactor the infrastructure into reusable Terraform modules:

* VPC module
* EC2 module
* S3 module
* Variables and outputs
* Environment-based configuration

## V3 — ALB + Auto Scaling

Add high availability and scalability:

* Application Load Balancer
* Target groups
* Launch templates
* Auto Scaling Group
* Health checks
* Multi-AZ deployment

## V4 — RDS

Introduce managed database infrastructure:

* Amazon RDS
* Private subnets
* Security groups
* Database subnet group
* Backup configuration
* High-availability considerations

## V5 — CloudWatch Monitoring

Add observability and monitoring:

* CloudWatch metrics
* CPU and memory monitoring
* Application logs
* Alarms
* Dashboards
* Notification integration

## V6 — AWS Budget / Cost Protection

Implement cost controls:

* AWS Budget
* Monthly spending threshold
* Budget alerts
* Cost monitoring
* Resource tagging

## V7 — GitHub Actions → Terraform

Automate infrastructure deployment through CI/CD:

* GitHub Actions workflow
* Terraform formatting and validation
* Terraform plan
* Terraform apply
* Remote state management
* Approval workflow for production

## V8 — EKS + Helm

Move toward a Kubernetes-based platform:

* Amazon EKS cluster
* Managed node groups
* Kubernetes networking
* Helm charts
* Application deployments
* Kubernetes services and ingress
* CloudWatch / container monitoring

## Architecture Progression

```text
V1  VPC + EC2 + S3
          ↓
V2  Terraform Modules
          ↓
V3  ALB + Auto Scaling
          ↓
V4  RDS
          ↓
V5  CloudWatch Monitoring
          ↓
V6  AWS Budget / Cost Protection
          ↓
V7  GitHub Actions → Terraform
          ↓
V8  EKS + Helm
```

## Goal

Progress from **basic AWS infrastructure** to a **modular, scalable, monitored, cost-aware, CI/CD-driven Kubernetes platform** using Terraform and AWS.
