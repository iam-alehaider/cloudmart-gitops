# 📌 CloudMart GitOps Repository (ArgoCD Manifests)

This repository serves as the **single source of truth** for all Kubernetes deployments in the **CloudMart platform**, following **GitOps principles** with **Argo CD**.

All production workloads are deployed using **Helm charts**, with environment-specific configuration managed through **Helm values stored in this repository**.

---

## 🔄 Deployment Flow

GitHub Push → Argo CD Sync → Amazon EKS Cluster


- Application repositories handle **build & CI**
- This repository controls **what runs in the cluster**
- Argo CD continuously reconciles desired vs actual state

---

## 📁 Repository Structure

```text
envs/
└── prod/
    ├── cart-values.yaml
    ├── catalog-values.yaml
    ├── checkout-values.yaml
    ├── orders-values.yaml
    └── ui-values.yaml

argocd/
└── applications.yaml


---
## 📌 Description

envs/prod/
Environment-specific Helm values for each microservice
argocd/applications.yaml
Defines Argo CD Application resources for all services


<img width="1111" height="539" alt="8" src="https://github.com/user-attachments/assets/65a12cdb-3397-4e50-962b-19087c97dc25" />


## 📦 Argo CD Applications

Each CloudMart microservice is deployed as an Argo CD Application with:

Helm-based deployment
Auto-sync enabled
Self-healing enabled
Namespace-scoped isolation
Declarative configuration

🧠 Why GitOps?
✅ Version-controlled deployments
🔁 Easy rollbacks using Git history
🔒 No manual kubectl in production
📜 Full audit trail of all changes
🤖 Automated reconciliation via Argo CD


## 🚀 How a Deployment Happens


Developer pushes code to the production branch
CI pipeline builds and pushes a Docker image
CI updates the image tag in this GitOps repository
Argo CD detects the Git change
Argo CD automatically syncs the cluster
EKS cluster updates the workload


## 🔐 Security Considerations

❌ No secrets stored in Git
🔑 Secrets injected via:
Kubernetes Secrets
External secret managers (if configured)
🛡️ IAM permissions handled via IRSA
🔒 Argo CD access protected with RBAC



## 📊 Architecture Reference

<img width="1111" height="539" alt="CloudMart GitOps Architecture" src="https://github.com/user-attachments/assets/f3459974-ee5c-44ba-a3e7-848a0322f8af" />

## 🎯 Key Takeaway

Git defines the desired state.
Argo CD enforces it.
Kubernetes runs it.
