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

### Declerative Object Configuration Example
- You can use the pod spec in /config folder.
```
kubectl apply -f config/
```

## Labels
### Equity Based Requirement
- You can use the pod spec equity_based in /label folder.
```
 kubectl get pods -l environment=preprod
```
### Set Based Requirement
- You can use the pod spec set_based_pod in /label folder.
```
kubectl get pods -l 'environment in (prod)'
```
## Namespaces
- You can set your name space
```
kubectl run nginx --image=nginx --namespace=<insert-namespace-name-here>
```
- List all pods with their namespaces
```
kubectl get pods --all-namespaces
```
- List default namespaces
```
kubectl get namespace
```

