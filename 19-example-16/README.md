# Volumes

## Volumes lifetime

- Depends on the Pod lifetime
  - Volumes survive Container restarts (and removal)
  - Volumes are removed when Pods are detroyed

## K8s vs Docker volumes

- Inside: image-volumes-vs.jpg

## Volumes:

- emptyDir: simply creates a new empty directory whenever the pod starts. And it keeps this directory alive and filled with data as long as the pod is alive. Containers can then write to this directory. And if containers restart or are removed, the data survives. But if the pod should be removed, this directory is removed.
  - down-side: when more than 1 replicas