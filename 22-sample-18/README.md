# EKS

## EKS role
- Use EKS-Cluster from use-case form

## Change kubectl to AWS EKS
- backup /user-home/.kube/config just in case
- delete minikube config
  - ```minikube delete```
  - all config for minikube will be removed from /<user-home>/.kube/config
- Change kubectl to AWS EKS
  - ```aws eks --region ap-southeast-1 update-kubeconfig --name kub-dep-demo```

## Add worker node
- Need a role for it
  - Access IAM -> EC2
    - -> search for eks -> check
    - -> search for cni -> check
    - -> search for ec2containerreg -> ...sth...READONLY -> check

## Stop minikube

## Issues
- error: exec plugin: invalid apiVersion "client.authentication.k8s.io/v1alpha1"
  - ```pip3 install awscli --upgrade --user```
  - ```aws eks --region ap-southeast-1 update-kubeconfig --name kub-dep-demo```
    - add config for aws into local kube

## Deployment
- apply as in minikibe
- ```kubectl apply -f auth.yml -f users.yml```
- ```kubectl get services```

## Apply AWS-EFS
- From https://github.com/kubernetes-sigs/aws-efs-csi-driver
  - ```kubectl apply -k "github.com/kubernetes-sigs/aws-efs-csi-driver/deploy/kubernetes/overlays/stable/?ref=release-2.0"```