# Apply node labels to demonstrate placement of tasks

## Official Docker Documentation
[Create Labels on Docker Swarm Nodes](https://docs.docker.com/engine/reference/commandline/node_update/)

```bash
docker node update --label-add foo --label-add bar worker1
docker node update --label-add type=queue worker1
```

[Specifiy Services Placement Constraints](https://docs.docker.com/engine/swarm/services/#placement-constraints)

```bash
docker service create \
  --name my-nginx \
  --constraint node.labels.region==east \
  nginx
  ```

**global** services : the scheduler places one task on each available node that meets the service’s placement constraints and resource requirements
```bash
docker service create \
  --name my-nginx \
  --mode global \
  --constraint node.labels.region==east \
  --constraint node.labels.type!=devel \
  nginx
```

[Specifiy Services Placement Preferences](https://docs.docker.com/engine/swarm/services/#placement-preferences)

```bash
docker service create \
  --replicas 9 \
  --name redis_2 \
  --placement-pref 'spread=node.labels.datacenter' \
  redis:3.0.6
```


## Preparation Hints
There exists the possibilty to add custom labels on nearly every Docker Object: [Manage labels on objects](https://docs.docker.com/engine/userguide/labels-custom-metadata/#manage-labels-on-objects)
 - Images and containers
 - Local Docker daemons
 - Volumes
 - Networks
 - Swarm nodes
 - Swarm services
 
```--label```