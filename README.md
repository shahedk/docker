# My Docker Cheat Sheet

### A collection of commonly used docker commands, utility scripts and compose files

##### Install docker on Ubuntu 18.x
```
apt update
apt install docker.io
```

##### Run a docker container (eg. nginx)

```
docker run --name=my_nginx -p 80:80 -p 443:443 -v "~/docker/data/nginx/conf.d:/etc/nginx/conf.d" -d nginx
```

Some useful switches for docker run commands are: 
* *--name* to specify a name for the container
* *-p* to map a port with host network. By default containers run in isolated network unless we explicitly specify to run on host network (eg. --network=host). 
* *-v* to map host folder (or file) to folder (or file) inside container
* Specify *-d* to run it on background and get command prompt back
