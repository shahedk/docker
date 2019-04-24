After downloading these files into linux machine, give execution rights to all `init.sh` scripts using the following code (assuming the code is checked out at ~/github/docker folder)
```
find ~/github/docker -type f -iname "*.sh" -exec chmod +x {} \;
```


### All compose files follow the following folder structure to map host path:

* ~/docker
* ~/docker/data/[container name]
* ~/docker/log/[container name]
* ~/docker/config/[container name]

