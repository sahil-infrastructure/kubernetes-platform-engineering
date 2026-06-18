# E-Commerce DevOps Engineering Project

## Project Overview

This project demonstrates the deployment, monitoring, troubleshooting, and rollback of a containerized e-commerce application using industry-standard DevOps tools.

The objective was to simulate a real-world production environment and implement observability, alerting, and recovery mechanisms.

---

## Architecture

Flask Application → PostgreSQL → Docker Compose

Monitoring Stack:

cAdvisor → Prometheus → Grafana

---

## Technologies Used

* Docker
* Docker Compose
* Python Flask
* PostgreSQL
* Prometheus
* cAdvisor
* Grafana
* Git
* GitHub

---

## Features Implemented

### Application Layer

* Flask REST API
* Health Check Endpoint
* PostgreSQL Integration

### Containerization

* Custom Docker Image
* Docker Compose Deployment
* Persistent Volumes
* Container Networking

### Monitoring

* cAdvisor Container Metrics
* Prometheus Metric Collection
* Grafana Visualization

### Dashboards

* Total Memory Usage
* CPU Usage
* Running Containers
* Filesystem Usage

### Alerting

* Backend Availability Alert
* Threshold-Based Monitoring

### Incident Simulation

* Deployment Failure Simulation
* Version Rollback
* Service Recovery Validation

---

## Rollback Demonstration

A faulty application version (v1.1.0) was intentionally deployed.

Observed Behavior:

* Container restart loop
* Application startup failure
* Service unavailable

Recovery Steps:

* Reverted deployment from v1.1.0 to v1.0.0
* Recreated containers
* Validated health endpoint
* Restored service availability

---

## Screenshots

### Grafana Dashboard

![Grafana Dashboard](screenshots/grafana-dashboard.png)

### Prometheus Targets

![Prometheus Targets](screenshots/prometheus-targets.png)

### Running Containers

![Docker Containers](screenshots/docker-containers.png)

---

## Verification

Health Check:

```bash
curl http://localhost:5000/health
```

Expected Output:

```json
{"status":"healthy"}
```

---

## Learning Outcomes

* Docker Image Management
* Docker Compose Orchestration
* Container Monitoring
* Metrics Collection
* Dashboard Creation
* Alerting Concepts
* Incident Response
* Deployment Rollback
* GitHub Version Control

---

## Repository Structure

```text
backend/
compose/
monitoring/
screenshots/
README.md
```

---

## Author

Sahil
Senior IT Support Engineer
Platform Engineering Learning Project
