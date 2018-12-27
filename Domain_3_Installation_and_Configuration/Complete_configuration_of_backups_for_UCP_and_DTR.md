# Complete configuration of backups for UCP and DTR

## Official Docker Documentation
[Backups and disaster recovery](https://docs.docker.com/datacenter/ucp/2.2/guides/admin/backups-and-disaster-recovery/)

To backup Docker Enterprise Edition you need to create individual backups for each of the following components:

1. Docker Swarm. Backup Swarm resources like service and network definitions.
2. Universal Control Plane (UCP). Backup UCP configurations.
3. Docker Trusted Registry (DTR). Backup DTR configurations and images.

[Backup the swarm](https://docs.docker.com/engine/swarm/admin_guide/#back-up-the-swarm)  

1. If the swarm has auto-lock enabled, you need the unlock key to restore the swarm from backup.
2. Stop Docker on the manager before backing up the data
3. Back up the entire ```/var/lib/docker/swarm``` directory.
4. Restart the manager.

[DTR backups and recovery](https://docs.docker.com/ee/dtr/admin/disaster-recovery/)  

Create a backup :
1. Backup image content ``` sudo tar -cf {{ image_backup_file }} \ $(dirname $(docker volume inspect --format '{{.Mountpoint}}' dtr-registry-<replica-id>)) ```
2. Backup DTR metadata
```bash
read -sp 'ucp password: ' UCP_PASSWORD; \
docker run --log-driver none -i --rm \
  --env UCP_PASSWORD=$UCP_PASSWORD \
  docker/dtr:2.5.6 backup \
  --ucp-url <ucp-url> \
  --ucp-insecure-tls \
  --ucp-username <ucp-username> \
  --existing-replica-id <replica-id> > dtr-metadata-backup.tar
```
[Restore UCP](https://docs.docker.com/datacenter/ucp/2.2/guides/admin/backups-and-disaster-recovery/#restore-ucp)

1. uninstall-ucp
1. restore with ```docker container run ... docker/ucp:2.2.14 restore < /tmp/backup.tar```