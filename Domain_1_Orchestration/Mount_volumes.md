# Mount volumes

## Official Docker Documentation
[How to give Docker Swarm Services access to Volumes or Bind Mounts](https://docs.docker.com/engine/swarm/services/#give-a-service-access-to-volumes-or-bind-mounts)  

For best performance and portability, you should avoid writing important data directly into a container’s writable layer, instead using data volumes or bind mounts.

### DATA VOLUMES

```bash
$ docker service create \
  --mount src=<VOLUME-NAME>,dst=<CONTAINER-PATH> \
  --name myservice \
  <IMAGE>

$ docker service create \
  --mount type=volume,src=<VOLUME-NAME>,dst=<CONTAINER-PATH>,volume-driver=<DRIVER>,volume-opt=<KEY0>=<VALUE0>,volume-opt=<KEY1>=<VALUE1>
  --name myservice \
  <IMAGE>  
```

### BIND MOUNTS

Important: Bind mounts can be useful but they can also cause problems. In most cases, it is recommended that you architect your application such that mounting paths from the host is unnecessary

```bash
$ docker service create \
  --mount type=bind,src=<HOST-PATH>,dst=<CONTAINER-PATH> \
  --name myservice \
  <IMAGE>

  $ docker service create \
  --mount type=bind,src=<HOST-PATH>,dst=<CONTAINER-PATH>,readonly \
  --name myservice \
  <IMAGE>
```