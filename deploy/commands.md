```bash
kubectl apply -f aws-secret.yaml
kubectl apply -f env-secret.yaml
kubectl apply -f env-configmap.yaml

# Feed API
kubectl apply -f backend-feed-deployment.yaml
kubectl apply -f backend-feed-service.yaml

# Users API
kubectl apply -f backend-user-deployment.yaml
kubectl apply -f backend-user-service.yaml

# Reverse proxy
kubectl apply -f reverseproxy-deployment.yaml
kubectl expose deployment udagram-reverseproxy --type=LoadBalancer --name=public-udagram-reverseproxy-svc

# Frontend
kubectl apply -f frontend-deployment.yaml
kubectl expose deployment udagram-frontend --type=LoadBalancer --name=public-udagram-frontend-svc
```