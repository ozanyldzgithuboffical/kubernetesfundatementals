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
- You can use the pod spec in /label folder.
```
 kubectl get pods -l environment=preprod
```
### Set Based Requirement

