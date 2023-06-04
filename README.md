- This repository serves for understanding concepts and features of kubernetes environment.
#  Tech Talk Agenda
## Minikube Tunnel If you use Windows OS
- Minikube tunnel exposes your service clustered ip address to open to external calls.
- In windows os based systems, when tunnel process is run, to start the service, the browser must be opened.
- To run the service:
```
minikube service <service-name>
```

 ## How to Use Spec Files
 - There are four spec files backend, backend service, frontend and frontend spec files respectively.
 - The backend spec file run the backend deployment with 3 replicas. 3 back-end pods are going to be run identically and managed by deployment.
 - Frontend application is run on only one pod.
 - Backend application is closed to outside and only reachable within by front end application via backend service.
 - Frontend service is open to external calls but not directly its pod ip address. It uses frontend service which is a loadbalancer.
 - Loadbalancer is the single exposed network entry for external calls.

## How to Run Spec Files
- Respectively, first we run backend deployment and backend service spec files respectively.
- Our backend application with 3 replicas are formed and bound to back end service which the frontend application can access for queries
- Then we run frontend deployment and frontend service.
- To see the run services
```
kubectl get svc -n <namespace-name>
```
- To see the run pods
```
kubectl get pods -n <namespace-name>
```
## How to activate the service
- To activate the front service for external calls
```
minikube service <frontend-service-name>
```
