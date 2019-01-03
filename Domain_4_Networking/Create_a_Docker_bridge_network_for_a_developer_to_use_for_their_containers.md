# Create a Docker bridge network for a developer to use for their containers

By default, Docker Engine connects container via a default bridge to the network of the node.
However, only overlay networks in a Swarm context let containers communicate further than the nodes network boundaries.
In special cases, own bridge networks can be added to i.e. allow for communication only between two special containers.

## Official Docker Documentation
[How to connect two containers via a private bridge](https://docs.docker.com/engine/userguide/networking/work-with-networks/#basic-container-networking-example)

[The extended description of Network Create](https://docs.docker.com/engine/reference/commandline/network_create/#extended-description)

[One can also change the default bridge of the Docker Engine](https://docs.docker.com/engine/userguide/networking/default_network/build-bridges/)

### user-defined bridges 

Differences between user-defined bridges and the default bridge :

- provide better isolation and interoperability :
  - Containers connected to the same user-defined bridge network automatically expose all ports to each other, and no ports to the outside world.
  - provide automatic DNS resolution between containers
  - Containers can be attached and detached from user-defined networks on the fly
  - Each user-defined network creates a configurable bridge (MTU, iptable rules)
  - Linked containers on the default bridge network share environment variables

Manage bridge

```bash
docker network create my-net
docker network rm my-net

docker create --name my-nginx \
  --network my-net \
  --publish 8080:80 \
  nginx:latest

docker network connect my-net my-nginx

docker network disconnect my-net my-nginx
```

By default, traffic from containers connected to the default bridge network is not forwarded to the outside world. To enable forwarding, you need to change two settings. These are not Docker commands and they affect the Docker host’s :
```bash
sysctl net.ipv4.conf.all.forwarding=1
sudo iptables -P FORWARD ACCEPT
```