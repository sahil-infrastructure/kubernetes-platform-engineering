# 🚀 Kubernetes Platform Engineering Project

> Production-ready Flask application deployed on Kubernetes using Helm, GitHub Actions, Argo CD (GitOps), Prometheus, and Grafana.

![Kubernetes](https://img.shields.io/badge/Kubernetes-1.34-blue)
![Docker](https://img.shields.io/badge/Docker-Enabled-blue)
![Helm](https://img.shields.io/badge/Helm-3.x-0f1689)
![ArgoCD](https://img.shields.io/badge/GitOps-ArgoCD-orange)
![Prometheus](https://img.shields.io/badge/Monitoring-Prometheus-red)
![Grafana](https://img.shields.io/badge/Dashboards-Grafana-F46800)

---

# Project Overview

This repository demonstrates a complete Platform Engineering workflow from containerization to Kubernetes deployment and GitOps.

## Features

- Dockerized Flask application
- Kubernetes Deployments and Services
- ConfigMaps & Secrets
- Liveness & Readiness Probes
- Rolling Updates
- Rollback Demonstration
- Persistent Volumes
- Helm Charts
- GitHub Actions CI/CD
- Argo CD GitOps
- Prometheus Monitoring
- Grafana Dashboards

---

# Architecture

```text
Developer
    │
Git Push
    │
GitHub
    │
GitHub Actions
    │
Docker Hub
    │
Argo CD
    │
Kubernetes Cluster
 ├── Flask Pods
 ├── PostgreSQL
 ├── Services
 ├── ConfigMaps
 ├── Secrets
 ├── PV/PVC
 ├── Prometheus
 └── Grafana
```

You can also replace this with a Mermaid diagram if preferred.

---

# Repository Structure

```text
.
├── backend/
├── kubernetes/
├── helm/
├── monitoring/
├── .github/workflows/
├── Screenshots/
└── README.md
```

---

# Technology Stack

| Category | Tools |
|-----------|-------|
| Containers | Docker |
| Orchestration | Kubernetes |
| Package Manager | Helm |
| CI/CD | GitHub Actions |
| GitOps | Argo CD |
| Monitoring | Prometheus |
| Visualization | Grafana |

---

# Screenshots

Place screenshots inside:

```text
Screenshots/
```

Example:

```markdown
![Deployment](Screenshots/deployment.png)

![Grafana](Screenshots/grafana-dashboard.png)

![ArgoCD](Screenshots/argocd.png)
```

---

# Deployment Guide

```bash
docker build -t your-image .
docker push your-image

kubectl apply -f kubernetes/

helm install ecommerce ./helm

kubectl get all
```

---

# GitHub Actions

Pipeline stages:

1. Checkout
2. Build Docker Image
3. Push Docker Image
4. Update Kubernetes manifests
5. GitOps sync through Argo CD

---

# Helm

Install

```bash
helm install ecommerce ./helm
```

Upgrade

```bash
helm upgrade ecommerce ./helm
```

Rollback

```bash
helm rollback ecommerce 1
```

---

# GitOps with Argo CD

Argo CD continuously watches this repository.

Whenever a change is pushed:

- Detects drift
- Syncs cluster
- Applies latest manifests

---

# Monitoring

Prometheus collects metrics from the cluster.

Grafana visualizes:

- CPU Usage
- Memory Usage
- Pod Health
- Container Restarts
- Node Metrics

---

# Rolling Updates

```bash
kubectl rollout status deployment/ecommerce
```

---

# Rollback Demonstration

Deploy new image

```bash
kubectl set image deployment/ecommerce backend=image:v2
```

Rollback

```bash
kubectl rollout undo deployment/ecommerce
```

---

# Lessons Learned

- Kubernetes resource management
- Production deployments
- GitOps workflows
- CI/CD automation
- Monitoring and observability
- High availability concepts

---

# Future Improvements

- Horizontal Pod Autoscaler
- Service Mesh
- Terraform Infrastructure
- Multi-cluster deployment
- External Secrets
- Loki Logging

---

# Author

## Sahil Singh Chib

**Platform Engineer**

Passionate about Kubernetes, Cloud Infrastructure, DevOps, GitOps, Automation, and Platform Engineering.

Connect on LinkedIn and GitHub.

---

⭐ If you found this project useful, consider giving it a star.
