


# 🚀 DevOps End-to-End Project on Microsoft Azure

### **Modern CI/CD | AKS | Terraform | Monitoring | Alerting | Slack | DevOps Best Practices**

---

## 📌 Overview

This project demonstrates a **complete real-world DevOps pipeline** built on Microsoft Azure.
It includes **Infrastructure as Code, containerized workloads, CI/CD automation, observability, alerts, and secure delivery pipelines**.

The system consists of:

* 🖥️ **Frontend Application (Containerized)**
* ⚙️ **Backend API (Containerized)**
* ☁️ **Azure Kubernetes Service (AKS) Deployment**
* 📦 **Azure Container Registry (ACR)**
* 📈 **Grafana + Prometheus Monitoring & Slack alerts**

This project follows industry deployment standards including:

* **Build Once → Deploy Many**
* **Immutable container images**
* **Git-based versioning**
* **Automated release workflow**

📄 This assessment reference: 

---

## 🧩 Architecture Diagram

```
Developer → GitHub → Azure DevOps Pipeline → Build Docker Images → ACR
                                                             ↓
                                                     Deploy to AKS
                                                             ↓
                                                Ingress + Nginx + TLS
                                                             ↓
                                   Monitoring (Grafana + Prometheus)
                                                             ↓
                                               Alerting to Slack
```

---

## Tech Stack

| Category         | Tools / Services               |
| ---------------- | ------------------------------ |
| Cloud            | Azure                          |
| IaC              | Terraform                      |
| Version Control  | Git + GitHub                   |
| CI/CD            | Azure DevOps Pipelines         |
| Containerization | Docker                         |
| Orchestration    | AKS (Azure Kubernetes Service) |
| Monitoring       | Grafana + Prometheus           |
| Alerting         | Slack + Grafana alert rules    |
| Storage          | Azure Blob                     |
                    

---

## 📂 Repository Structure

```
/Azure-DevOps-Project
│
├── infra/                   # Terraform infrastructure
├── k8s/                     # Kubernetes manifests or Helm charts
├── pipelines/              # Azure DevOps YAML CI/CD pipelines
├── alerts/                  # Grafana + Slack alert configs
├── docker/                  # Dockerfile + container build logic
└── README.md                # You're reading this
```

---

##  Infrastructure Deployment Using Terraform

### 1️⃣ Configure Backend for Terraform State

```sh
terraform init
```

### 2️⃣ Validate the configuration

```sh
terraform validate
```

### 3️⃣ Create the infrastructure

```sh
terraform apply -auto-approve
```

Resources created:

* Resource Group
* VNet + Subnets
* Azure Kubernetes Service (AKS)
* Azure Container Registry (ACR)
* Azure Storage Account (Terraform backend)

---

## 🏗️ CI/CD Workflow (Azure DevOps Pipelines)

✔ Fully automated with **multi-stage YAML pipeline**:

| Stage      | Description                              |
| ---------- | ---------------------------------------- |
| **Build**  | Build Docker images (frontend + backend) |
| **Scan**   | Security scanning + linting              |
| **Push**   | Push container images to ACR             |
| **Deploy** | Deploy to AKS                            |
| **Verify** | Health checks + smoke tests              |

📌 Strategy used:

> **Build Once → Deploy to Dev → QA → Prod using same verified image.**

---

## 🐳 Docker Image Strategy

* Tagged using **Semantic Versioning + Git SHA**
* Uses **Multi-stage Docker build**
* Runs under **non-root container user**

Example:

```
myapp-frontend:v1.2.3-sha1123abc
myapp-backend:v1.2.3
```

---

## ☸ Kubernetes Deployment (AKS)

Includes:

* Deployment
* Service
* Ingress (Nginx)
* Liveness/Readiness probes
* HPA (Horizontal Pod Autoscaler)

To deploy manually:

```sh
kubectl apply -f k8s/
```

---

## 📈 Observability & Alerting

✔ **Grafana dashboards configured**
✔ **Prometheus metrics scraping enabled**
✔ **Slack alert webhook integrated**

Example Slack alert received 👇 (from your screenshot):

>  **TestAlert – Firing**

---

##  Testing & Validation

* Pipeline validation
* Health checks
* Load testing
* Scaling test via HPA
* Slack alert rule verification

---

## Operational Runbook

| Scenario            | Action                                         |
| ------------------- | ---------------------------------------------- |
| Rollback Deployment | `kubectl rollout undo deployment <name>`       |
| Restart Pods        | `kubectl rollout restart deployment <name>`    |
| Scale Manually      | `kubectl scale deployment <name> --replicas=3` |
| Re-run CI/CD        | Commit → push → pipeline triggers              |

---

## 📚 Deliverables Summary

✔ Terraform provisioning
✔ CI/CD automation
✔ Secure image build + versioning
✔ AKS deployment
✔ Grafana + Slack alerts
✔ Documentation + runbooks
✔ Architecture & redesign reports (per assessment) 

---

