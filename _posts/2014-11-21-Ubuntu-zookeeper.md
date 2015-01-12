---
layout: default
title: Ubuntu下的ZooKeeper环境搭建
---
====================

以下文档适用于：

- Operating System： Ubuntu 14.10
- Go Version： 1.33

### 1. 下载Zookeeper安装包

在ZooKeeper的发行页面找到安装包并下载，这里选用当前的稳定版本3.4.6

```
cd ~/Downloads
wget http://apache.mirrors.pair.com/zookeeper/zookeeper-3.4.6/zookeeper-3.4.6.tar.gz
```

### 2. 安装

```
mv zookeeper-3.4.6 zookeeper
mv zookeepr /opt/zookeeper
```

将以下行加到`~/.bashrc`

```
export PATH=$PATH:/opt/zookeeper/bin
```

### 3. 启动


前台启动：
```
zkServer.sh start
```
