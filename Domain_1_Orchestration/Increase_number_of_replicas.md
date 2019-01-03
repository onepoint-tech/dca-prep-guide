# Increase number of replicas

Scaling works only on replicated: 
- `docker service scale SERVICE=NUMBER`
- works also for many service : `docker service scale SERVICE1=NUMBER1 SERVICE2=NUMBER2 [...]`
- `docker service update --replicas=NUMBER SERVICE`

## Official Docker Documentation
[Service Scale](https://docs.docker.com/engine/reference/commandline/service_scale/#examples)
