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

V1  VPC + EC2 + S3
 ↓
V2  Terraform modules
 ↓
V3  ALB + Auto Scaling
 ↓
V4  RDS
 ↓
V5  CloudWatch monitoring
 ↓
V6  AWS Budget / cost protection
 ↓
V7  GitHub Actions → Terraform
 ↓
V8  EKS + Helm
