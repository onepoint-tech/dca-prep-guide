# Demonstrate the usage of templates with docker service create

## Official Docker Documentation
[Create Docker Swarm Services using templates](https://docs.docker.com/engine/reference/commandline/service_create/#create-services-using-templates)  


 - .Service.ID
 - .Service.Name
 - .Service.Labels
 - .Node.ID
 - .Node.Hostname
 - .Task.ID
 - .Task.Name
 - .Task.Slot

 ```bash
$ docker service create --name hosttempl \
                        --hostname="{{.Node.Hostname}}-{{.Node.ID}}-{{.Service.Name}}"\
                         busybox top

va8ew30grofhjoychbr6iot8c

$ docker inspect --format="{{.Config.Hostname}}" 2e7a8a9c4da2-wo41w8hg8qanxwjwsg4kxpprj-hosttempl

```