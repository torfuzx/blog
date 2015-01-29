---
layout: default
title: Ubuntu下的Nsq环境搭建
---
=============
从NSQ源码安装
-----------

以下文档适用于：

- Operating System： Ubuntu 14.10
- Go Version： 1.33


### 1. 安装godeps

```
cd ~/Projects
git clone https://github.com/pote/gpm.git && cd gpm
git checkout v1.3.1 # You can ignore this part if you want to install HEAD.
./configure
make install
```

### 2.下载NSQ源码

```
cd ~/Projects
git clone https://github.com/bitly/nsq.git
```

### 3. 对NSQ安装包编译并测试

```
cd ~/Projects/nsq
gpm install
go get github.com/bitly/nsq/...
```

### 4. 启动NSQ相关服务

#### 4.1 nsqlookupd

在一个单独的终端中：

```
nsqlookupd
```

#### 4.2 nsqd

在一个单独的终端中：

```
nsqd --lookupd-tcp-address=127.0.0.1:4160
```

#### 4.3 nsqadmin

在一个单独的终端中：

```
nsqadmin --lookupd-http-address=127.0.0.1:4161
```

在浏览器中输入：127.0.0.1:4171访问
