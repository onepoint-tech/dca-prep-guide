# Use certificate-based client-server authentication to ensure a Docker daemon has the rights to access images on a registry

## Official Docker Documentation
[Verify repository client with certificates](https://docs.docker.com/engine/security/certificates/)  

ensure the traffic between the Docker registry server and the Docker daemon (a client of the registry server) is encrypted and properly authenticated using certificate-based client-server authentication.

custom certificate is configured by creating a directory under ```/etc/docker/certs.d``` using the same name as the registry’s hostname