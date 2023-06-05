# dockerfiles
> Personal Dockerfiles

### build
```
docker image build --tag ubuntu:0.1 /ubuntu/
```

### run
```
CONTAINER_NAME=younghoon
IMAGE_NAME=younghoon:0.3
MOUNT_DIR=/home1/irteam/younghoon/workspace

docker run -it --name $CONTAINER_NAME -v $MOUNT_DIR:/root/workspace $IMAGE_NAME
```
