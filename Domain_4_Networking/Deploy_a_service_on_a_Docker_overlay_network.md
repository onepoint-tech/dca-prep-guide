# Deploy a service on a Docker overlay network

## Official Docker Documentation

[Publish a Service to the Default Routing Mesh in Docker Swarm](https://docs.docker.com/engine/swarm/services/#publish-a-services-ports-using-the-routing-mesh)  
[Connect a Service to an Overlay Network in Docker Swarm](https://docs.docker.com/engine/swarm/services/#connect-the-service-to-an-overlay-network)  


Deploy a service running three tasks on a 10-node swarm, any of the 10 nodes redirect call on port 8080 to one of the three nginx tasks (on port 80).

```bash
docker service create --name my_web \
                        --replicas 3 \
                        --publish published=8080,target=80 \
                        nginx
```

To PUBLISH A SERVICE’S PORTS DIRECTLY ON THE SWARM NODE : use ```--publish mode=host,target=80,published=8080```