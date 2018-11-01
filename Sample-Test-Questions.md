# Sample Test Questions

Q1. Which command is used to place an image into a registry?

- A. docker commit
- B. docker tag
- C. docker push
- D. docker images
- E. docker pull

<details>
  <summary>💡 Solution</summary>
C. docker push
</details>

---
Q2. Which network allows Docker Trusted Registry components running on different nodes to
communicate and replicate Docker Trusted Registry data?

- A. dtr-ol
- B. dtr-hosts
- C. dtr-br
- D. dtr-vlan

<details>
  <summary>💡 Solution</summary>
A. dtr-ol
</details>

---
Q3. Which of the following is not an endpoint exposed by Docker Trusted Registry that can be
used to assess the health of a Docker Trusted Registry replica?

- A. /health
- B. /nginx_status
- C. /api/v0/meta/cluster_status
- D. /replica_status
<details>
  <summary>💡 Solution</summary>
D. /replica_status
</details>


---
Q4. Which of the following endpoints exposed by Docker Trusted Registry can be used to
assess the health of a Docker Trusted Registry replica?

- A. /health
- B. /api/health
- C. /replica_status
- D. /nginx/health

<details>
  <summary>💡 Solution</summary>
A. /health
</details>


---
Q5. One of your developers is trying to push an image to the registry (dtr.example.com). The
push fails with the error “denied: requested access to the resource is denied”. What should you
verify the user has completed?

- A. ```docker login -u <username> -p <password> dtr.example.com```
- B. ```docker registry login -u username -p <password> dtr.example.com```
- C. ```docker push <username>/<image:tag> dtr.example.com```
- D. ```docker images login -u <username> -p <password> dtr.example.com```

<details>
  <summary>💡 Solution</summary>
A. docker login -u username -p password dtr.example.com
</details>

---
Q6. You have been asked to backup the swarm state on a Linux installation. By default, where do Docker manager nodes store the swarm state and manager logs?

- A. /var/run/docker/swarm
- B. /var/lib/docker/swarm
- C. /etc/docker/swarm
- D. /run/docker/swarm

<details>
  <summary>💡 Solution</summary>
B. /var/lib/docker/swarm  
</details>

---
Q7. Which of the following will put the Docker engine into debug mode?

- A. ```echo '{"debug": true}' > /var/lib/docker/daemon.json ; sudo kill -HUP <pid of dockerd>```
- B. ```echo '{"debug": true}' > /etc/docker/config.json ; sudo kill -HUP <pid of dockerd>```
- C.``` echo '{"debug": true}' > /var/lib/docker/config.json ; sudo kill -HUP <pid of dockerd>```
- D. ```echo '{"debug": true}' > /etc/docker/daemon.json ; sudo kill -HUP <pid of dockerd>```

<details>
  <summary>💡 Solution</summary>
D. /etc/docker/daemon.json
</details>

---
Q8. How do you deploy 4 new instances of nginx with a single command?

- A. docker service create --replicas 4 --name myservice nginx
- B. docker service create --instances 4 --name myservice nginx
- C. docker service scale myservice=4 nginx
- D. docker service scale --replicas 4 --name myservice nginx

<details>
  <summary>💡 Solution</summary>
A. docker service create --replicas 4 --name myservice nginx    
</details>

---
Q9. You are using self-signed UCP certs and have a second DNS name that points to your
internal controllers. When installing UCP, which flag should you use to add this additional
name?
- A. --internal-server-cert
- B. --dns
- C. --san
- D. --external-server-cert

<details>
  <summary>💡 Solution</summary>
C. --san    
</details>


