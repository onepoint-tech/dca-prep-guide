# Outline the sizing requirements prior to installation

## Official Docker Documentation
[Hardware and software requirements](https://docs.docker.com/datacenter/ucp/2.2/guides/admin/install/system-requirements/#hardware-and-software-requirements)  
[DTR requirements](https://success.docker.com/KBase/What_are_the_minimum_requirements_for_Docker_Trusted_Registry_(DTR)%3F)  
[UCP requirements](https://docs.docker.com/datacenter/ucp/2.2/guides/admin/install/system-requirements/)  
[Docker EE best practices and design considerations](https://success.docker.com/article/Docker_Reference_Architecture-_Docker_EE_Best_Practices_and_Design_Considerations_17_03)  

Minimum requirements
- 8GB of RAM for manager nodes or nodes running DTR
- 4GB of RAM for worker nodes
- 3GB of free disk space

Recommended production requirements
- 16GB of RAM for manager nodes or nodes running DTR
- 4 vCPUs for manager nodes or nodes running DTR
- 25-100GB of free disk space


### DTR

- RAM: Generally 4GB is considered sufficient for smaller production installations.
- DISK (DTR itself, not image storage): 20-30GB.
- DISK (image storage): ​ The requirements for the storage of Docker container images used in conjunction with DTR will scale linearly with the size and number of images, as well as how much I/O will be conducted.
- CPU: modern dual core processors are likely to be sufficient.