# Capstone Project: Serverless API & Containerized Web App
**Week 1 Foundations: Bringing It All Together**

## 🏗️ Project Overview
This project demonstrates a hybrid cloud-native architecture on AWS, combining a containerized frontend with a serverless backend. The deployment is automated using Infrastructure as Code (IaC) to ensure consistency and scalability across the environment.

### Architecture
* [cite_start]**Infrastructure as Code:** AWS CloudFormation for automated resource provisioning[cite: 5].
* [cite_start]**Containerized App:** Amazon ECS (Fargate) hosting a lightweight Nginx web application[cite: 5, 7].
* [cite_start]**Serverless API:** Amazon API Gateway and AWS Lambda handling backend requests[cite: 5, 6].
* [cite_start]**Observability:** Amazon CloudWatch for logging, metrics, and health dashboards[cite: 1, 5].

---

## 🛠️ Repository Structure
* [cite_start]`infrastructure.yml`: CloudFormation template for ECS Cluster, Task Definition, and Fargate Service[cite: 5].
* [cite_start]`lambda-api/`: Folder containing the Node.js Lambda function code (`index.js`)[cite: 5].
* [cite_start]`webapp/`: Folder containing the Dockerfile and static web app source code[cite: 5].
* `media/`: Evidence of deployment success and system monitoring.

---

## 🚀 Deployment Steps

### 1. The Containerized Web App
* [cite_start]Developed a static website and packaged it using a lightweight `nginx:alpine` Docker image[cite: 5].
* [cite_start]Pushed the image to **Amazon ECR** (Elastic Container Registry)[cite: 5].
* [cite_start]Deployed the ECS Cluster and Fargate Service using the `infrastructure.yml` CloudFormation template[cite: 5].

### 2. The Serverless API
* [cite_start]Created an **AWS Lambda** function to accept JSON payloads and return a success message with a unique submission ID[cite: 5].
* [cite_start]Configured **Amazon API Gateway** with a `POST /submit` route integrated with the Lambda function[cite: 5, 6].

### 3. Observability
* [cite_start]Configured a **CloudWatch Dashboard** to monitor Lambda Invocations, Errors, and Duration[cite: 5].
* [cite_start]Verified logging functionality through **CloudWatch Logs Insights**[cite: 1, 5].

---

## 📊 Evidence of Success

### 1. Live ECS Web Application
The web application is live and accessible via a public IP address, showing successful deployment on Fargate.
![Live Web Server](media/live-web-server.png)
 [cite_start][cite: 7]

### 2. API Gateway Test
A successful POST request to the API endpoint showing a `200 OK` status and the returned submission message.
![API Gateway Test](media/api-gateway-test.png)
 [cite_start][cite: 6]

### 3. Custom CloudWatch Dashboard
Custom dashboard visualizing key metrics including Lambda Invocations and system health.
![CloudWatch Dashboard](media/DemoApp-Observability.png)
 [cite_start][cite: 5]

---

## 🛡️ Advanced Monitoring & Deployment Insights

Beyond the core requirements, this project implements advanced observability and performance tracking to ensure production-level reliability.

### Performance Analysis & Reliability
* [cite_start]**Lambda Execution Analysis:** Used CloudWatch Logs Insights to analyze the average execution duration of the backend API, ensuring low latency for users[cite: 2].
* [cite_start]**Automated Alerting:** Configured a `LambdaErrorAlarm` to notify administrators immediately if the API failure rate exceeds defined thresholds[cite: 3, 4].
* **SNS Integration:** Successfully confirmed subscription to the Amazon SNS topic for real-time alert delivery.

### Key Technical Factors
* **Zero-Downtime Deployment:** The ECS service was configured to ensure the web app remains available during updates.
* [cite_start]**Granular Logging:** Every API request is captured in detailed logs, allowing for deep-dive debugging through specific log groups[cite: 1].
* **Infrastructure Validation:** Verified the complete stack lifecycle, including successful stack creation and change-set execution via the AWS CLI.

### Additional Evidence
### 4. Deep-Dive Logs Insights
[cite_start]Evidence of detailed log analysis using CloudWatch Logs Insights to verify data capture and system behavior. [cite: 8]
![Logs Insights](media/log-insights.png)

### 5. Performance Benchmarking
[cite_start]Analysis of the **Average Execution Duration** for the Lambda backend to ensure optimal latency and user experience. [cite: 9]
![Average Execution Duration](media/average-execution-duration.png)

### 6. Proactive Health Alarms
[cite_start]Configuration of a `LambdaErrorAlarm` to monitor for system failures and ensure high availability. [cite: 10, 11]
![Lambda Error Alarm](media/LambdaErrorAlarm.png)

### 7. Notification System Verification
Confirmation of the Amazon SNS subscription to ensure that automated health alerts are successfully delivered.
![Subscription Confirmation](media/subscription-confirm.png)

## 🧹 Cleanup
To avoid unnecessary AWS costs:
1. Delete the CloudFormation Stack.
2. Delete the ECR Repository and images.
3. Remove the API Gateway and Lambda function.