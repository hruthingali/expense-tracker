Multi-Region AWS Infrastructure Deployment with CI/CD and EKS

This project demonstrates a complete 3-tier cloud infrastructure deployment on AWS using CloudFormation and Terraform, integrated with CodePipeline for CI/CD, and deploying applications to Amazon EKS in two regions. It also includes security scanning, observability, and automated monitoring tools.

🚀 Key Features

Multi-Region Deployment:

Deploys infrastructure and application in Region A and Region B.

Uses both CloudFormation and Terraform for provisioning.

3-Tier Architecture:

Load Balancer in Public Subnet.

Application (EKS) in Private Subnet.

Database (RDS) in Private Subnet.

CI/CD Pipeline (AWS CodePipeline):

End-to-end automation of infrastructure and application deployments.

Integrates with GitHub for source control.

Infrastructure as Code (IaC):

CloudFormation and Terraform templates for VPC, Subnets, Route Tables, NAT Gateways, RDS, EKS, etc.

Terraform provisioning is triggered via buildspec.yml in CodeBuild.

Observability and Monitoring:

Amazon CloudWatch for logs and metrics.

SonarQube for static code analysis in build.

Trivy for container image vulnerability scanning in build.

📁 Project Structure

.
├── cloudformation/           # CloudFormation templates
│   └── ...
├── terraform/                # Terraform configuration files
│   └── ...
├── buildspec/                # CodeBuild buildspec files
│   └── buildspec.yml
├── codepipeline/             # CodePipeline configuration (if any)
│   └── ...
├── k8s/                      # Kubernetes YAMLs for application
│   └── ...
├── README.md

🏗️ Infrastructure Components

Layer

Services Used

Network

VPC, Subnets (Public/Private), IGW, NAT Gateway

Compute

Amazon EKS (Private Subnet)

Storage

Amazon RDS (Private Subnet, MySQL/PostgreSQL)

Load Balancer

AWS Application Load Balancer (ALB)

Monitoring

CloudWatch Logs, Alarms, Dashboards

Security

Security Groups, IAM Roles, VPC Flow Logs

🔄 CI/CD Pipeline Flow

Source Stage – GitHub repository trigger.

Build Stage –

Infrastructure build using Terraform (executed via buildspec.yml).

Static code analysis using SonarQube.

Security scan using Trivy.

Deploy Stage –

Deploy application to EKS in both regions.

Monitor via CloudWatch.

🧪 Security & Quality Checks

✅ SonarQube – Quality gates for code.

✅ Trivy – Vulnerability scan for Docker images.

✅ IAM roles with least privilege.

✅ Private Subnets for all sensitive services.

📊 Monitoring & Logging

📌 CloudWatch Logs – Centralized logging for application, EKS, and infrastructure.

📌 CloudWatch Alarms – Set for critical metrics like CPU, memory, and errors.

📌 Grafana Integration (Optional) – Visual dashboards (if configured).

📦 How to Use

Before proceeding, make sure you have the following prerequisites:

AWS CLI configured

kubectl, eksctl, terraform, and aws-iam-authenticator installed

SonarQube and Trivy running (can be local or hosted)

Step 1: Clone the Repository

git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>

Step 2: Provision Infrastructure

The infrastructure is provisioned automatically by CodePipeline using Terraform steps defined in buildspec.yml.

Alternatively, to test locally:

cd terraform
terraform init
terraform apply

Step 3: Setup CodePipeline

Create pipeline using console or CDK.

Link GitHub as source and CodeBuild with buildspec.yml.

Step 4: Deploy Application

EKS YAML files are present under k8s/ directory.

Deploy manually (or through CodePipeline):

kubectl apply -f k8s/

This project is open-source and available under the MIT License.


AWS Free Tier

Open Source tools like SonarQube, Trivy

Terraform & CloudFormation teams

