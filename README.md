# Kubernetes-03 Working with Kubernetes Objects
## Kubernetes Object Management Techniques
### Imperative Commands Example:
```
kubectl create deployment nginx --image nginx
```

```
kubectl get pods --all-namespaces
```

```
kubectl describe pod <pod-name>
```

```
kubectl get deployments
```

### Imperative Object Configuration Example:
```
kubectl apply -f nginx_pod.yaml
```
