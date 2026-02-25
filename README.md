# EasyStore: Full-Scale Cloud-Native Ecosystem 🚀

This is a production-grade e-commerce ecosystem architected with a microservices approach. This repository serves as the **Master Blueprint**, documenting the end-to-end automation, networking, and Infrastructure as Code (IaC) strategies used to build a resilient environment on Azure.

---

## 🏗 Infrastructure as Code (Terraform)
The entire infrastructure is managed declaratively using **Terraform**. 
* **IaC Migration**: Successfully migrated manual Azure setups into version-controlled code using `terraform import`.
* **State Management**: Implemented a **Remote Backend** using Azure Storage Accounts with state locking to ensure security and team collaboration.
* **Networking**: Configured **Azure CNI Overlay** for high-performance pod networking and the **Kubernetes Gateway API** for modern traffic routing.

---

## 📦 Project Structure & Repositories
The ecosystem is modularized into four specialized repositories:

1.  **[Infrastructure (IaC)](https://github.com/denismironiuk/online-store-infrastructure)**: Terraform manifests for AKS, Networking, and Remote State management.
2.  **[Backend API](https://github.com/denismironiuk/online-store-backend)**: Node.js/Express service with MongoDB Atlas and Redis.
3.  **[Frontend Service](https://github.com/denismironiuk/online-store-frontend)**: React-based UI optimized for containerized deployment.
4.  **[GitOps Manifests](https://github.com/denismironiuk/online-store-gitops)**: Kustomize configurations and ArgoCD application definitions.

---

## 🔄 Automation & GitOps Flow
1. **CI Pipeline**: Jenkins (Pipeline as Code) triggers on every push, runs integration tests (Jest), and builds secure images using **Kaniko**.
2. **CD Pipeline**: Jenkins updates image tags in the GitOps repository.
3. **Synchronization**: **ArgoCD** detects changes and reconciles the AKS cluster state automatically.

---

## 💼 Professional Background
* **Transition**: Evolved from managing high-precision manufacturing systems at **Tower Semiconductor** (2024-2025) to architecting scalable cloud infrastructures.
* **Education**: Developed as a capstone project during intensive R&D training at **Infinity Labs**, Israel.
* **Skills**: Azure, Kubernetes, Terraform, Jenkins, GitOps, Linux Networking.

---
*Architected by Denis Mironiuk. Focus on reliability, scalability, and automation.*
