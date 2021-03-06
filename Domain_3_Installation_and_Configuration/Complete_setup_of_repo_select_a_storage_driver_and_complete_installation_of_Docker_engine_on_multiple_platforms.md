# Complete setup of repo, select a storage driver and complete installation of Docker engine on multiple platforms

## Official Docker Documentation
Choosing and setting up the source for installing Docker EE - usually a repo - is described in the documentation for getting Docker EE.
There you also find the exact commands that you need to follow to install the Docker EE engine.

[Oracle Linux](https://docs.docker.com/install/linux/docker-ee/oracle/)  
[Red Hat Enterprise Linux](https://docs.docker.com/install/linux/docker-ee/rhel/)  
[SUSE SLES](https://docs.docker.com/install/linux/docker-ee/suse/)  
[Cent OS](https://docs.docker.com/install/linux/docker-ee/centos/)  
[Ubuntu](https://docs.docker.com/install/linux/docker-ee/ubuntu/)  
[Windows Server 2016](https://docs.docker.com/install/windows/docker-ee/)  

The information about the supported storage drivers for production workloads can be found in the [Product Compatibility Matrix](https://success.docker.com/Policies/Compatibility_Matrix).
How to configure which storage driver is used is also described in the installation guide of each operating system.

[Configuredevice mapper](https://docs.docker.com/storage/storagedriver/device-mapper-driver/)

## sumamry

- get the URL of our private repos from https://hub.docker.com/my-content
- add this repo to the package manager
  - ubuntu : ```add-apt-repository```
  - RHEL : 
    - ```sudo -E yum-config-manager --add-repo     "$DOCKERURL/rhel/docker-ee.repo"```
- install requirements
  - on RHEL ```sudo yum install -y yum-utils  device-mapper-persistent-data lvm2```
- configure device mapper (if used)
  -  add ```"storage-driver": "devicemapper"``` to ```/etc/docker/daemon.json```