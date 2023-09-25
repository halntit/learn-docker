# learn-docker

### Notes
- EXPOSE 80 in the Dockerfile in the end is optional, but recommended (best practice)
- For all docker commands where an ID can be used, you don't always have to copy / write out the full id, just few first charaters is enough
  - instead of ``docker run abcdefg``, you could also run ``docker run abc``, or even ``docker run a`` if there are no other ID starting with 'a'
- Images are read only, you can't write to them. Need to rebuild them for changes
- Every instruction in an image creates a cacheable layer - layers help with image re-building and sharing
- By default, if you run a Container without -d, you run in "attached mode"
- Use copy files/folders from container to local folders for review logs
- 