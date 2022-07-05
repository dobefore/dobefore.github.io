---
title: termux-settings
readmore: true
date: 2022-07-05 11:46:11
tags:
---

## install linux distribution
```
pkg install proot-distro
proot-distro list

proot-distro install ubuntu
# or save command to a script
proot-distro login ubuntu
```
## settings in linux distribution
### install ssh
```
pkg install openssh-server
```
start sshd
```
/etc/init.d/ssh stop
/etc/init.d/ssh start
```
get username `whoami`
