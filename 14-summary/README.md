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
    - Isolated, encapsulated, reproducible development environments
    - No dependency or software clashes
  - Remote host / Production
    - Isolated, encapsulated, reproducible environments
    - Easy updates: Simply replace a running container with an updated one

## Deployment Is Optional!
  - It’s perfectly fine to use Docker (and Docker Compose) for local development!
    - `Encapsulated` environments for different projects
    - `No global` installation of tools
    - `Easy to share` and re-produce

## Deployment Considerations
  - Replace `Bind Mounts` with `Volumes` or `COPY`
  - Multiple containers might need multiple hosts
    But they can also run on the same host (depends on application)
  - `Multi-stage builds` help with apps that need a `build step`
  - Control vs Ease-of-use
    - You can `launch a remote server, install Docker` and run your containers
      Full control but you also need to manage everything
    - You can use a `managed service` (AWS ECS) instead
      Less control and extra knowledge required but easier to use, less responsibility