# EasyStore: Cloud-Native GitOps Ecosystem on Azure

This repository serves as the central hub for the EasyStore project — a full-scale e-commerce platform built with a microservices architecture. The project demonstrates end-to-end automation, from code commit to cloud deployment.

### 🛠 Tech Stack & Infrastructure
* **Orchestration**: Kubernetes (AKS-ready or Self-managed).
* **Networking**: **Azure CNI Overlay** for high-performance pod networking and scalable IP management.
* **CI/CD**: Jenkins (Declarative Pipelines) & Kaniko for containerization.
* **GitOps**: ArgoCD with Kustomize for automated environment synchronization.
* **Traffic Management**: Kubernetes Gateway API.
* **App Stack**: React (Frontend), Node.js (Backend), MongoDB Atlas.

### 📦 Project Structure
The ecosystem is modularized into four specialized repositories:
1. [Frontend Service](ссылка) - React UI.
2. [Backend API](ссылка) - Node.js microservice.
3. [GitOps Manifests](ссылка) - Kustomize overlays and K8s configurations.
4. [Infrastructure (IaC)](ссылка) - Cluster-wide settings and monitoring (Azure CNI, Gateway API).

### 🚀 Automation Flow
1. **CI**: Jenkins detects changes via Poll SCM/Webhooks, runs ESLint Quality Gates, and builds images using Kaniko.
2. **Registry**: Images are pushed to DockerHub with unique build tags.
3. **GitOps**: Jenkins automatically updates image tags in the GitOps repository.
4. **CD**: ArgoCD detects the manifest change and synchronizes the cluster state.
