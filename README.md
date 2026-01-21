
# 🛒 CloudMart GitOps Deployment with Argo CD on AWS EKS

This repository implements **GitOps-based continuous delivery** for the CloudMart microservices platform using **Argo CD, Helm, and Amazon EKS**.

All Kubernetes deployments are managed declaratively via Git, ensuring **reliable, auditable, and automated production releases**.

---

## 🧩 Tech Stack

- Kubernetes (Amazon EKS)
- Argo CD (GitOps Continuous Delivery)
- Helm (Application Packaging)
- Docker (Containerization)
- CI/CD (GitHub Actions / Jenkins)
- AWS (ECR, EKS, IAM, IRSA)
- Terraform (for EKS & infra provisioning – in separate repo)

---

## 📁 Repository Structure

---

.
├── argocd/
│   └── applications.yaml        # Argo CD Application definitions
│
└── envs/
    └── prod/                   # Production environment values
        ├── cart-values.yaml
        ├── catalog-values.yaml
        ├── checkout-values.yaml
        ├── orders-values.yaml
        └── ui-values.yaml


---

## envs/prod

Contains environment-specific Helm values:

- Image tags
- Resource limits
- Environment variables
- Service configuration

---

## argocd/applications.yaml

Defines Argo CD Application resources:

- Tracks Helm charts from app repositories
- Applies values from this repo
- Auto-syncs to the cluster

---

## Microservices

- Cart
- Catalog
- Checkout
- Orders
- UI

---

## Deployment Flow

1. Code push
2. CI builds image
3. Push to ECR
4. Update GitOps repo
5. Argo CD sync
6. Pods updated in EKS

---

## Author

Ali Haider — Cloud & DevOps Engineer




