# Consistently repeat steps to deploy Docker engine UCP and DTR on AWS and on premises in an HA config

## Official Docker Documentation
[Install UCP for production](https://docs.docker.com/datacenter/ucp/2.2/guides/admin/install/)  
[Install Docker Trusted Registry](https://docs.docker.com/datacenter/dtr/2.3/guides/admin/install/)  
[Docker for AWS setup & prerequisites](https://docs.docker.com/docker-for-aws/)  

### UCP

1. Validate the system requirements
2. Install Docker EE on all nodes
3. Customize named volumes
4. Install UCP ```docker container run --rm -it -v /var/run/docker.sock:/var/run/docker.sock docker/ucp:2.2.14 install --host-address <node-ip-address> --interactive```
5. License your installation
6. Join manager nodes
7. Join worker nodes

### DTR 

Since DTR requires Docker Universal Control Plane (UCP) to run, you need to install UCP on all the nodes where you plan to install DTR.

```bash
docker run -it --rm \
  docker/dtr:2.6.0 install \
  --ucp-node <ucp-worker-name> \
  --ucp-url <manager-url>
  --ucp-insecure-tls
```

#### DTR Health check

https://docs.docker.com/ee/dtr/admin/configure/use-a-load-balancer/

You can use the unauthenticated **/_ping** endpoint on each DTR replica, to check if the replica is healthy and if it should remain in the load balancing pool or not.

endpoints exposed by Docker Trusted Registry that can be used to assess the health of a Docker Trusted Registry replica :
- /_ping
- /health
- /nginx_status
- /api/v0/meta/cluster_status

**NOT** :
- /api/health
- /replica_status
- /nginx/health

### AWS

Important update: Docker Enterprise for AWS is being deprecated. The Docker recommended approach to deploy Docker Enterprise on AWS is the new Docker Certified Infrastructure for AWS. https://success.docker.com/article/certified-infrastructures-aws
