# Paraphrase the importance of quorum in a swarm cluster

## Official Docker Documentation
[Maintain the Quorum of Managers](https://docs.docker.com/engine/swarm/admin_guide/#maintain-the-quorum-of-managers)

If the swarm loses the quorum of managers, the swarm cannot perform management tasks. If your swarm has multiple managers, always have more than two. To maintain quorum, a majority of managers must be available.

Even if a swarm loses the quorum of managers, swarm tasks on existing worker nodes continue to run. 


[Add Manager Nodes for Fault Tolerance](https://docs.docker.com/engine/swarm/admin_guide/#add-manager-nodes-for-fault-tolerance)  
[Recover from losing the Quorum](https://docs.docker.com/engine/swarm/admin_guide/#recover-from-losing-the-quorum)  
the swarm can tolerate up to (N-1)/2 permanent failures
