# Describe how volumes are used with Docker for persistent storage


### Official Docker Documentation
[Use volumes](https://docs.docker.com/engine/admin/volumes/volumes/)


## Summary 

https://docs.docker.com/storage/

- **Volumes** are stored in a part of the host filesystem which is managed by Docker (/var/lib/docker/volumes/ on Linux). Non-Docker processes should not modify this part of the filesystem. Volumes are the best way to persist data in Docker.
  - can be declare with ```-v``` or ```--mount``` command. Originally, the ```-v``` or ```--volume``` flag was used for standalone containers and the ```--mount``` flag was used for swarm services. However, starting with Docker 17.06, you can also use ```--mount``` with standalone containers.

- **Bind mounts** may be stored anywhere on the host system. They may even be important system files or directories. Non-Docker processes on the Docker host or a Docker container can modify them at any time.

- **tmpfs** mounts are stored in the host system’s memory only, and are never written to the host system’s filesystem.
