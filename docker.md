# Docker

## Delete all images for repo `myorg/myimage` before version `x.y.z`

Useful for managing disk space in CI environments.

```
VERSION=1.0.0
REPO_NAME=something.amazonaws.com/myorg/myimage
TAG_NAME=$REPO_NAME:$VERSION
OLD_IMAGES=$(docker images -a -q --filter=before="$TAG_NAME" --filter=reference="$REPO_NAME")
docker rmi $OLD_IMAGES
```

## Build a Dockerfile without a build context

Useful if you don't need a build context. Copying the entire current directory wastes time.

```
docker build -t myimage:latest - < Dockerfile
``` 
