# Describe the different types and use cases for the built-in network drivers

## Official Docker Documentation
[Understanding Docker Networking Drivers Use Cases](https://blog.docker.com/2016/12/understanding-docker-networking-drivers-use-cases/)  
[Portable Container Networks: Docker Native Network Drivers](https://success.docker.com/article/networking)  
[Network drivers](https://docs.docker.com/network/#network-drivers)

- Bridge
- Overlay (based on VXLAN)
- MacVLAN
  - offers several unique characteristics
    - lightweight, because rather than using any Linux bridging or port mapping, it connects container interfaces directly to host interfaces. 
    - Containers are addressed with routable IP addresses that are on the subnet of the external network.
  - As a result of routable IP addresses, containers communicate directly with resources that exist outside a Swarm cluster without the use of NAT and port mapping. 
    - This can aid in network visibility and troubleshooting. 
    - the direct traffic path between containers and the host interface helps reduce latency. macvlan is a local scope network driver which is configured per-host.
    - As a result, there are stricter dependencies between MACVLAN and external networks, which is both a constraint and an advantage that is different from overlay or bridge.