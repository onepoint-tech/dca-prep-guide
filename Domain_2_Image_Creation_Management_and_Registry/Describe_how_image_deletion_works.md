# Describe how image deletion works

## Official Docker Documentation
[Images and Layers](https://docs.docker.com/engine/reference/commandline/image_prune/)

Depuis API 1.25
```bash
docker image prune [OPTIONS]
```
- --all , -a		Remove all unused images, not just dangling ones
- --filter		Provide filter values (e.g. ‘until=')
- --force , -f		Do not prompt for confirmation

```bash
docker image prune -a --force --filter "until=2017-01-04T00:00:00"
docker image prune -a --force --filter "until=240h"
docker image prune --filter="label!=maintainer=john"
```


## Third party resources
[Docker Tips: How to Delete All Docker Containers and Images](https://www.brianchristner.io/how-to-delete-all-docker-containers-and-images/)  

```docker rmi $(docker images -f "dangling=true" -q)```



[What are Docker <none>:<none> images?](https://www.projectatomic.io/blog/2015/07/what-are-docker-none-none-images/)  
image ```<none>:<none>``` soit des layer intermédiaires soit des Dangling image

