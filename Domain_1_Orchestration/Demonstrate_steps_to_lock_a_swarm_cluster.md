# Demonstrate steps to lock a swarm cluster

## Official Docker Documentation
[How to lock your Docker Swarm to protect its encryption key](https://docs.docker.com/engine/swarm/swarm_manager_locking/)  

### Initialize a swarm with autolocking enabled

```bash
docker swarm init --autolock
```

### Enable or disable autolock on an existing swarm

```bash
docker swarm update --autolock=true
docker swarm update --autolock=false
```

### Unlock

```bash
docker swarm unlock
```

### View the current unlock key for a running swarm

```bash
docker swarm unlock-key
```

### Rotate the unlock key

```bash
docker swarm unlock-key --rotate
```