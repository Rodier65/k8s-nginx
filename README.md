# Kubernetes Nginx Deployment

Deployment of Nginx on a K3s cluster using Kubernetes manifests and Traefik.

## Technologies

- Kubernetes (K3s)
- Nginx
- Traefik
- Git & GitHub

## Features

- Deployment and Service
- Ingress configuration
- Readiness and Liveness probes
- Horizontal Pod Autoscaler (HPA)
- RBAC (read-only access)
- CPU and memory resource limits

## Project Structure

```text
k8s-nginx/
├── base/
│   ├── namespace.yaml
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── ingress.yaml
│   ├── hpa.yaml
│   └── rbac.yaml
└── README.md
```

## Deployment

```bash
kubectl apply -f base/
```

## Verification

```bash
kubectl get pods -n demo
kubectl get svc -n demo
kubectl get ingress -n demo
kubectl get hpa -n demo
kubectl get pvc -n demo
```

## Access

```text
http://<SERVER_IP>
```

## Cleanup

```bash
kubectl delete -f base/
```

**Goal:** Practice Kubernetes fundamentals, workload management, autoscaling and access control on a K3s cluster.