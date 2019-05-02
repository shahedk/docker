# My Docker Cheat Sheet

*Note: The detailed documentation of docker api and services are available at [docs.docker.com](https://docs.docker.com).*
### A collection of commonly used docker commands, utility scripts and compose files

#### Install docker on Ubuntu 18.x
```
sudo apt update

# Install docker
sudo apt install docker.io

# Install docker compose
sudo apt install docker-compose

# Add permission to current user to access docker
sudo usermod -aG docker $(whoami)
```

#### Run a docker container (eg. nginx)

```
docker run --name=my_nginx --restart=always -p 80:80 -p 443:443 -v "~/docker/data/nginx/conf.d:/etc/nginx/conf.d" -d nginx
```

Some useful options: 
* **--name** to specify a name for the container
* **-p** to map a port with host network. By default containers run in isolated network unless we explicitly specify to run on host network (eg. --network=host). 
* **-v** to map host folder (or file) to folder (or file) inside container
* Specify **-d** to run it on background and get command prompt back
* **--restart** defines the restart behaviour. For example, in this case we ask docker engine to restart the container if its down for unexpected reasons (eg. host machine restart).

Running a container using the above command syntax is quick and easy. But as the configuration settings are added, it becomes less readable. In my experience, I found using the *docker-compose.yml* is a better choice. Examples of the commonly used scenarios for docker-compose file are available in the [compose](https://github.com/shahedk/docker/tree/master/compose) folder. 

#### Starting and Stopping

* `docker start` starts a container
* `docker stop` stops a running container
* `docker kill` sends a SIGKILL to a running container
* `docker rm` removes the container


#### Info

* `docker ps` shows running containers
* `docker ps -a` shows running and stopped containers
* `docker stats` shows containers resource usage statistics.
* `docker port` shows public facing port of container.
* `docker inspect -f '{{ .Mounts }}'` shows list of volume maps

#### Executing Commands

* `docker exec` to execute a command in container. For example, use `docker exec -it [container_name] /bin/bash` to attach a new shell process to a running container.
