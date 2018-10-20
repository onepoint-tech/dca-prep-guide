# State the differences between running a container vs running a service

## Official Docker Documentation
[Docker run](https://docs.docker.com/engine/reference/commandline/run/#parent-command) 

The docker run command first creates a writeable container layer over the specified image, and then starts it using the specified command. 

[Docker services](https://docs.docker.com/engine/swarm/how-swarm-mode-works/services/#services-tasks-and-containers)

![](https://docs.docker.com/engine/swarm/images/services-diagram.png)

## Third Party Resources
[What is the difference between Docker Service and Docker Container?](https://stackoverflow.com/a/43408904)

When you create a service, you specify which container image to use and which commands to execute inside running containers. You also define options for the service including:

- the port where the swarm will make the service available outside the swarm
- an overlay network for the service to connect to other services in the swarm
- CPU and memory limits and reservations 
- a rolling update policy
- the number of replicas of the image to run in the swarm