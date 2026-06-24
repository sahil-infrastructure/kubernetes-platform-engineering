# 🚀 E-Commerce DevOps Engineering Project

## Overview

This project demonstrates the deployment, monitoring, troubleshooting, security scanning, alerting, and recovery of a containerized e-commerce platform using modern DevOps and Platform Engineering practices.

The goal was to simulate a production-style environment while gaining hands-on experience with:

* Docker
* Docker Compose
* PostgreSQL
* Prometheus
* Grafana
* cAdvisor
* Health Checks
* Alerting
* Vulnerability Scanning
* Incident Response
* Rollback Procedures

The project follows workflows commonly used by DevOps Engineers, Platform Engineers, SREs, and Cloud Engineers.

---

# 🏗 Architecture

## Application Flow

```text
User
 │
 ▼
Flask Application
 │
 ▼
PostgreSQL Database
```

## Monitoring Flow

```text
Application Containers
        │
        ▼
     cAdvisor
        │
        ▼
    Prometheus
        │
        ▼
      Grafana
```

---

# ⚙️ Technology Stack

| Category              | Technology     |
| --------------------- | -------------- |
| Application           | Python Flask   |
| Database              | PostgreSQL     |
| Containerization      | Docker         |
| Orchestration         | Docker Compose |
| Monitoring            | Prometheus     |
| Container Metrics     | cAdvisor       |
| Visualization         | Grafana        |
| Security Scanning     | Trivy          |
| Version Control       | Git            |
| Repository Management | GitHub         |

---

# 📁 Repository Structure

```text
ecommerce-platform/
│
├── frontend/
│
├── backend/
│   ├── Dockerfile
│   ├── app.py
│   └── requirements.txt
│
├── database/
│
├── monitoring/
│   ├── prometheus/
│   │    └── prometheus.yml
│   │
│   ├── grafana/
│   │
│   └── cadvisor/
│
├── compose/
│   └── docker-compose.yml
│
├── docs/
│
├── scripts/
│
├── screenshots/
│
└── README.md
```

---

# ✨ Key Features

## Application Layer

* Flask-based REST API
* PostgreSQL Integration
* Health Check Endpoint
* Containerized Deployment

## Containerization

* Custom Docker Image
* Multi-Container Deployment
* Docker Compose Orchestration
* Persistent Storage
* Internal Docker Networking

## Monitoring & Observability

* Real-Time Metrics Collection
* Infrastructure Monitoring
* Resource Utilization Tracking
* Dashboard Visualization
* Service Availability Monitoring

## Security

* Container Vulnerability Scanning
* Trivy Image Analysis
* Basic Secure Configuration Practices

---

# 🔄 Reliability Features

## Health Checks

PostgreSQL health checks ensure that dependent services start only when the database is available.

```yaml
healthcheck:
  test: ["CMD-SHELL", "pg_isready -U admin"]
  interval: 10s
  timeout: 5s
  retries: 5
```

### Why Health Checks Matter

Without health checks, the backend may start before PostgreSQL is ready and fail during initialization.

Health checks prevent startup race conditions and improve deployment reliability.

---

## Restart Policies

All services use:

```yaml
restart: unless-stopped
```

Benefits:

* Automatic recovery after crashes
* Recovery after host reboot
* Reduced manual intervention

---

## Dependency Management

Backend startup is controlled using:

```yaml
depends_on:
  postgres:
    condition: service_healthy
```

This ensures:

* PostgreSQL starts first
* Backend waits for database readiness
* Fewer deployment failures

---

# 📊 Monitoring Stack

## cAdvisor

cAdvisor collects container-level metrics including:

* CPU Usage
* Memory Usage
* Filesystem Usage
* Network Statistics

---

## Prometheus

Prometheus is responsible for:

* Metric Collection
* Time-Series Storage
* Service Monitoring
* Availability Tracking

Prometheus scrapes metrics from cAdvisor every 15 seconds.

---

## Grafana

Grafana visualizes infrastructure metrics through dashboards.

Monitored Metrics:

* Total Container Memory Usage
* Total CPU Usage
* Running Containers
* Filesystem Usage

---

# 🚨 Alerting

Grafana Alerting was configured to simulate production monitoring workflows.

### Alert Example

Backend Availability Alert

Condition:

```promql
up{job="cadvisor"} < 1
```

Evaluation Period:

```text
1 minute
```

Purpose:

* Detect service outages
* Simulate incident response
* Validate monitoring effectiveness

---

# 🔍 Health Verification

Verify backend health:

```bash
curl http://localhost:5000/health
```

Expected Output:

```json
{
  "status": "healthy"
}
```

---

# 🔐 Security Scanning

Trivy was used to scan container images for vulnerabilities.

Example:

```bash
trivy image ecommerce-backend:1.0.0
```

Benefits:

* Detect vulnerable packages
* Detect outdated dependencies
* Improve container security posture
* Shift security validation earlier in the deployment lifecycle

---

# 🔄 Incident Simulation & Rollback

A deployment failure was intentionally simulated.

## Faulty Release

A broken image version was created:

```text
ecommerce-backend:1.1.0
```

Behavior:

* Application startup failure
* Container restart loop
* Health check failure
* Service unavailable

---

## Rollback Procedure

The environment was recovered by rolling back to:

```text
ecommerce-backend:1.0.0
```

Actions Performed:

1. Reverted image version
2. Rebuilt application image
3. Redeployed containers
4. Validated service health
5. Confirmed monitoring recovery

Verification:

```bash
curl http://localhost:5000/health
```

Output:

```json
{
  "status": "healthy"
}
```

This demonstrates a real-world deployment recovery workflow commonly used in production environments.

---

# 📸 Screenshots

Add screenshots for:

* Docker Compose Running Containers
* Prometheus Targets
* Grafana Dashboard
* Grafana Alert Rule
* Rollback Demonstration
* Trivy Scan Results

Example:

```text
screenshots/
├── docker-compose-running.png
├── prometheus-targets.png
├── grafana-dashboard.png
├── grafana-alert-rule.png
├── rollback-demo.png
└── trivy-scan.png
```

---

# 🎯 Skills Demonstrated

* Docker
* Docker Compose
* Python Flask
* PostgreSQL
* Prometheus
* Grafana
* cAdvisor
* Trivy
* Infrastructure Monitoring
* Container Observability
* Incident Troubleshooting
* Alerting
* Deployment Rollback
* Git
* GitHub

---

# 📚 Learning Outcomes

Through this project I gained practical experience in:

* Building containerized applications
* Managing multi-container deployments
* Implementing health checks
* Designing monitoring dashboards
* Creating alerting rules
* Troubleshooting deployment failures
* Performing vulnerability scans
* Recovering from faulty deployments
* Implementing rollback strategies
* Maintaining infrastructure through version control

---

# 🔮 Future Enhancements

* Kubernetes Deployment
* GitHub Actions CI/CD Pipeline
* Terraform Infrastructure Provisioning
* Prometheus Alertmanager
* Centralized Logging
* Blue-Green Deployments
* Horizontal Scaling
* Automated Rollback Workflows

---

# 👨‍💻 Author

**Sahil Singh Chib**

Senior IT Support Engineer
Aspiring Devops Engineer

This project was created as part of my hands-on Platform Engineering and DevOps learning journey, focusing on production-style operational practices used in modern cloud-native environments.
