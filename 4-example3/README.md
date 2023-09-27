## Example 03

### Build and run image file
- `docker build .`

### Volume
- Volumes are folders on your host machine that are mounted/mapped to folders on your container
- `docker run -v /path/to/folder:/path/to/mapped/folder`
  - `docker run -p 3000:80 -d --name fba -v /feedback:/app/feedback --rm 0f99`
- 3 ways to use volumes
  - `docker run -v /app/data`: anonymous
  - `docker run -v data:/app/data`: named volume
  - `docker run -v /path/to/code:/app/code`: bind mount
- Read-only volumes
  - `docker run -v /path/to/code:/app/code:ro`

### Bind Mounts - Shortcuts
- options: `-v $(pwd):/app`