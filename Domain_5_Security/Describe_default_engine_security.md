# Describe default engine security

## Official Docker Documentation
[Secure Engine](https://docs.docker.com/engine/security/)

- configure Docker’s trust features so that your users can push and pull trusted images. To learn how to do this, see Use trusted images in this section.
- protect the Docker daemon socket and ensure only trusted Docker client connections. For more information, Protect the Docker daemon socket
- use certificate-based client-server authentication to verify a Docker daemon has the rights to access images on a registry. For more information, see Using certificates for repository client verification.
- configure secure computing mode (Seccomp) policies to secure system calls in a container. For more information, see Seccomp security profiles for Docker.
- An AppArmor profile for Docker is installed with the official .deb packages. For information about this profile and overriding it, see AppArmor security profiles for Docker.

[Docker security](https://docs.docker.com/engine/security/security/)

- Kernel namespaces
- Control groups
- Docker daemon attack surface
- Linux kernel capabilities
- Docker Content Trust Signature Verification
- Other kernel security features : AppArmor, SELinux, ...