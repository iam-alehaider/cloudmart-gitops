# 🛒 CloudMart GitOps Deployment with Argo CD on AWS EKS

This repository implements **GitOps-based continuous delivery** for the CloudMart microservices platform using **Argo CD, Helm, and Amazon EKS**.

All Kubernetes deployments are managed declaratively via Git, ensuring **reliable, auditable, and automated production releases**.

---

## 🧩 Tech Stack

- ☸️ Kubernetes (Amazon EKS)
- 🚀 Argo CD (GitOps Continuous Delivery)
- ⎈ Helm (Application Packaging)
- 🐳 Docker (Containerization)
- 🔁 CI/CD (GitHub Actions / Jenkins)
- ☁️ AWS (ECR, EKS, IAM, IRSA)
- 🧱 Terraform (for EKS & infra provisioning – in separate repo)

---

## 📁 Repository Structure

```text
.
├── argocd/
│   └── applications.yaml        # Argo CD Application definitions
│
└── envs/
    └── prod/                    # Production environment values
        ├── cart-values.yaml
        ├── catalog-values.yaml
        ├── checkout-values.yaml
        ├── orders-values.yaml
        └── ui-values.yaml
