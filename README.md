<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&amp;color=0:0a0f2e,50:1a237e,100:283593&amp;height=200&amp;section=header&amp;text=Kubernetes%20Nginx%20Demo&amp;fontSize=42&amp;fontColor=ffffff&amp;fontAlignY=38&amp;desc=Production-Style%20K8s%20Deployment%20Project&amp;descAlignY=58&amp;descSize=16" width="100%"/>

<br/>

[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](/)
[![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)](/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](/)
[![Helm](https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white)](/)

<br/>

![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)
![Level](https://img.shields.io/badge/Level-Beginner%20→%20Intermediate-blue?style=flat-square)
![Type](https://img.shields.io/badge/Type-Learning%20Project-orange?style=flat-square)

<br/>

> *A hands-on Kubernetes project covering real-world deployment patterns — from basic pods to autoscaling and rolling updates.*

</div>

---

## 📖 Project Overview

This project deploys a production-style **Nginx application on Kubernetes**, implementing the core patterns used in real DevOps workflows — not just `kubectl run`, but proper manifests with resource management, scaling, and zero-downtime updates.

### Features Implemented

| Feature | Description |
|---|---|
| ⚙️ **Deployment & Service** | Declarative manifest-based deployment |
| 🌐 **NodePort Exposure** | External access via NodePort `30007` |
| 📦 **Resource Limits** | CPU & Memory requests/limits configured |
| 📈 **Manual Scaling** | On-demand replica scaling |
| 🤖 **HPA** | Horizontal Pod Autoscaler (CPU-based) |
| 🔄 **Rolling Updates** | Zero-downtime image upgrades |
| ⏪ **Rollback** | Instant revert to previous version |
| 🚦 **Ingress** | Optional external routing via Ingress controller |

---

## 🗂️ Repository Structure

```
📦 kubernetes-nginx-demo/
├── 📄 deployment.yaml       ← Deployment manifest with resource limits
├── 📄 service.yaml          ← NodePort service
├── 📄 ingress.yaml          ← Optional Ingress config
└── 📄 README.md
```

---

## 🚀 How to Run

### 1 — Deploy the Application

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

Verify everything is running:

```bash
kubectl get pods
kubectl get svc
```

---

### 2 — Access the App

```
http://localhost:30007/
```

---

### 3 — (Optional) Enable Ingress

```bash
kubectl apply -f ingress.yaml
kubectl port-forward -n ingress-nginx service/ingress-nginx-controller 8080:80
```

Then access via:

```
http://localhost:8080/
```

---

### 4 — Manual Scaling

```bash
# Scale up
kubectl scale deployment nginx-demo --replicas=3

# Verify pods
kubectl get pods -w
```

---

### 5 — Horizontal Pod Autoscaler

```bash
# Create HPA (scales between 1–5 pods at 50% CPU)
kubectl autoscale deployment nginx-demo --cpu-percent=50 --min=1 --max=5

# Monitor HPA
kubectl get hpa -w
```

---

### 6 — Rolling Update

```bash
# Edit the deployment (change image version)
kubectl edit deployment nginx-demo

# Watch the rollout
kubectl rollout status deployment nginx-demo

# View rollout history
kubectl rollout history deployment nginx-demo
```

---

### 7 — Rollback

```bash
# Undo last rollout
kubectl rollout undo deployment nginx-demo

# Rollback to a specific revision
kubectl rollout undo deployment nginx-demo --to-revision=1
```

---

## 🔁 Deployment Lifecycle

```mermaid
flowchart TD
    A[📄 Write Manifest\ndeployment.yaml] --> B[🚀 kubectl apply]
    B --> C[⚙️ Deployment Created\nn replicas running]
    C --> D{Need Changes?}
    D -->|Scale| E[kubectl scale\n--replicas=N]
    D -->|Update Image| F[kubectl edit /\nkubectl set image]
    D -->|HPA| G[kubectl autoscale\ncpu-percent=50]
    F --> H[🔄 Rolling Update\nZero Downtime]
    H --> I{Update OK?}
    I -->|✅ Yes| J[New Version Live]
    I -->|❌ No| K[⏪ kubectl rollout undo]
    K --> C
    E --> C
    G --> C
```

---

## 📚 Learning Outcomes

```mermaid
mindmap
  root((K8s Nginx Demo))
    Workloads
      Deployments
      ReplicaSets
      Pod Lifecycle
    Networking
      Services
      NodePort
      Ingress Controller
    Scaling
      Manual Scaling
      HPA
      CPU Metrics
    Operations
      Rolling Updates
      Rollback
      Rollout History
    Config
      Resource Requests
      Resource Limits
```

---

## 🧠 Key Concepts Covered

| Concept | What Was Practiced |
|---|---|
| `Deployment` | Declarative pod management with replica control |
| `Service` | Stable network endpoint for pods |
| `NodePort` | Exposing the app outside the cluster |
| `Ingress` | HTTP routing via Ingress controller |
| `Resources` | Setting CPU/memory requests & limits |
| `HPA` | Auto-scaling based on CPU utilisation |
| `Rolling Update` | Updating image with zero downtime |
| `Rollback` | Reverting to a safe previous revision |

---

<div align="center">

[![www.linkedin.com/in/mihisara-koralage-06b739313](https://img.shields.io/badge/LinkedIn-Follow%20My%20Journey-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com)
[![https://github.com/mihisara-koralage](https://img.shields.io/badge/GitHub-More%20Projects-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com)

*Part of my hands-on Cloud & DevOps learning path.*

<img src="https://capsule-render.vercel.app/api?type=waving&amp;color=0:283593,50:1a237e,100:0a0f2e&amp;height=100&amp;section=footer" width="100%"/>

</div>
