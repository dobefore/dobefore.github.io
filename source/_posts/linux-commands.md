---
title: linux-commands
readmore: true
date: 2022-05-16 08:44:22
tags: linux
---

### scp copy file between local and remote

copy file from local to a remote

\```

# eg:location2=/home/ubuntu

scp test.txt [ubuntu@192.x.x.x](mailto:ubuntu@192.x.x.x):/location2

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