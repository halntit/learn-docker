## Multi-stage Builds
- Every FROM instruction creates a new stage in your Dockerfile
- build with specified Dockerfile name
    - ```docker build -f frontend/Dockerfile.prod -t halntit/goals-react ./frontend```

### Container using Load balancer
- Get IP address from subnet/listener
- Fix LB issue:
  - Careful on Target group section in Load balancer when creating service
  - If failed in attaching LB to a service, should re-create it, updating does not work