# Modify an image to a single layer

## Official Docker Documentation

### Without rebuilding
- create a container from the image: [docker create](https://docs.docker.com/engine/reference/commandline/create/)

The docker create command creates a writeable container layer over the specified image and prepares it for running the specified command. The container ID is then printed to STDOUT. This is similar to ```docker run -d``` except the container is never started. You can then use the ```docker start <container_id>``` command to start the container at any point.

- export the container to a flattened tar: [docker container export](https://docs.docker.com/engine/reference/commandline/export/) 
```bash
docker export red_panda > latest.tar
docker export --output="latest.tar" red_panda 
```
- load the image back from the tarball: [docker image import](https://docs.docker.com/engine/reference/commandline/image_import/)  





### With rebuilding
See the `--squash` option of [docker build](https://docs.docker.com/engine/reference/commandline/build/#options)  
Squash newly built layers into a single new laye

## Third party resources
[Flatten a Docker container or image](https://tuhrig.de/flatten-a-docker-container-or-image/)

A Docker image can be saved to a tarball and loaded back again. This will preserve the history of the image.
```bash
# save the image to a tarball
docker save <IMAGE NAME> > /home/save.tar
 
# load it back
docker load < /home/save.tar
```

A Docker container can be exported to a tarball and imported back again. This will not preserve the history of the container.
```bash
# export the container to a tarball
docker export <CONTAINER ID> > /home/export.tar
 
# import it back
cat /home/export.tar | docker import - some-name:latest
```

Flatten a Docker container :
```bash
docker export <CONTAINER ID> | docker import - some-image-name:latest
```