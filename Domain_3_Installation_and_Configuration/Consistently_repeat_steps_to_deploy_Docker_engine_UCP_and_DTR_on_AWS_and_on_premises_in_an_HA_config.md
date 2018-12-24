# Consistently repeat steps to deploy Docker engine UCP and DTR on AWS and on premises in an HA config

## Official Docker Documentation
[Install Docker Trusted Registry](https://docs.docker.com/datacenter/dtr/2.3/guides/admin/install/)  
[Install UCP for production](https://docs.docker.com/datacenter/ucp/2.2/guides/admin/install/)  
[Docker for AWS setup & prerequisites](https://docs.docker.com/docker-for-aws/)  


### DTR Health check

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