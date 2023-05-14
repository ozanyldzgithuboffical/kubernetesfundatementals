- This repository serves for understanding concepts and features of kubernetes environment.
# Replica Set
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

# Deamon Set
## Creating Fluentd Elastic Search Deamon Set
```
kubectl create -f fluentd_version2.yaml
```
- If you want to set a custom namespace rather than default namespace you can add namespace under metadata in yaml file and you can first create the namespace before creating the deamon set.
- Optional:
```
kubectl create ns <namespace-name>
```
```
kubectl create -f fluentd_version2.yaml
```
## Checking the Deamon Set
```
kubectl get daemonset -n <namespace-name>
```
## Checking the Pods under the namespace on which node the deamon set is running:
```
kubectl get pods -n <namespace-name> -o wide
```
## Describing the Deamon Set
```
kubectl describe daemonset -n <namespace>
```
