# VPC Infrastructure for Todo Application

This repository contains the CloudFormation template for provisioning the complete infrastructure for the containerized Todo application, including VPC, ECS, and CI/CD pipeline.

## Architecture

- **VPC**: Custom VPC with private and public subnets across 2 AZs
- **VPC Endpoints**: Cost-optimized with DynamoDB and S3 gateway endpoints only
- **Application Load Balancer**: Internet-facing ALB in public subnets
- **ECS Cluster**: Fargate cluster for container orchestration
- **CodePipeline**: Event-driven CI/CD pipeline triggered by ECR image pushes
- **EventBridge**: Automatic pipeline triggering on ECR image updates
- **Parameter Store**: Centralized configuration management

## Key Features

### ✅ **Cost Optimized**
- **No NAT Gateways**: Saves ~$90/month by using VPC endpoints only
- **Gateway Endpoints**: DynamoDB and S3 endpoints for internal AWS communication
- **Efficient Resource Sizing**: Right-sized ECS tasks and infrastructure

### ✅ **Event-Driven Deployment**
- **ECR Integration**: Pipeline automatically triggers when new Docker images are pushed
- **EventBridge Rules**: Monitors ECR for `todo-app:latest` image updates
- **CodeBuild in VPC**: Deployment happens securely within private subnets

