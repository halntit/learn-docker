## Example 01

### Build and run image file
- `docker build .`
- There will be an id of image in success information
- `Successfully built ffe5b0401d1f`
- Copy it and run
- `docker run ffe5b0401d1f`
- It will start the webapp on port 80
- `docker run -p 3000:80 ffe5b0401d1f`
- It will start the webapp on local port 3000 match with port 80 in the container

### Stop docker
- Turn on another terminal, run command to list all docker processes
- `docker ps`
- Copy the running webapp docker id
- e.g. `fa56244d0d4c   ffe5b0401d1f    "docker-entrypoint.s…"   19 seconds ago   Up 18 seconds   0.0.0.0:3000->3000/tcp, :::3000->3000/tcp  ...`
- Then stop it
- `docker stop fa56244d0d4c`

### Restart container
- `docker start fa56244d0d4c`, restart the container (in detached mode)
- `docker ps`