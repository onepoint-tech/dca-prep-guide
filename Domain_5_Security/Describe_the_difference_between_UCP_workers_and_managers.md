# Describe the difference between UCP workers and managers

## Official Docker Documentation
[Under the hood](https://docs.docker.com/datacenter/ucp/2.2/guides/architecture/#under-the-hood)

Components on manager :

- **ucp-agent** : Monitors the node and ensures the right UCP services are running (also on worker only)
- **ucp-dsinfo** : Docker system information collection script to assist with troubleshooting (also on worker only)
- **ucp-reconcile** : When ucp-agent detects that the node is not running the right UCP components, it starts the ucp-reconcile container to converge the node to its desired state. It is expected for the ucp-reconcile container to remain in an exited state when the node is healthy. (also on worker only)
- **ucp-auth-api** : The centralized service for identity and authentication used by UCP and DTR
- **ucp-auth-store** : Stores authentication configurations and data for users, organizations, and teams
- **ucp-auth-worker** : Performs scheduled LDAP synchronizations and cleans authentication and authorization data
- **ucp-client-root-ca** : A certificate authority to sign client bundles
- **ucp-cluster-root-ca** : A certificate authority used for TLS communication between UCP components
- **ucp-controller** : The UCP web server
- **ucp-dsinfo** : Docker system information collection script to assist with troubleshooting
- **ucp-kv** : Used to store the UCP configurations. Don’t use it in your applications, since it’s for internal use only
- **ucp-metrics** : Used to collect and process metrics for a node, like the disk space available
- **ucp-proxy** : A TLS proxy. It allows secure access to the local Docker Engine to UCP components
- **ucp-swarm-manager** : Used to provide backwards-compatibility with Docker Swarm

Components on worker :

- **ucp-agent** : same as manager
- **ucp-dsinfo** : same as manager
- **ucp-reconcile** : same as manager
- **ucp-proxy** : A TLS proxy. It allows secure access to the local Docker Engine to UCP components