## Example 07 - node utils

### Build and run image file
- `docker build -t node-util`: build node utils image
- `docker run -it -v $(pwd):/app node-util npm init`: run node utils image and run command `npm init` in interactive mode
- `docker run -it -v $(pwd):/app node-util init`: run node utils image and run command `init` in interactive mode (no npm live above because we already add ENTRYPOINT in dockerfile)
- Use docker compose
  - `docker-compose run npm init`: run command `init` in interactive mode
  - or `docker-compose run --rm npm init`