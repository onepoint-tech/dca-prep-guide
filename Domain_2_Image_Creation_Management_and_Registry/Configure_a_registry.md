# Configure a registry

## Official Docker Documentation
[Configuring a registry](https://docs.docker.com/registry/configuration/)  

### Override specific configuration options

Exemple of config that will be override
```bash
storage:
  filesystem:
    rootdirectory: /var/lib/registry
```

To override this value, set an environment variable like this: ```REGISTRY_STORAGE_FILESYSTEM_ROOTDIRECTORY=/somewhere```

### Overriding the entire configuration file

```bash
$ docker run -d -p 5000:5000 --restart=always --name registry \
             -v `pwd`/config.yml:/etc/docker/registry/config.yml \
             registry:2
```