# Identify the steps needed to troubleshoot a service not deploying

## Official Docker Documentation
[Reasons for Pending Services in Docker Swarm](https://docs.docker.com/engine/swarm/how-swarm-mode-works/services/#pending-services)

- If all nodes are paused or drained, and you create a service, it is pending until a node becomes available. In reality, the first node to become available gets all of the tasks, so this is not a good thing to do in a production environment.
- You can reserve a specific amount of memory for a service. If no node in the swarm has the required amount of memory, the service remains in a pending state until a node is available which can run its tasks. If you specify a very large value, such as 500 GB, the task stays pending forever, unless you really have a node which can satisfy it.
- You can impose placement constraints on the service, and the constraints may not be able to be honored at a given time.

## Third Party Resources
[How to diagnose Service Problems](https://stackoverflow.com/a/41658522)

```bash
docker service ps <service-name>
docker inspect <task-id>
docker logs <container-id>
```