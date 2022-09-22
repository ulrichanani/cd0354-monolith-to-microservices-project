```bash
kubectl apply -f aws-secret.yaml
kubectl apply -f env-secret.yaml
kubectl apply -f env-configmap.yaml

kubectl get secrets
kubectl get configmap

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
kubectl apply -f frontend-deployment.yamlkc describe 
kubectl expose deployment udagram-frontend --type=LoadBalancer --name=public-udagram-frontend-svc

# HPA & Metric server
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
kubectl autoscale deployment udagram-api-feed --cpu-percent=50 --min=1 --max=3

# Screenshots
kubectl get pods
kubectl describe services
kubectl describe hpa
kubectl logs udagram-api-user
kubectl logs udagram-api-feed
kubectl logs udagram-frontend
kubectl logs udagram-reverseproxy
```

http://a5e288e67f1bc49528d2a20d0eca0d54-1487765455.us-east-1.elb.amazonaws.com:8080/api/v0/feed

http://aaefd158d5a2e4f11b8db38778cad47b-848227203.us-east-1.elb.amazonaws.com