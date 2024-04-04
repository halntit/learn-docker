# K8S in action
  - Install minikube: https://minikube.sigs.k8s.io/docs/start/
  - Install kubectl: https://kubernetes.io/docs/tasks/tools/
  - Kubenetes works with Objects. Objects can be created in 2 ways:
    - Imperatively (bat buoc)
    - Declaratively (khai bao)

## Pod object:
  - the smallest "unit" k8s interacts with
  - contains and runs 1 or multiple containers
  - Pods contain share resources (e.g. volumes)
  - Has a cluster-internal IP by default; Containers inside a Pod can comminucate via localhost
  - (a Task in AWS ESC is very similar to pod)
  - Pods are designed to be ephemeral (khong ton tai lau): k8s will start/ stop/ replace them as needed

## Deployment object: (key object)
  - controls (mutiple) Pods
  - define which Pods and containers to run and the number of instances
  - deployments can be paused, deleted and rolled back
  - deployments can be scaled dynamically (and automatically)
  - **NOTES**: We typically don't directly control Pods, instead you use Deployments to set up the desired end state