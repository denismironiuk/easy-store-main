# EasyStore: Cloud-Native GitOps Ecosystem on Azure 🚀

This is a comprehensive e-commerce ecosystem architected with a microservices approach. This repository serves as the **Master Blueprint**, documenting the end-to-end automation, networking, and deployment strategies used to build a resilient production environment.

---

## 🏗 Infrastructure Blueprint

Rather than just deploying containers, this project focuses on a robust infrastructure foundation:

### 🌐 Scalable Networking (Azure CNI Overlay)
* **Strategy**: Implemented **Azure CNI Overlay** to ensure high-performance pod networking.
* **Benefit**: Solved the "IP exhaustion" problem common in standard CNI by assigning pods IPs from a dedicated overlay address space, allowing for thousands of pods without depleting the VNET subnet.

### 🚦 Modern Traffic Management (Gateway API)
* **Evolution**: Moved beyond legacy Ingress to the **Kubernetes Gateway API**.
* **Implementation**: Configured dedicated Gateways and HTTPRoutes for fine-grained traffic control, enabling path-based routing between Frontend and Backend services.

### 🔄 Deployment Strategy (The GitOps Way)
* **Source of Truth**: All infrastructure and application states are stored in Git.
* **Sync Engine**: **ArgoCD** continuously monitors the GitOps repository, ensuring the AKS cluster remains in the desired state.
* **CI Automation**: **Jenkins** handles the heavy lifting—from code quality gates (ESLint/Jest) to secure container builds using **Kaniko**.

---

## 📦 Project Ecosystem
The project is modularized into specialized repositories:

1.  **[Frontend Service](https://github.com/denismironiuk/online-store-frontend)**: React 18 UI with dynamic environment injection.
2.  **[Backend API](https://github.com/denismironiuk/online-store-backend)**: Node.js/Express service with MongoDB Atlas integration.
3.  **[GitOps Manifests](https://github.com/denismironiuk/online-store-gitops)**: Kustomize-based manifests for seamless environment promotion.

---

## 📊 High-Level Architecture



```mermaid
graph TD
    subgraph "External Access"
    GW[Gateway API / Load Balancer]
    end

    subgraph "AKS Cluster (Azure CNI Overlay)"
    FE[Frontend Pods]
    BE[Backend Pods]
    end

    subgraph "External Services"
    DB[(MongoDB Atlas)]
    RED[(Redis Cache)]
    end

    GW --> FE
    FE --> BE
    BE --> DB
    BE --> RED
