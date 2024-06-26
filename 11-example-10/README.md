## Example 10 - deployment multi containers with docker to EC2

### Multi-container App
- Delete old service (above)
- Prepare apps

### How
- edit backend.env to add
    ```MONGODB_URL=```
- edit app.js to change from mongodb -> ${MONGODB_URL}
    ```mongoose.connect(`mongodb://...@${process.env.MONGODB_URL}:27017/course-goals?authSource=admin`,```
- build image
    ```docker build -t goals-node ./backend/```
- add tag
    ```docker tag goals-node halntit/goals-node```
- push to docker hub
    ```docker push halntit/goals-node```

### ECS
- services based on tasks -> create tasks first
- Create task definition
  - Add container for nodejs server
  - Add container for mongodb
  - (have issue on connecting from nodejs to mongodb)
- Use EFS for storing data
  - Mind the VPC
  - Mind the mount point (should be the same with local machine)
- Architecture

   |=======================================|
   | AWS   |            AWS ECS            |
   | LB    |-------------------------------|
   |       |            ECS TASK           |
   |       |-------------------------------|
   |       |   NODE APP    |    MongoDB    |
   |       |               |    -------    |
   |       |               |    | Vol |    |
   |       |               |    | EFS |    |
   |=======================================|  