# Sketch how a Dockerized application communicates with legacy systems


## Official Docker Documentation
[Understanding Docker Container Communication](https://docs.docker.com/engine/userguide/networking/default_network/container-communication/)  

### Published ports

```--publish or -p```

### IP address and hostname
When the container starts, it can only be connected to a single network, using ```--network```. However, you can connect a running container to multiple networks using docker network connect
```docker network connect```

### DNS services
By default, a container inherits the DNS settings of the Docker daemon, including the ```/etc/hosts``` and ```/etc/resolv.conf```

```
--dns
--dns-search
--dns-opt
--hostname
```