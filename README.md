# Docker Commands including Docker Swarm

## 1. Introduction
### Control Specific Containers

Starting or stopping specific docker containers. We can even schedule it by writing cron jobs

``` docker ps -a -f name=nginx -q | xargs docker start ```

### Display Container Stats by Names

If you wonder how much cpu your container consumes, you can easily view it by typing

``` docker stats $(docker ps --format '{{.Names}}') ```

### Remove Unused Docker Images 

You can remove unused images with the following oneliner 

``` docker images -q |xargs docker rmi ```

### Remove Unused Docker Volumes 

Since the point of volumes is to exist independent from containers, when a container is removed, a volume is not automatically removed at the same time. When a volume exists and is no longer connected to any containers, it's called a dangling volume.

``` docker volume ls -qf dangling=true | xargs docker volume rm ```


### Remove Container Logs

You can clear container logs properly with the following oneliner. Especially nginx container logs could be huge in a short period.

``` CONTAINER_ID=$(docker ps -a -f name=nginx -q) && find -type f /var/lib/docker/containers/$CONTAINER_ID* -name "*.log" | xargs rm -rf ```

