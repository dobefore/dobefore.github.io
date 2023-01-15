---
title: linux-commands
readmore: true
date: 2022-05-16 08:44:22
tags: linux
---

# scp transfer files between local and remote

## copy file from local to a remote

```
scp test.txt [ubuntu@192.111.111.111](mailto:ubuntu@192.111.111.111):/home/ubuntu
```
## receive/download files from remote
for example receive an executable task from remote to local dir .
```
scp ubuntu@119.111.111.111:/home/ubuntu/task .
ubuntu@119.111.111.111's password:
task                     100% 3325KB 531.1KB/s   00:06
```

# decompress
## unzip
download via curl and unzip 
```
curl -o everytask.zip http://192.168.31.244:8000/everytask.zip
mkdir everytask
cp everytask.zip everytask

cd everytask
unzip everytask.zip
```