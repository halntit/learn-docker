## Example 05 - multiple containers

### Build and run image file
- `docker build -t mc .` (BE)
  - to make BE container connect to MongoDB docker on the same network, modify this code 'mongodb://localhost:27017/course-goals' to 'mongodb://mongo:27017/course-goals', which mongo is the name of the mongoDB docker container
- `docker build -t mc-fe .` (FE)

### Run
- mongoDB: `docker run --name mongo --rm --network mc mongodb/mongodb-community-server:latest`
- BE: `docker run --name mc --network mc -p 8000:8000 --rm mc` BE needs to connect to mongoDB in docker container network, publish port for FE to communicate
- FE: `docker run --name mc-fe -p 3000:3000 --rm mc-fe` FE don't need to connect to container network
- add creds for mongodb
  - `docker run --name mongo --rm -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=5ecr3t -p 27017:27017 mongodb/mongodb-community-server:latest`
  - update code
    - `mongoose.connect('mongodb://mongo:27017/course-goals', ...)` to `mongoose.connect('mongodb://admin:5ecr3t@mongo:27017/course-goals', ...)`