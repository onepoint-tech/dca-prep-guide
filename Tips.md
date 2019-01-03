# Tips

- Where to configure docker daemon : ```/etc/docker/daemon.json```
- Directory to save to backup swarm : ```/var/lib/docker/swarm```

## Domain 1: Orchestration (25% of exam)

- publish port
  - --publish published=8080,target=80
  - --publish mode=host,target=80,published=8080
- label
  - docker node update --label-add
  - --constraint
  - --placement-pref
- swarm
  - docker swarm init --advertise-addr <MANAGER-IP>
  - (on master) : docker swarm join-token worker
  - (on worker) : docker swarm join --token SWMTKN-XXX MasterIP:2377
- quorum in a swarm
  - swarm can tolerate up to (N-1)/2 permanent failures
  - If the swarm loses the quorum of managers, the swarm cannot perform management tasks.
  - Even if a swarm loses the quorum of managers, swarm tasks on existing worker nodes continue to run
- communication with legacy systems
  - --publish or -p
  - --network
  - dns
```bash

# Swarm lock
docker swarm init --autolock
docker swarm update --autolock=true/false
socker swarm unlock
docker swarm unlock-key
docker swarm unlock-key --rotate

# Service
docker service create --replicas 1 --name helloworld alpine ping docker.com


# Service mode : replicated (default) vs. global
--mode	replicated or global

# scale a replicated service
docker service scale SERVICE=NUMBER
docker service update --replicas=NUMBER SERVICE

# Template
docker service create --name hosttempl \
                       --hostname="{{.Node.Hostname}}-{{.Node.ID}}-{{.Service.Name}}"\
                        busybox top

# Troubleshoot
docker service ps <service-name>
docker inspect <task-id>
docker logs <container-id>

# inspect (json by default)
docker service inspect --pretty helloworld
ID:		9uk4639qpg7npwf3fn2aasksr
Name:		helloworld
Service Mode:	REPLICATED
 Replicas:		1
Placement:
UpdateConfig:
 Parallelism:	1
ContainerSpec:
 Image:		alpine
 Args:	ping docker.com
Resources:
Endpoint Mode:  vip

# stack
docker stack deploy
docker stack ls
docker stack ps
docker stack rm
docker stack services

# data volumes
docker service create \
  --mount src=<VOLUME-NAME>,dst=<CONTAINER-PATH> \
  --name myservice \
  <IMAGE>

docker service create \
  --mount type=volume,src=<VOLUME-NAME>,dst=<CONTAINER-PATH>,volume-driver=<DRIVER>,volume-opt=<KEY0>=<VALUE0>,volume-opt=<KEY1>=<VALUE1>
  --name myservice \
  <IMAGE> 

# bind mounts
docker service create \
  --mount type=bind,src=<HOST-PATH>,dst=<CONTAINER-PATH> \
  --name myservice \
  <IMAGE>

docker service create \
  --mount type=bind,src=<HOST-PATH>,dst=<CONTAINER-PATH>,readonly \
  --name myservice \
  <IMAGE>

# DNS
--dns
--dns-search
--dns-opt
--hostname

```

## Domain 2: Image Creation, Management, and Registry (20% of exam)

- Dockerfile
  - instructions
    - ADD (file or url, unzip)
    - COPY (prefer copy over add)
    - ENV
    - EXPOSE
      - informs Docker that the container listens on the specified network ports at runtime
      - not actually publish the port
      - ucp by default use /udp
    - FROM
    - LABEL
    - STOPSIGNAL
    - USER
    - VOLUME
    - WORKDIR
  - main parts
    - FROM
    - LABEL
    - ADD
    - COPY
    - ENV
    - EXPOSE
    - STOPSIGNAL
    - USER
    - VOLUME
    - WORKDIR
    - CMD
    - ENTRYPOINT

Best practices :
- Exclude with .dockerignore
- Use multi-stage builds
- Don’t install unnecessary packages
- Decouple applications
- Minimize the number of layers
- Sort multi-line arguments
- Leverage build cache

Default location for image layer : /var/lib/docker/aufs/layers

Signing / Docker Content Trust (DCT)
- Currently, content trust is disabled by default. To enable it, set the DOCKER_CONTENT_TRUST environment variable to 1.
- When you push your first tagged image with DCT enabled, the docker client recognizes this is your first push and:
  - alerts you that it is creating a new root key
  - requests a passphrase for the root key
  - generates a root key in the ~/.docker/trust directory
  - requests a passphrase for the repository key
  - generates a repository key in the ~/.docker/trust directory

