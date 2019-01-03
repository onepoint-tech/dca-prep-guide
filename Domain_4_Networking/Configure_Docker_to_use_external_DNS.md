# Configure Docker to use external DNS

## Official Docker Documentation
[Configure DNS](https://docs.docker.com/engine/reference/commandline/dockerd/#daemon-dns-options)  

To set the DNS server for all Docker containers, use: ```sudo dockerd --dns 8.8.8.8```

To set the DNS search domain for all Docker containers, use: ```sudo dockerd --dns-search example.com```
