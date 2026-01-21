
# 🛒 CloudMart GitOps Deployment with Argo CD on AWS EKS

This repository implements **GitOps-based continuous delivery** for the CloudMart microservices platform using **Argo CD, Helm, and Amazon EKS**.
All Kubernetes deployments are managed declaratively via Git, ensuring **reliable, auditable, and automated production releases**.

---

## 🧩 Tech Stack

- Kubernetes (Amazon EKS)
- Argo CD (GitOps Continuous Delivery)
- Helm (Application Packaging)
- Docker (Containerization)
- CI/CD (GitHub Actions / Argocd)
- AWS (ECR, EKS, IAM, IRSA)
- Terraform (for EKS & infra provisioning – in separate repo)

---

## 📁 Repository Structure

```text

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
```


<img width="1111" height="539" alt="8" src="https://github.com/user-attachments/assets/56a285b0-b430-4b58-a032-8f26057443ac" />


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


<img width="1437" height="638" alt="Screenshot 2026-01-13 200446" src="https://github.com/user-attachments/assets/7d9fd5f4-793c-4a6b-a356-deb215b021f4" />

5. Argo CD sync
6. Pods updated in EKS

<img width="1366" height="524" alt="Screenshot 2026-01-16 055404" src="https://github.com/user-attachments/assets/5cde033e-7190-437d-8271-e28f10f959fe" />


<img width="1895" height="804" alt="Screenshot 2026-01-19 025552" src="https://github.com/user-attachments/assets/74197bac-a53c-4ca0-aed3-e230fa032fad" />

---

## Author
Ali Haider DevOps / Cloud Engineer /linux
- Github: https://github.com/iam-alehaider





