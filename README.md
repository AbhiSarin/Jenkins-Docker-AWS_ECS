# Jenkins → Docker → Amazon ECR → Amazon ECS CI/CD Pipeline

This project demonstrates a complete production-style CI/CD pipeline for containerized application deployment on AWS using Jenkins, Docker, Amazon ECR, and Amazon ECS Fargate.

The pipeline automatically builds, packages, and deploys a Python Flask application whenever code is pushed to the GitHub repository.

## Architecture

GitHub → Jenkins → Docker → Amazon ECR → Amazon ECS Fargate → Application Load Balancer

## Features

* Automated CI/CD pipeline using Jenkins
* GitHub webhook integration for automatic builds
* Dockerized Python Flask application
* Secure image storage using Amazon ECR
* Container orchestration with Amazon ECS Fargate
* Zero-downtime deployments using ECS Service updates
* Application Load Balancer integration
* IAM Role-based authentication (no hardcoded AWS credentials)
* Health checks and automatic task replacement
* Scalable cloud-native deployment architecture

## Workflow

1. Developer pushes code to GitHub.
2. GitHub webhook triggers Jenkins automatically.
3. Jenkins pulls the latest source code.
4. Jenkins builds a Docker image.
5. Docker image is tagged and pushed to Amazon ECR.
6. Jenkins triggers an ECS service deployment.
7. ECS pulls the latest image from ECR.
8. New tasks are launched behind the Application Load Balancer.
9. Traffic is routed to healthy containers automatically.

## Technologies Used

* Python (Flask)
* Docker
* Jenkins
* GitHub
* Amazon ECR
* Amazon ECS Fargate
* Application Load Balancer (ALB)
* IAM Roles
* AWS CLI

## Learning Outcomes

Through this project, the following DevOps concepts were implemented and validated:

* Continuous Integration (CI)
* Continuous Deployment (CD)
* Infrastructure on AWS
* Containerization using Docker
* Image Registry Management
* ECS Service Deployment
* Load Balancing
* Webhook Automation
* Cloud Security using IAM Roles
* Production Deployment Best Practices

## Future Enhancements

* HTTPS using AWS Certificate Manager (ACM)
* Custom Domain with Route 53
* Blue/Green Deployments
* Terraform Infrastructure as Code
* Monitoring with CloudWatch
* Container Security Scanning
* Multi-Environment Deployments (Dev/Staging/Production)
* Automated Testing Stage Integration

This project serves as a practical implementation of modern DevOps practices and demonstrates end-to-end cloud deployment automation on AWS.
