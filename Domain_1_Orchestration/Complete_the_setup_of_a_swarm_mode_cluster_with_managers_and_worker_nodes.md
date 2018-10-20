# Complete the setup of a swarm mode cluster with managers and worker nodes

## Official Docker Documentation
[Create a Docker Swarm cluster](https://docs.docker.com/engine/swarm/swarm-tutorial/create-swarm/)  

```bash
docker swarm init --advertise-addr <MANAGER-IP>
docker node ls
```

[Add nodes to the Docker Swarm cluster](https://docs.docker.com/engine/swarm/swarm-tutorial/add-nodes/)

On the master
```bash
docker swarm join-token worker
```

On Workers 
```bash
docker swarm join \
  --token  SWMTKN-1-49nj1cmql0jkz5s954yi3oex3nedyz0fb0xx14ie39trti4wxv-8vxv8rssmk743ojnwacrr2e7c \
  192.168.99.100:2377
```