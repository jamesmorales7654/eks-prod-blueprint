# EKS-Prod-Blueprint

> **Production-ready Amazon EKS infrastructure using modular Terraform**

This project provisions a scalable, secure, and production-grade Kubernetes cluster on AWS using Amazon EKS. The infrastructure is split into modular components (networking, IAM, and EKS) and follows best practices for multi-AZ deployment, IAM roles, NAT gateway usage, and remote state management.

---

## 📐 Architecture Overview

* **VPC with Public & Private Subnets** across 2 Availability Zones
* **Internet Gateway & NAT Gateway** for controlled egress
* **Private EKS Cluster** with managed node group
* **IAM roles for cluster and nodes** with least privilege policies
* **Remote state backend** using S3 and DynamoDB for state locking

---

## 🗂 Directory Structure

```
terraform/
├── backend.tf                # Remote backend config
├── main.tf                   # Root module calling submodules
├── provider.tf               # AWS provider config
├── variables.tf              # Global variables
├── outputs.tf                # Exported outputs
├── prod.tfvars               # Production environment variable values
├── .gitignore                # Ignore Terraform state/secrets
│
├── eks/                      # EKS module
│   ├── main.tf
│   ├── outputs.tf
│   └── variable.tf
│
├── iam/                      # IAM module for EKS roles
│   ├── main.tf
│   ├── outputs.tf
│   └── variable.tf
│
└── networking/               # VPC, subnets, NAT gateways
    ├── main.tf
    ├── outputs.tf
    └── variable.tf
```

---

## 🚀 How to Use

> Make sure your AWS credentials are set and you have permission to create the resources below.

```bash
# Clone the repo
$ git clone https://github.com/jamesmorales7654/eks-prod-blueprint.git
$ cd eks-prod-blueprint/terraform

# Initialize Terraform
$ terraform init

# Preview the deployment
$ terraform plan -var-file="prod.tfvars"

# (Optional) Apply the infrastructure
$ terraform apply -var-file="prod.tfvars"
```

> 🔥 **Lab Use Only**: This project was validated using an AWS Free Tier account and is not intended for deployment in production without security, cost, and scalability review.

---

## 📦 Features

* Modular Terraform structure
* Multi-AZ high availability
* Secure IAM setup
* Remote backend (S3 + DynamoDB)
* Reusable submodules
* Best practices for EKS production readiness

---

## 🔐 Security Notes

* Secrets and keys are **not committed**
* `.tfvars` and `*.tfstate` are ignored by default
* IAM roles follow least privilege

---

## 🧠 Credits

Created by **James Morales** — Security Platform Engineer with 15+ years of experience designing scalable infrastructure and leading secure cloud transformations.


---

## 📫 Connect with me

* [LinkedIn](https://linkedin.com/in/jamesmorales7654)
* [GitHub](https://github.com/jamesmorales7654)
* [Portfolio](https://your-portfolio-link.com)

