- This repository serves for understanding concepts and features of kubernetes environment.
## Creating Replica Set
```
kubectl create -f replicasetwithnginx.yaml
```
## Querying the Replica Set
```
kubectl get replicaset my-replicaset
```
## Querying the replicated Pods
```
kubectl get pods 
```
## Changing the Replication Number of Pods Manually
- Change the replicas property in yaml file.
- Then run:
```
kubectl replace -f <yaml-file>
```
## Rescale the Replica Set with Imperative-Argument Command
```
kubectl scale --replicas=5 -f .\replicasetwithnginx.yaml
```
- You can check the replicaset and pods again.

## Deamon Set

