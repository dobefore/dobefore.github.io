---
title: termux-settings
readmore: true
date: 2022-07-05 11:46:11
tags: termux
---
## 获取手机存储访问权限
```
termux-setup-storage
```
## set user account for termux 
```
whoami
#set new pass
passwd
```
## install and set ssh
start sshd
```
apt install openssh
sshd -p8022
```
delete old host key in file `known_hosts` from client
e.g. `C:\Users\Admin\.ssh\known_hosts`

## set on-my-zsh
```
apt install curl zsh git
sh -c "$(curl -fsSL https://gitee.com/sherkeyxd/termux-ohmyzsh/raw/master/install.sh)"
```
add plugin `autosuggestions`
```
# 拷贝到 plugins 目录下(or use alternative repo from gitee)
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```
在 ~/.zshrc 中配置：
```
plugins=(其他的插件 zsh-autosuggestions)
```

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
apt update
apt install openssh-server
```
modify sshd_config
```
vim /etc/ssh/sshd_config
```
把Port 22改为 9022，注意不能是22，也不能是8022
把PermitRootLogin那一行，注释去掉，改为PermiRootLogin yes

start sshd
```
/etc/init.d/ssh stop
/etc/init.d/ssh start
```
check status of sshd
```
/etc/init.d/ssh status
```
get username `whoami`
最终还是失败不是ssh的问题
