# First app on k8s

## Build image
  - ```docker build -t kub-first-app .```

## Push image to HUB
- Build image
  - ```docker tag kub-first-app halntit/kube-first-app```
- Push to HUB
  - ```docker push halntit/kube-first-app:tagname```

## Start deployment
- Start minikube
  - ```minikube start --driver=hyperv``` (hyperV not support on linux/amd64)
- Create new deployment object
  - ```kubectl create deployment first-app --image=halntit/kube-first-app```
- Get insight
  - ```kubectl get deployments```
  - ```kubectl get pods```
- Delete deployment
  - ```kubectl delete deployment <name>```

## Access dashboard
- ```minikube dashboard```

## Service object
- Pod have an internal IP address by default (and changed when a Pod is replaced)
- Sevice group Pods with a shared IP
- Service can allow external access to Pods
- Expose a deployment with a service
  - ```kubectl expose deployment first-app --type=LoadBalancer --port=8080```
  - ```kubectl get services```
- Access pod from serivce (start webpage)
  - ```minikube service first-app```

## Scaling in action
- ```kubectl scale deployment/first-app --replicas=3```

## Updating deployments
- Changes code, rebuild image
  - docker build... / docker tag .../ docker push
- Update new image for deployment
  - ```kubectl set image deployment/first-app kube-first-app=halntit/kube-first-app```
- **NOTE: the image won't updated without tag**
  - rebuild image with tag: ```docker build -t kub-first-app:2 .```
  - retag image with tag: ```docker tag kub-first-app:2 halntit/kube-first-app:2```
  - repush with tag: ```docker push halntit/kube-first-app:2```
  - set image with tag: ```kubectl set image deployment/first-app kube-first-app=halntit/kube-first-app:2```
  - check the status of the rollout: ```kubectl rollout status deployment/first-app```

## Rollback and History
- If you has typo in the ```set image``` command like ```kube-first-app=halntit/kube-first-app:**a2**``, the deployment will failed
- In that case, the current pod will not terminated and won't replaced by the failed pod
- Review history
  - ```kubectl rollout history deployment/first-app``` or
  - ```kubectl rollout history deployment/first-app --revision=1```
- To roll back, use command
  - ```kubectl rollout undo deployment/first-app``` or
  - ```kubectl rollout undo deployment/first-app --to-revision=1```