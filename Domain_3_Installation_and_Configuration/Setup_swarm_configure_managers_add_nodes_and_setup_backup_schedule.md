# Setup swarm, configure managers, add nodes, and setup backup schedule

## Official Docker Documentation

- [Create a swarm](https://docs.docker.com/engine/swarm/swarm-tutorial/create-swarm/)
  - ```docker swarm init --advertise-addr <MANAGER-IP>```
- [Add nodes to a swarm](https://docs.docker.com/engine/swarm/swarm-tutorial/add-nodes/) :
  - ```docker swarm join --token  SWMTKN-XXX  192.168.99.100:2377```
- [Back up a swarm](https://docs.docker.com/engine/swarm/admin_guide/#back-up-the-swarm)  
  1. If the swarm has auto-lock enabled, you need the unlock key to restore the swarm from backup.
  2. Stop Docker on the manager before backing up the data
  3. Back up the entire ```/var/lib/docker/swarm``` directory.
  4. Restart the manager.