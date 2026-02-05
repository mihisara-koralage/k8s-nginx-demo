# Kubernetes Nginx Demo

This repository contains my Kubernetes learning project as part of my Cloud & DevOps journey.

## Project Overview

A simple Nginx application deployed on Kubernetes with:

- Deployment & Service
- NodePort exposure
- Resource limits (CPU & Memory)
- Manual scaling
- Horizontal Pod Autoscaler (HPA)
- Rolling updates & rollbacks

## How to Run

1. Apply Deployment & Service:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```
2. (Optional) Apply Ingress:

```bash
kubectl apply -f ingress.yaml
kubectl port-forward -n ingress-nginx service/ingress-nginx-controller 8080:80
```
3. Access NodePort:

```bash
http://localhost:30007/
```
4. Scale manually:

```bash
kubectl scale deployment nginx-demo --replicas=3
```
5. Horizontal Pod Autoscaler:

```bash
kubectl autoscale deployment nginx-demo --cpu-percent=50 --min=1 --max=5
```
6. Rolling update example:

```bash
kubectl edit deployment nginx-demo
# change image to v2
kubectl rollout status deployment nginx-demo
```
7. Rollback if needed:

```bash
kubectl rollout undo deployment nginx-demo
```
## Learning Outcomes
- Kubernetes Deployments & Services
- NodePort & Ingress concepts
- Resource requests & limits
- Scaling & HPA
- Rolling updates & rollbacks
