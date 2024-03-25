## Multi-stage Builds

- Every FROM instruction creates a new stage in your Dockerfile
- build with specified Dockerfile name
  - ```docker build -f frontend/Dockerfile.prod -t halntit/goals-react ./frontend```

### Container using Load balancer

- Get IP address from subnet/listener
- Fix LB issue:
  - Careful on Target group section in Load balancer when creating service
  - If failed in attaching LB to a service, should re-create it, updating does not work

### Different between normal and alpine system

* You can use the normal image, since it is based on the "buildpack-deps", which is *commonly used by a lot of images* .
* Alpine images very small and reduce the amount of needed memory. Especially there is no other type of installation of the docker container.

In general, **yes alpine images are better than the official node images** which comes with pre-baked binaries.

But this is highly case specific.

1. If you have heavy customization, you might still end up adding dependencies even with the official node image.
2. If you don't have a lot of customization, adding small dependencies to node alpine will not cost you much in terms of size and build time when compared to official node images.
3. If you are having complicated dependencies (sometimes docs can be poor), things will work fine in the official node image but you will need to go out of your way to get things working in node alpine and still it will be unstable. (This happened to me once with `libpng16-dev` package and it worked only with the official node image and I couldn't figure out why it didn't work with node alpine even after trying for days).
