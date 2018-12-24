# Demonstrate how to configure devicemapper

## Official Docker Documentation
[Configure Docker with the devicemapper storage driver](https://docs.docker.com/engine/userguide/storagedriver/device-mapper-driver/#configure-docker-with-the-devicemapper-storage-driver)  

Supported Distribution :

- RHEL 7.3 & 7.4 (not 7.5)
- Centos 7
- Oracle Linux 7.3

daemon.json example :

````json
{
  "storage-driver": "devicemapper",
  "storage-opts": [
    "dm.directlvm_device=/dev/xdf",
    "dm.thinp_percent=95",
    "dm.thinp_metapercent=1",
    "dm.thinp_autoextend_threshold=80",
    "dm.thinp_autoextend_percent=20",
    "dm.directlvm_device_force=false"
  ]
}
```