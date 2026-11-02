# Kubernetes Nginx Deployment

Deployment of Nginx on a K3s cluster using Kubernetes manifests, Kustomize and Traefik.

## Technologies

- Kubernetes (K3s)
- Nginx
- Traefik (Ingress Controller)
- Kustomize
- Git & GitHub

## Features

- Deployment and Service
- Ingress configuration with Traefik
- Readiness and Liveness probes
- Horizontal Pod Autoscaler (HPA)
- RBAC (read-only access)
- CPU and memory requests/limits

## Project Structure

```text
k8s-nginx/
├── base/
│   ├── kustomization.yaml
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
kubectl apply -k base/
```

## Verification

```bash
kubectl get all,ingress,hpa -n demo
```

## Test Autoscaling

```bash
kubectl run load-gen -n demo --rm -it --image=busybox:1.36 -- \
  /bin/sh -c "while true; do wget -q -O- http://nginx-service; done"
```

In another terminal:

```bash
kubectl get hpa -n demo -w
```

> K3s includes Metrics Server, which provides the metrics required by the HPA.

## Test RBAC

```bash
kubectl auth can-i list pods -n demo \
  --as=system:serviceaccount:demo:nginx-viewer

# Expected: yes

kubectl auth can-i delete pods -n demo \
  --as=system:serviceaccount:demo:nginx-viewer

# Expected: no
```

## Access

```text
http://<SERVER_IP>
```

## Cleanup

```bash
kubectl delete -k base/
```

## Goal

Practice Kubernetes fundamentals, workload management, autoscaling, access control and application deployment on a K3s cluster.