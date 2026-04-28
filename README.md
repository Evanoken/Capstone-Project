# Capstone: Serverless API & Containerized Web App

## Architecture
- **API Gateway** — REST API that exposes a POST /submit endpoint
- **Lambda** — Serverless function that receives JSON payloads and logs them to CloudWatch
- **ECS (Fargate)** — Runs the containerized Nginx web app
- **ECR** — Stores the Docker image
- **CloudFormation** — Provisions the ECS cluster, task, and service
- **CloudWatch** — Collects logs and displays a monitoring dashboard

## Setup Instructions
1. Deploy Lambda + API Gateway
2. Build & push Docker image to ECR
3. Deploy ECS via CloudFormation
4. View monitoring in CloudWatch

## Screenshots

### Live ECS Web App
![ECS Web App](screenshots/ecs-webapp.png)

### Successful API Test
![API Test](screenshots/api-test.png)

### CloudWatch Dashboard
![CloudWatch Dashboard](screenshots/cloudwatch-dashboard.png)

## Repository Structure
- `lambda-api/` — Lambda function code
- `webapp/` — Dockerfile + index.html
- `infrastructure.yml` — CloudFormation template
