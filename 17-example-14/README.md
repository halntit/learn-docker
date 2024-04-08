# First app on k8s

# Build image
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