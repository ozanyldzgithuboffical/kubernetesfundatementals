- This repository serves for understanding concepts and features of kubernetes environment.
#  Tech Talk Agenda
## Rolling Update Strategy
- Deploy nginx backend deployment with ngixn 1.14.2
```
kubectl apply -f rollingupdate.yaml
```
- Check the deployment to look into the status of the deployment and deployment name.
```
kubectl get deployment
```
- Update the image with 1.24:

```
kubectl set image deployment/<deployment-name> <container-name-of-deployment>=<image>:<version> --to-revision=<revision-number><optional>
```
```
kubectl set image deployment/backend hello=nginx:1.24
```
- Check the status of update.
```
kubectl rollout history deployment/<deployment-name>
```
- Check the rollout history: You will see the revisions. 
```
kubectl rollout history deployment/<deployment-name>
```
- You can undo/rollback operation by the revision number
```
kubectl rollout undo deployment/<deployment-name> --to-revision=<revision-number>
```

## Recreate Strategy
- Deploy recreateoriginal.yaml file
```
kubectl apply -f recreateoriginal.yaml
```
- Check the deployment to look into the status of the deployment and deployment name.
```
kubectl get deployment
```
- Update the version of the deployment in yaml file.
- Then, apply the deployment again
```
kubectl apply -f recreateoriginal.yaml
```

## Blue - Green (Red - Black Strategy)
- Create First blue , then green deployments. The traffic will be same for both then you can discard one of them once green is stabilized.
