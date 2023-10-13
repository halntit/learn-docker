# learn-docker

### Notes
- EXPOSE 80 in the Dockerfile in the end is optional, but recommended (best practice)
- For all docker commands where an ID can be used, you don't always have to copy / write out the full id, just few first charaters is enough
  - instead of ``docker run abcdefg``, you could also run ``docker run abc``, or even ``docker run a`` if there are no other ID starting with 'a'
- Images are read only, you can't write to them. Need to rebuild them for changes
- Every instruction in an image creates a cacheable layer - layers help with image re-building and sharing
- By default, if you run a Container without -d, you run in "attached mode"
- Use copy files/folders from container to local folders for review logs
- When start / run a container with the --rm option, anonymous volume will be removed automatically. Without that option, it will not removed even if remove its container
- Volumes: local files will overwrite container files, not the other way around (container never overwrite local files)
- Volumes: `-v /path/to/folder:/path/to/mapped/folder` has volume name, while `-v /app/node_modules` is anonymous volume
- Volumes: in Dockerfile this `VOLUME [ "app/node_modules" ]` is equivalent to anonymous volume in cli `-v /app/node_modules`
- Send requests from container to WWW just works (no need configs)
- `host.docker.internal` is localhost / host machine used by docker
  - `host.docker.internal` for Windows and MacOS, `localhost`(host mode)/`172.18.0.1`(bridge mode) for Linux
- mongodb:
  - use docker: `docker pull mongodb/mongodb-community-server`
  - run docker: `docker run --name mongo --rm -p 27017:27017 mongodb/mongodb-community-server:latest`
  - data stored: /data/db
  - add creds: `docker run --name mongo --rm -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password -p 27017:27017 mongodb/mongodb-community-server:latest`
- run `docker inspect <container id>` to view the container details, including IP addresses
- docker compose:
  - named volumes must be declared here: `volumes:`
- untilities:
  - `docker exec ...`: allow to run command in running container