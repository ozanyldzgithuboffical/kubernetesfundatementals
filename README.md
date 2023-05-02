- This repository serves for understanding concepts and features of kubernetes environment.
#  Kubernetes-02 WorkLoads#1
## Pod Creation
- Save the content with .yaml file.
```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```
- Run the yaml file.
```
kubectl apply -f $yaml_file_name
```
- List the available pods with their namespaces
```
kubectl get pods --all-namespaces
```
- Describe the pod to see pod status.
```
kubectl describe pod $pod_name
```
## Container Probes - Liveness
- Create your pod with liveness probe.
```
apiVersion: v1
kind: Pod
metadata:
  labels:
    test: liveness
  name: liveness-exec
spec:
  containers:
  - name: liveness
    image: registry.k8s.io/busybox
    args:
    - /bin/sh
    - -c
    - touch /tmp/healthy; sleep 30; rm -f /tmp/healthy; sleep 600
    livenessProbe:
      exec:
        command:
        - cat
        - /tmp/healthy
      initialDelaySeconds: 5
      periodSeconds: 5
 ```
 - Run the yaml file.
```
kubectl apply -f $yaml_file_name
```
 - Describe the pod after 30 seconds to see liveness prob container created.
 - After describing, wait for 35 seconds by describing again to see the status of the pod which will be restarted.
 ## Init Containers
 - Create your pod with init container.
  ```
 apiVersion: v1
kind: Pod
metadata:
  name: nginxwithinit
spec:
  initContainers:
  - name: sleepy
    image: alpine
    command: ['sleep', '60']	
  containers:
  - name: nginxwithinit
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```
 - Run the yaml file.
```
kubectl apply -f $yaml_file_name
```
- Describe the pod after 1 minute so that it will be in sleep mode.
     
 ## Pod Template
 - Create your pod with pod template.
 ```
 apiVersion: batch/v1
kind: Job
metadata:
  name: hello
spec:
  template:
    spec:
      containers:
      - name: hello
        image: busybox:1.28
        command: ['sh', '-c', 'echo "Hello, Kubernetes!" && sleep 3600']
      restartPolicy: OnFailure
      ```
- Run the yaml file.
```
kubectl apply -f $yaml_file_name
```
- It will create a single container with template. You can increase the size of the containers by replicating.
