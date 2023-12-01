## Example 09 - deployment with docker to EC2

### Build and push image to Docker Hub
- `docker build -t aws-ec2-10 .`: build image
- `docker tag aws-ec2-10 halntit/aws-ec2`: create a tag (matching tag on docker Hub)
- `docker push halntit/aws-ec2`: push image to Docker hub

### Run container
- `ssh ec2-user@54.254.90.16 -i propextra-dev-ap-southeast-1.pem`: ssh to EC2
- Download docker
  - `sudo yum update -y`
  - `sudo yum -y install docker`
  - `sudo service docker start`
  - `sudo usermod -a -G docker ec2-user`
  - `sudo systemctl enable docker`
  - `docker version`
- Log out and back in EC2 instance
- `docker run -d --rm -p 80:80 halntit/aws-ec2`
- EC2: open inbound for port 80, 8000 on EC2 instance

### Update container on EC2
- Update codes locally
- Rebuild image, tag and push to Docker Hub
- EC2:
  - `docker stop <containerID>`
  - `docker pull halntit/aws-ec2`
  - `docker run -d --rm -p 80:80 halntit/aws-ec2`

### Managed service (AWS ECS)
https://aws.amazon.com/getting-started/hands-on/deploy-docker-containers/

### Update container on ECS
- Update codes locally
- Rebuild image, tag and push to Docker Hub
- ECS:
  - Create new revision for task
  - Update service (with the same settings)
