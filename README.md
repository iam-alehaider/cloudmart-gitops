🛒 CloudMart GitOps Deployment with Argo CD on AWS EKS

This repository implements GitOps-based continuous delivery for the CloudMart microservices platform using Argo CD, Helm, and Amazon EKS.

All Kubernetes deployments are managed declaratively via Git, ensuring reliable, auditable, and automated production releases.

🧩 Tech Stack

☸️ Kubernetes (Amazon EKS)

🚀 Argo CD (GitOps Continuous Delivery)

⎈ Helm (Application Packaging)

🐳 Docker (Containerization)

🔁 CI/CD (GitHub Actions / Jenkins)

☁️ AWS (ECR, EKS, IAM, IRSA)

🧱 Terraform (for EKS & infra provisioning – in separate repo)

📁 Repository Structure
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

🔹 envs/prod

Contains environment-specific Helm values for each microservice.
This includes:

Image tags

Resource limits

Environment variables

Service configuration

🔹 argocd/applications.yaml

Defines Argo CD Application resources that:

Track Helm charts from app repositories

Apply values from this GitOps repo

Auto-sync changes to the cluster

📦 Microservices Deployed

🛒 Cart Service

📦 Catalog Service

💳 Checkout Service

📬 Orders Service

🖥️ UI Frontend

Each service is deployed as an independent Argo CD Application with:

Helm-based deployment

Auto-sync enabled

Self-healing enabled

Namespace isolation

🧠 Why GitOps?

This project follows GitOps principles:

✅ Git is the single source of truth

🔁 Easy rollback using Git history

🔒 No manual kubectl in production

📜 Full audit trail of changes

🤖 Continuous reconciliation by Argo CD

If cluster state drifts from Git, Argo CD automatically corrects it.

🚀 Deployment Workflow

Developer pushes code to production branch

CI pipeline builds Docker image

Image pushed to Amazon ECR

CI updates image tag in this GitOps repo

Argo CD detects Git changes

Argo CD syncs workloads to EKS

Kubernetes updates running pods

➡️ No manual deployment steps required.

🔐 Security Design

❌ No secrets stored in Git

🔑 Secrets injected using:

Kubernetes Secrets

External secret managers (optional)

🛡️ AWS IAM access via IRSA (IAM Roles for Service Accounts)

🔒 Argo CD access controlled using RBAC

📊 Architecture Overview

Flow:

Developer → GitHub → CI Pipeline → ECR → GitOps Repo → Argo CD → EKS


Separation of Responsibilities:

Application code → App repositories

Infrastructure → Terraform repo

Deployment configuration → This GitOps repo

This improves security, auditability, and team collaboration.

⚙️ Prerequisites

Amazon EKS cluster

Argo CD installed in cluster

Helm charts available for services

CI pipeline capable of updating image tags

🧪 Local Testing (Optional)

Helm values can be tested locally:

helm template cart ./chart -f envs/prod/cart-values.yaml


This allows validation before committing to Git.

📈 Future Improvements

Multi-environment support (dev / staging / prod)

Argo CD Image Updater integration

Progressive delivery (canary / blue-green)

Policy enforcement with OPA Gatekeeper

Prometheus & Grafana monitoring

👨‍💻 Author

Ali Haider
IT Infrastructure & Cloud Engineer
Skills: Linux, AWS, Docker, Kubernetes, Terraform, CI/CD, Security

📍 Lahore, Pakistan
🌍 Open to international opportunities
