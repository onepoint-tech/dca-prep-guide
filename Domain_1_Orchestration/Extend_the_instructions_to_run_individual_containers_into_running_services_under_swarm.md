# Extend the instructions to run individual containers into running services under swarm

## Official Docker Documentation
[How to run a service under Docker Swarm](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)  

```bash
$ docker service create --replicas 1 --name helloworld alpine ping docker.com

$ docker service ls

ID            NAME        SCALE  IMAGE   COMMAND
9uk4639qpg7n  helloworld  1/1    alpine  ping docker.com
```