---
title: wsl-ubuntu22.04使用
header-includes:
 - \usepackage{fvextra}
 - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    template: C:/Huaxv/Huaxv-Tool/markdown-preview=enhanced/template.tex
    highlight: tango
    path: C:/Users/huaxv/Desktop/wsl-ubuntu22.04使用.pdf
---

# wsl-ubuntu22.04使用

## 添加用户

```bash
# 进入管理员模式
sudo su

# 创建新用户，会提示你输入密码、手机号等
adduser lrq

# 设置新用户权限，添加 sudo 权限
usermod -aG sudo lrq

# 为新用户创建一个 home 目录
mkhomedir_helper lrq

# 切换新用户
su - lrq

# 删除用户
deluser lrq
```

## 换源

```bash
sudo su


cp /etc/apt/sources.list /etc/apt/sources.list_1


vim /etc/apt/sources.list
```

阿里源：

```bash
deb http://mirrors.aliyun.com/ubuntu/ jammy main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-backports main restricted universe multiverse
```

更新：

```bash
sudo apt-get update


sudo apt-get upgrade
```

## 下载编辑环境

```bash
sudo su

sudo apt install build-essential manpages-dev software-properties-common gcc g++ make bison binutils gcc-multilib flex


sudo apt install gdb


sudo apt install openjdk-17-jre-headless


sudo apt-get install default-jdk


sudo apt-get install python3-pip
```

## ssh 连接

```bash
sudo su


vim /etc/systemd/resolved.conf


DNS=8.8.8.8
FallbackDNS=8.8.4.4


# 然后重启
reboot


sudu su


sudo apt install openssh-server


/etc/init.d/ssh start


sudo vim /etc/ssh/sshd_config


Port 16600
PermitRootLogin yes
PasswordAuthentication yes


sudo /etc/init.d/ssh restart


apt install net-tools


# 查看 ip 地址
ifconfig
```

powershell：

```bash
function ssh-copy-id([string]$userAtMachine, $args){   
    $publicKey = "$ENV:USERPROFILE" + "/.ssh/id_rsa.pub"
    if (!(Test-Path "$publicKey")){
        Write-Error "ERROR: failed to open ID file '$publicKey': No such file"            
    }
    else {
        & cat "$publicKey" | ssh $args $userAtMachine "umask 077; test -d .ssh || mkdir .ssh ; cat >> .ssh/authorized_keys || exit 1"      
    }
}

ssh-copy-id -p 16600 lrq@127.0.0.1
```
