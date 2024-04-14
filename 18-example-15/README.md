# Declerative Approach

- Command: ```kubectl apply -f config.yml```

## Configuration file:

- filename is chosen freely
- find **apiVersion**: Kubenetes website
- **kind** is very important, e.g. Deployment, Service, ...
- **metedata**: cruel data, like **name**
- **spec**: how this deployment should configured
- **selector**:
  - tell which pod belongs to this deployment
  - Label selector for pods. Existing ReplicaSets whose pods are selected by this will be the ones affected by this deployment. It must match the pod template's labels.

## Service

- Command: ```kubectl apply -f service.yml```
- ```minibuke service backend```

### Notes

- **spec > selector** of deployment object is newer so it has different instruction from service object (with matchLabels)