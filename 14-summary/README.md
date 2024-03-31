# Docker and Container summary

## Containers
  - Isolated
  - Single-task-focused
  - Sharable, reproducible
  - Stateless (+ volumes)

## Images
  - Blueprints for Containers
  - Code + env
  - Read-only / does not run
  - Can be built + shared

## Key Commands
  - Build an image based on a Dockerfile
    - ```docker build -t NAME:TAG .```
      - ```NAME:TAG```: name and version
      - ```.```: build context
  - Run a container based on a remote or local image
    - ```docker run --name NAME --rm -d IMAGE```
      - ```--rm```: remove once stopped
      - ```-d```: detach mode
  - Share (push) an Image to a Registry (def: DockerHub)
    - ```docker push REPOSITORY/NAME:TAG```
  - Fetch (pull) an Image from a Registry (def: DockerHub)
    - ```docker pull REPOSITORY/NAME:TAG```

## Data, Volumes & Networking
  - Containers are isolated and stateless
    - Isolated: Containers have their own data and filesystem, detached from the host machine filesystem
      - Use `Bind Mounts` to connect host machine folders
      - -v /local/path:/container/path
    - Stateless: Data will be lost when container is removed
      - Use `Volumes` to persist data
      - -v NAME:/container/path

## Networks
  - Containers are isolated but can be connected to send requests to each other (e.g. HTTP)
    - Opt1: Determine container IP and use that: IP might changed, unnecessary work
    - Opt2: Create a Docker network and add both containers: containers can use each other's name as request addresses

## Docker compose
  - Docker run can be long and gets annoying
  - Docker compose allows to pre-define build and run configuration in a .yml file
    - ```docker-compose up```
    - ```docker-compose down```

## Local and Remote
  - Local host / Development
  - Remote host / Production
