## Multi-stage Builds
- Every FROM instruction creates a new stage in your Dockerfile
- build with specified Dockerfile name
    - ```docker build -f frontend/Dockerfile.prod -t halntit/goals-react ./frontend```

### Container using Load balancer
- Get IP address from subnet/listener