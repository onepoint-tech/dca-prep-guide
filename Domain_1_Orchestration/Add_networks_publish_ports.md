# Add networks publish ports

## Official Docker Documentation
[Publish network ports in a Docker Swarm](https://docs.docker.com/engine/swarm/services/#publish-ports)

- rely on the routing mesh (8080 port open on each node of the swarm cluster)

```bash
docker service create --name my_web \
                        --replicas 3 \
                        --publish published=8080,target=80 \
                        nginx
```                        

- publish a service task’s port directly on the swarm node

```bash
docker service create \
  --mode global \
  --publish mode=host,target=80,published=8080 \
  --name=nginx \
  nginx:latest
```   