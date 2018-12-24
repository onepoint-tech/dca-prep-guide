# Describe swarm default security

## Official Docker Documentation
[Swarm mode overview](https://docs.docker.com/engine/swarm/)
- Each node in the swarm enforces **TLS mutual authentication** and **encryption to secure communications** between itself and all other nodes. You have the option to use *self-signed* root certificates or certificates from a *custom root CA*.

[Manage swarm security with public key infrastructure - PKI](https://docs.docker.com/engine/swarm/how-swarm-mode-works/pki/)

When you create a swarm by running ```docker swarm init```, Docker designates itself as a manager node. By default, the manager node generates a new root Certificate Authority (CA) along with a key pair, which are used to secure communications with other nodes that join the swarm. If you prefer, you can specify your own externally-generated root CA, using the ```--external-ca``` flag of the docker swarm init command.

In the event that a cluster CA key or a manager node is compromised, you can rotate the swarm root CA so that none of the nodes trust certificates signed by the old root CA anymore. ```docker swarm ca --rotate```. If you prefer, you can pass the ```--ca-cert``` and ```--external-ca``` flags to specify the root certificate and to use a root CA external to the swarm. Alternately, you can pass the ```--ca-cert``` and ```--ca-key``` flags to specify the exact certificate and key you would like the swarm to use.