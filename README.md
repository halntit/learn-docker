# learn-docker

### Notes
- EXPOSE 80 in the Dockerfile in the end is optional, but recommended (best practice)
- For all docker commands where an ID can be used, you don't always have to copy / write out the full id, just few first charaters is enough
  - instead of ``docker run abcdefg``, you could also run ``docker run abc``, or even ``docker run a`` if there are no other ID starting with 'a'
- Images are read only, you can't write to them. Need to rebuild them for changes