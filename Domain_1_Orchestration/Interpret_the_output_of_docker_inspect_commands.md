# Interpret the output of docker inspect commands

## Official Docker Documentation
[How to Inspect a running Service on Docker Swarm](https://docs.docker.com/engine/swarm/swarm-tutorial/inspect-service/) 

```docker service inspect --pretty <SERVICE-ID>```

```bash
docker service inspect --pretty helloworld

ID:		9uk4639qpg7npwf3fn2aasksr
Name:		helloworld
Service Mode:	REPLICATED
 Replicas:		1
Placement:
UpdateConfig:
 Parallelism:	1
ContainerSpec:
 Image:		alpine
 Args:	ping docker.com
Resources:
Endpoint Mode:  vip
```
