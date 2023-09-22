## Example 01

### Build and run image file
- `docker build .`
- There will be an id of image in success information
- `Successfully built c690e4739ba0`
- Copy it and run
- `docker run c690e4739ba0`
- It will start the webapp on port 3000

### Stop docker
- Turn on another terminal, run command to list all docker processes
- `docker ps`
- Copy the running webapp docker id
- e.g. `fa56244d0d4c   c690e4739ba0    "docker-entrypoint.s…"   19 seconds ago   Up 18 seconds   0.0.0.0:3000->3000/tcp, :::3000->3000/tcp  ...`
- Then stop it
- `docker stop fa56244d0d4c`