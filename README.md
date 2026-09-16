# AWS EKS Cloud Infrastructure Monorepo ☁️🚀

A complete, production-grade cloud infrastructure and CI/CD project designed to provision and manage an Amazon Elastic Kubernetes Service (EKS) cluster using **Terraform** (Infrastructure as Code).

## 🏗️ Architecture Highlights

This project follows AWS Well-Architected Framework best practices, specifically focusing on Security and High Availability:
* **Custom VPC:** A dedicated Virtual Private Cloud spanning 2 Availability Zones (`us-east-1a`, `us-east-1b`).
* **Strict Security Boundaries:** 
  * Public Subnets house the NAT Gateway and Internet Gateway.
  * Private Subnets strictly host the EKS Worker Nodes (`t3.small`), ensuring they are not directly accessible from the internet.
* **Identity & Access Management:** Least Privilege IAM Roles for EKS Control Plane and Worker Nodes.
* **Infrastructure as Code (IaC):** 100% of the infrastructure is automated and version-controlled using Terraform.

## 📂 Project Structure

This monorepo is divided into functional stages:

- `infra/` : Terraform configurations for VPC, Networking, IAM, and EKS Cluster (Complete ✅).
- `app/` : Source code and `Dockerfile` for the application (Upcoming 🚧).
- `k8s/` : Kubernetes deployment and service manifests (Upcoming 🚧).
- `.github/workflows/` : GitHub Actions pipelines for automated CI/CD (Upcoming 🚧).

## 🛠️ Prerequisites

To run this project, you need the following tools installed and configured:
* [AWS CLI](https://aws.amazon.com/cli/) (Configured with AdministratorAccess)
* [Terraform](https://www.terraform.io/downloads)
* [kubectl](https://kubernetes.io/docs/tasks/tools/)

## 🚀 How to Provision (Phase 1: Infrastructure)

Navigate to the `infra` directory:
```bash
cd infra
```

1. **Initialize Terraform:**
```bash
terraform init
```

2. **Review the Deployment Plan:**
```bash
terraform plan
```

3. **Provision the Infrastructure:**
```bash
terraform apply
```
*(Note: The EKS Control Plane and Node Group may take 15-20 minutes to provision).*

4. **Connect to the Cluster:**
Configure `kubectl` to interact with the new cluster:
```bash
aws eks update-kubeconfig --region us-east-1 --name eks-main-cluster
```

## 🧹 Cleanup (The Golden Rule)
To avoid incurring AWS charges, always tear down the infrastructure after practice:
```bash
terraform destroy
```

---
**Author:** Anees Ahmad  
*AWS Certified Solutions Architect – Associate*