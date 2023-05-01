# Kubernetes-01 Kubernetes Fundamentals and KubeConfig
This repository serves for understanding concepts and features of kubernetes environment.
- Please check out each branch to reach the context of Kubernetes.
- You can use powershell on windows. When Kubernetes is installed on docker, it will be available from all command lines.

## Installing Kubernetes Dashboard via Kubernetes Docker
- The Dashboard UI is not deployed by default. To deploy it, run the following command:
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
```

## Running Kube Proxy
- Now, run kube proxy to execute the ui.
```
kubectl proxy
```
- To reach the UI , go to ** http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
- To login, you need to have a token or kubeconfig.

## Accessing the Dashboard UI 
- To protect your cluster data, Dashboard deploys with a minimal RBAC configuration by default. Currently, Dashboard only supports logging in with a Bearer Token. To create a token for this demo, you can follow our guide on
- Run the serviceaccount.yaml and clusterrolebinding.yaml files in K8s to create an admin user and granting access role to the user.
- You can create a single yaml spec file to run all in one.
  - To create an admin user to access the resource operations.
```
kubectl apply -f .\serviceaccount.yaml
```
  - To assign role to user for the authentication.
```
kubectl apply -f .\clusterrolebinding.yaml
```

## Creating Access Token
- Now we need to find the token we can use to log in. Execute the following command:
```
kubectl -n kubernetes-dashboard create token admin-user
```
- Copy the printed token.

## Running Kube Proxy
- Now, run kube proxy to execute the ui.

```
kubectl proxy
```
- Go to UI ** - To reach the UI , go to ** http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/

- Enter the token you copied.

## Running Kubernetes Dashboard with MiniKube Cluster on Windows:
- Install minikube via Powershell by running the command:
```
New-Item -Path 'c:\' -Name 'minikube' -ItemType Directory -Force
Invoke-WebRequest -OutFile 'c:\minikube\minikube.exe' -Uri 'https://github.com/kubernetes/minikube/releases/latest/download/minikube-windows-amd64.exe' -UseBasicParsing
```
- Add the minikube.exe binary to your PATH.
** Make sure to run PowerShell as Administrator.
```
$oldPath = [Environment]::GetEnvironmentVariable('Path', [EnvironmentVariableTarget]::Machine)
if ($oldPath.Split(';') -inotcontains 'C:\minikube'){ `
  [Environment]::SetEnvironmentVariable('Path', $('{0};C:\minikube' -f $oldPath), [EnvironmentVariableTarget]::Machine) `
}
```
- From a terminal with administrator access (but not logged in as root), run your minikube cluster
```
minikube start
```
- Interact with your cluster:
```
kubectl get po -A
```
- Running the Kubernetes dashboard as you do not need to deal with token process anymore:
```
minikube dashboard
```
## View your MiniKube Config
```
kubectl config view
```
That's all :)
