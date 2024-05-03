# K8S networking

## Hostname in k8s
- Automatically create env var for hostname
  - combine service-name with "SERVICE_HOST" string, e.g. "AUTH_SERVICE_SERVICE_HOST"
  - with AUTH_SERVICE is from auth service name "auth-service"
  - SERVICE_HOST is the key by k8s

## CoreDNS
- Written in GO

## Issues:
- Create a private docker hub project so it is always return error "ImagePullBackOff"
- Make the repo public
- Delete/remove pod with issue, then the new one will auto-re-create