## Example 03

### Build and run image file
- `docker build -t fn .` (favourite nodes)

### Run
- `docker run --name fav -d --rm -p 3000:3000 fn`
- `docker network create <net-name>`
- `docker run --network my-network --name fav -d --rm -p 3000:3000 fn`: within a Docker network, all containers can communicate with each other and IP addresses are automatically resolved