```bash
# image management
docker image ls
docker image rm
docker image prune
docker image inspect [OPTIONS] IMAGE [IMAGE...]

# filtre
docker image ls --filter "dangling=true"
docker image ls --filter "label=com.example.version"

# format 
docker images --format "{{.ID}}: {{.Repository}}"

# tag
docker image tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]

# push
docker image push [OPTIONS] NAME[:TAG]

# Display layers of a Docker image
docker history IMAGE-NAME[:TAG]

# Build
docker image build [OPTIONS] PATH | URL | -

# Modify an image to a single layer (without rebuilding) or use --squash option of docker build
docker create [OPTIONS] IMAGE
docker export <CONTAINER ID> | docker import - some-image-name:latest

# save an image to a tarball
docker save <IMAGE NAME> > /home/save.tar
# load it back
docker load < /home/save.tar

# deploy a registry
docker run -d -p 5000:5000 --name registry registry:2

# custom config
storage:
  filesystem:
    rootdirectory: /var/lib/registry

docker run -d -p 5000:5000 --restart=always --name registry \
             -v `pwd`/config.yml:/etc/docker/registry/config.yml \
             registry:2

# login Using STDIN prevents the password from ending up in the shell’s history, or log-files :
cat ~/my_password.txt | docker login --username foo --password-stdin

# search in registry
docker search [OPTIONS] TERM

# pull (option --all-tags , -a	 / --disable-content-trust	true :	Skip image verification / --platform : Set platform if server is multi-platform capable)
docker pull myregistry.local:5000/testing/test-image

# prune image
docker image prune -a --force --filter "until=2017-01-04T00:00:00"
docker image prune -a --force --filter "until=240h"
docker image prune --filter="label!=maintainer=john"
docker rmi $(docker images -f "dangling=true" -q)

# delete image (via DTR or with API) :
DELETE /v2/<name>/manifests/<reference>

```

## Domain 3: Installation and Configuration (15% of exam)

- engine setup
  - EE
    - add the private repos
    - configure device mapper (if used) : add "storage-driver": "devicemapper" to /etc/docker/daemon.json



```bash
# Upgrade UCP after the engine upgrade
docker container run ... docker/ucp:3.0.7 upgrade --interactive

# Configure Docker to start on boot
sudo systemctl enable docker

# install UCP
docker container run --rm -it -v /var/run/docker.sock:/var/run/docker.sock docker/ucp:2.2.14 install --host-address <node-ip-address> --interactive

# install DTR
docker run -it --rm \
  docker/dtr:2.6.0 install \
  --ucp-node <ucp-worker-name> \
  --ucp-url <manager-url>
  --ucp-insecure-tls

# backup DTR meta data
read -sp 'ucp password: ' UCP_PASSWORD; \
docker run --log-driver none -i --rm \
  --env UCP_PASSWORD=$UCP_PASSWORD \
  docker/dtr:2.5.6 backup \
  --ucp-url <ucp-url> \
  --ucp-insecure-tls \
  --ucp-username <ucp-username> \
  --existing-replica-id <replica-id> > dtr-metadata-backup.tar

# restore UCP (after uninstall-ucp)
docker container run ... docker/ucp:2.2.14 restore < /tmp/backup.tar
```

# Domain 4: Networking (15% of exam)

- -P option : publish all exposed port

Built in network driver :
- Bridge
- Overlay (based on VXLAN)
- MacVLAN (connects container interfaces directly to host interfaces)

Container Network Model (CNM) Constructs
- Sandbox
- Endpoint
- Network 

```bash

docker network create my-net
docker network rm my-net

docker create --name my-nginx \
  --network my-net \
  --publish 8080:80 \
  nginx:latest

docker network connect my-net my-nginx

docker network disconnect my-net my-nginx

docker network inspect

# display publish port
docker port `docker ps -q`
80/tcp -> 0.0.0.0:32768

# DNS
sudo dockerd --dns 8.8.8.8
sudo dockerd --dns-search example.com

```

## Domain 5: Security (15% of exam)


sign images in a way that UCP trusts them, you need to:
- Configure your Notary client
- Initialize trust metadata for the repository
- Delegate signing to the keys in your UCP client bundle

Using external cert with UCP and DTR
- via UI or during install ```--external-server-cert```

Grant = Subject + Role + Resource collections

```bash
# sign
export DOCKER_CONTENT_TRUST=1
docker push <dtr-domain>/<repository>/<image>:<tag>

# bundle
# 1 - Create an environment variable with the user security token
AUTHTOKEN=$(curl -sk -d '{"username":"<username>","password":"<password>"}' https://<ucp-ip>/auth/login | jq -r .auth_token)
# 2 - Download the client certificate bundle
curl -k -H "Authorization: Bearer $AUTHTOKEN" https://<ucp-ip>/api/clientbundle -o bundle.zip

```

## Domain 6: Storage and Volumes (10% of exam)

Configure device mapper
```json
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