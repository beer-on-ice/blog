---
title: 'euserv免费Vps安装ServerStatus'
date: 2020-03-26 16:35:00
tags: vps
---

# Euserv 的免费 IPV6 Only Vps 安装 ServerStatus

## 1. 安装 serverStatus 服务端

我是在阿里云国际免费试用的小鸡(该小鸡是 ipv4 小鸡，我使用了 tunnelbroker 做了隧道，支持了 ipv6，可自行搜索教程)上安装了 ServerStatus 服务端，并添加好了节点

tip: 在配置隧道时，可参考截图部分

![https://i.loli.net/2020/03/26/imJ8621LfDRoOwX.png](https://i.loli.net/2020/03/26/imJ8621LfDRoOwX.png)

#### 安装：

```bash
wget https://raw.githubusercontent.com/CokeMine/ServerStatus-Hotaru/master/status.sh && chmod +x status.sh
```

#### 运行：

```bash
sh status.sh s
```

## 2. euserv 安装客户端

#### 安装：

```bash
wget https://raw.githubusercontent.com/CokeMine/ServerStatus-Hotaru/master/status.sh && chmod +x status.sh
```

#### 运行：

```bash
sh status.sh c
```

目前节点可以随便写，因为待会儿会删除配置文件

## 3.修改配置文件

### 方法一（本人使用）：

```bash
rm -f /usr/local/ServerStatus/client/status-client.py

wget -O /usr/local/ServerStatus/client/status-client.py https://raw.githubusercontent.com/CokeMine/ServerStatus-Hotaru/master/clients/status-client_ipv6.py

```

### 方法二：

打开/usr/local/ServerStatus/client/status-client.py 文件，然后把建立 socket 连接那一行的
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)改成 s = socket.socket(socket.AF_INET6, socket.SOCK_STREAM)

### 重新配置节点

节点配置为在服务端填写的信息，注意，此时的 ip 要写为服务端的 ipv6 地址，即使用 tunnelbroker 隧道后他们提供的 ipv6 地址（后面/64 不需要）

![79c9e25ba93ec818306d4b916530a39.png](https://i.loli.net/2020/03/26/aeD5HjRhBG7EuwZ.png)

```bash
bash status.sh c
```
