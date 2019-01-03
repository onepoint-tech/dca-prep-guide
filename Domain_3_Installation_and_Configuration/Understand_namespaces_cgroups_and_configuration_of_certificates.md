# Understand namespaces, cgroups and configuration of certificates

## Official Docker Documentation
[Namespaces](https://docs.docker.com/engine/docker-overview/#namespaces)  
[Controlgroups](https://docs.docker.com/engine/docker-overview/#control-groups)  
[Protect the Docker daemon socket](https://docs.docker.com/engine/security/https/)  

### Namespaces

Namespaces provide isolated workspace called the container. When you run a container, Docker creates a set of namespaces for that container.
These namespaces provide a layer of isolation. Each aspect of a container runs in a separate namespace and its access is limited to that namespace.

Docker Engine uses namespaces such as the following on Linux:

- **pid** : Process isolation (PID: Process ID).
- **net** : Managing network interfaces (NET: Networking).
- **ipc** : Managing access to IPC resources (IPC: InterProcess Communication).
- **mnt** : Managing filesystem mount points (MNT: Mount).
- **uts** : Isolating kernel and version identifiers. (UTS: Unix Timesharing System).

### Controlgroups

Docker Engine on Linux also relies on another technology called control groups (cgroups). A cgroup limits an application to a specific set of resources. Control groups allow Docker Engine to share available hardware resources to containers and optionally enforce limits and constraints. For example, you can limit the memory available to a specific container.

### Protect the Docker daemon socket

By default, Docker runs through a non-networked UNIX socket. It can also optionally communicate using an HTTP socket.
If you need Docker to be reachable through the network in a safe manner, you can enable TLS by specifying the tlsverify flag and pointing Docker’s tlscacert flag to a trusted CA certificate.

```dockerd --tlsverify --tlscacert=ca.pem --tlscert=server-cert.pem --tlskey=server-key.pem -H=0.0.0.0:2376```