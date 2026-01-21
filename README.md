cloudmart-gitops (ArgoCD Manifests)
📌 CloudMart GitOps Repository

This repository is the single source of truth for Kubernetes deployments using ArgoCD.

All production deployments are driven by Helm values stored here.


## 🔄 Deployment Flow

GitHub Push → ArgoCD Sync → EKS Cluster

Application repo CI only updates image tags here.

## 📁 Structure

envs/
└── prod/
    ├── cart-values.yaml
    ├── catalog-values.yaml
    ├── checkout-values.yaml
    ├── orders-values.yaml
    └── ui-values.yaml

argocd/
└── applications.yaml




<img width="1111" height="539" alt="8" src="https://github.com/user-attachments/assets/f3459974-ee5c-44ba-a3e7-848a0322f8af" />



## 📦 ArgoCD Applications
Each service is defined as:

Helm-based app
Auto-sync enabled
Self-healing
Namespace scoped

## 🧠 Why GitOps?

Version-controlled deployments
Rollbacks via Git
No manual kubectl in prod
Full audit trail


## 🚀 How Deployment Happens

Developer pushes code to prod
CI builds & pushes Docker image
CI updates image tag in this repo
ArgoCD detects change
Cluster auto-updates


## 🔐 Security

No secrets in Git
Secrets injected via Kubernetes secrets / external services
IAM roles via IRSA where needed


## 👨‍💻 Author

Ali Haider DevOps / Cloud Engineer /linux


