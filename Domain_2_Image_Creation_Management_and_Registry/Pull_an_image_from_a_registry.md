# Pull an image from a registry

## Official Docker Documentation
[docker pull](https://docs.docker.com/engine/reference/commandline/pull/)  
- --all-tags , -a	:	Download all tagged images in the repository
- --disable-content-trust	true :	Skip image verification
- --platform : Set platform if server is multi-platform capable


[Pull from a private/different registry](https://docs.docker.com/engine/reference/commandline/pull/#pull-from-a-different-registry)  

```docker pull myregistry.local:5000/testing/test-image```

