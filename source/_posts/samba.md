---
title: Samba
date: 2016-09-20 14:16:21
tags:
  - Ubuntu
  - Debian
  - Fedora
  - Centos
  - Opensuse
categories:
  - Server
---

## On Centos

### 安装应用

```bash
yum install samba
```

### 在home目录下新建samba文件夹

```bash
cd /home && sudo mkdir samba
```

### 修改配置文件/etc/samba/smb.conf

添加如下配置项
```
[share]
   comment = shared area
   public = yes
   writable = yes
   path = /home/samba
   create mask = 0777
   directory mask = 0777
   force user = smb
   force group = smb
   available = yes
   browseable = yes
```

### 新建用户smb

```bash
adduser smb --shell /bin/bash
```

### 给新用户设置密码

```bash
passwd smb
smbpasswd -a smb
```

### 关闭防火墙

```bash
systemctl stop firewalld.service
```

### 重启smb服务

```bash
systemctl restart nmb.service smb.service
```

### 测试验证

**在/home/samba目录下新建一个测试文件**

```bash
cd /home/samba
sudo touch readme.txt
```

**查看当前板子的IP地址**

```bash
ip addr
```
**访问samba目录**

在PC机上输入：`smb://192.168.1.xxx`
在出现的登录界面输入新添加的用户名和密码进行登录

## On Fedora

**ToDo ...**

## On Ubuntu

**ToDo ...**

## On Debian

**ToDo ...**

## On Opensuse

**ToDo ...**

