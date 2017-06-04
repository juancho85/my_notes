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
`docker volume ls`
### Details on a volume
`docker volume ls {volume_name}`
### Named volumes
`docker container run -v {volume_name}:{/path/of/volume} {image}`
### Volume creation (usings specific drivers is possible)
`docker volume create` 

## Bind Mounts
* Sharing/Mounting folder/file from the host into the container (two locations pointing to the same files).
* Host files overwrite any in container.
* Can't be used in Dockerfile (must be in container run)
* Format (full path):
  * `run -v /my/dir:/path/container (mac/linux)`
  * `run -v //d/my/dir:/path/container (Windows)`

As an example: https://github.com/juancho85/udemy-docker-mastery/tree/master/dockerfile-sample-2
`docker container run -d --name nginx -p 80:80 -v $(pwd):/usr/share/nginx/html nginx`
> $(pwd) won't work for windows. ($pwd -replace "D:", "//d" -replace "\\", "/") is not working either

The html folder is shared between host and container and changes done in the host are immediately taken into accout!