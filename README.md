# 🚀 Deploying Ruby on Rails with Terraform on AWS ECS Fargate

This repo demonstrates deploying a Dockerized Ruby on Rails app using Terraform + AWS ECS Fargate in **us-east-1**.

## 🧩 What it includes
- Terraform-managed VPC, RDS, ECS, ALB, CloudWatch
- Dockerfile for Rails app
- GitHub Actions CI/CD pipeline

## ⚙️ Steps to deploy

### 1. Setup environment
- AWS account + IAM credentials
- Terraform CLI
- Docker installed

### 2. Configure GitHub Secrets
Add the following secrets to your GitHub repo:
```
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_ACCOUNT_ID
AWS_REGION=us-east-1
IMAGE_NAME=rails-fargate-app
```

### 3. Bootstrap Terraform state backend
Create:
- S3 bucket: `my-rails-terraform-state`
- DynamoDB table: `terraform-locks`

### 4. Deploy
```bash
cd infra
terraform init
terraform apply -auto-approve
```

After apply, you’ll get output:
```
app_url = myapp-alb-xxxx.us-east-1.elb.amazonaws.com
```

Visit that URL 🎉

### 5. CI/CD via GitHub Actions
Push to `main` branch → it:
- Builds Docker image
- Pushes to ECR
- Applies Terraform automatically

Enjoy your fully automated Rails deployment ❤️
