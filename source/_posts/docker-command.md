---
title: docker-command
readmore: true
date: 2022-05-16 08:42:46
tags: docker
---

difference between image and container
We can build or image on local or from docker hub.Then We run container from image,you can run multi-containers from a image with `--name=appname`.

## install docker

```none
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```



## Add a Non-Root User to the Docker Group

this require you are login to non-root user on OS

```none
sudo usermod -aG docker Pi
```



## remove docker

```none
sudo apt-get purge docker-ce
sudo rm -rf /var/lib/docker
```



## build docker image

image_name:tag

```none
sudo docker build -t ankisyncd:latest .
```



## container run,start,stop,remove

### run container in foreground (add -d to run in background)

```none
sudo docker run -it ankisyncd:latest
```



### start and stop container

```none
docker container stop container_name
docker container start container_name
```



### look up IP address in a container

`docker ps -a` to get container_name

```none
docker inspect container_name | grep Address
```



### remove image and container

remove image

run `docker images` to get `IMAGE ID`,
then run `sudo docker rmi 8458e1ca9dca`

remove container

run `docker ps -a` to get `CONTAINER ID`,
then run `sudo docker rm 97590f6d5deb`

## Volume for persist data

add `VOLUME /app` in Dockerfile

show Volume

```none
docker volume list
```



remove the volume by `volume name`

```none
docker volume rm 962b2d970bcd96de860b348130a84aa86c0aaa55378b3dce35225659679ff808
```



## reference

https://phoenixnap.com/kb/docker-on-raspberry-pi