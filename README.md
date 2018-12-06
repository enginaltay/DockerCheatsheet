# Advanced Docker Commands including Docker Swarm! 

## 1. Introduction
### Control Specific Containers

Starting or stopping specific docker containers. We can even schedule it by writing cron jobs

``` docker ps -a -f name=nginx -q | xargs docker start ```


### Display Container Stats by Names

If you wonder how much cpu your container consumes, you can easily view it by typing

``` docker stats $(docker ps --format '{{.Names}}') ```
