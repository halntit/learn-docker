# EKS

## EKS role
- Use EKS-Cluster from use-case form

## Change kubectl to AWS EKS
- ```aws eks --region ap-southeast-1 update-kubeconfig --name kub-dep-demo```

## Add worker node
- Need a role for it
  - Access IAM -> EC2 
    - -> search for eks -> check
    - -> search for cni -> check
    - -> search for ec2containerreg -> ... READONLY -> check