# Kubernetes Nginx Deployment

A simple Nginx deployment on K3s using Kubernetes and Traefik.

## Technologies
- Kubernetes (K3s)
- Nginx
- Traefik
- Git and GitHub

## Deploy

```bash
kubectl apply -f base/
```

## Verify

```bash
kubectl get pods -n demo
kubectl get svc -n demo
kubectl get ingress -n demo
```

## Access

Open `http://<YOUR_SERVER_IP>` in your browser.

## Cleanup

```bash
kubectl delete -f base/
```
