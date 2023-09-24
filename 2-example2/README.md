## Example 02

### Build and run image file
- `docker build .`

### Start container with interactive shell
- `docker run -it 7080`, runs in interactive shell (-i interactive, -t tty (teletypewriter/terminal))

### Remove container
- `docker rm 7080`, removes container
- `docker images`, list all images
- `docker rmi 7080`, removes image, only with not used from any container (stop/running)
- `docker container prune`, removes unused images