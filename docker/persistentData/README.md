# Persistent Data: Data Volumes and Bind Mounts

## Data Volumes
Special location outside of the containers UFS (Union File System). Preserved after container removal

### VOLUME in Dockerfile
`VOLUME /path/to/mounted/volume`
### Volumes available in the image
`docker image inspect {image}`
### Volumes & mounts in the containes
`docker container inspect {container}`
### listing of the volumes
docker volume ls
### Details on a volume
docker volume ls {volume name}

## Bind Mounts
Sharing/Mounting directory/file from the host into the container