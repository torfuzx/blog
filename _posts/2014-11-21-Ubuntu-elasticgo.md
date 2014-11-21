---
layout: default
title: Ubuntu 下的 ElasticSearch搭建
---
======================

###elasticsearch可部署到ubuntu或windows平台
####本文档的中搭建平台是 ubuntu 14.10
---------------------------
###安装openjdk
```
sudo apt-get install openjdk-8-jdk
```
###下载elasticsearch
```
https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.4.0.zip
```
###安装elasticsearch
```
sudo cp 下载目录/elasticsearch-1.4.0.zip /opt
cd /opt
sudo unzip elasticsearch-1.4.0.zip
cd /elasticsearch-1.4.0/bin
sudo ./elasticsearch
```

###测试elasticsearch
```
web browser中打开http://localhost:9200/

显示
{
  "status" : 200,
  "name" : "Logan",
  "version" : {
    "number" : "1.3.4",
    "build_hash" : "a70f3ccb52200f8f2c87e9c370c6597448eb3e45",
    "build_timestamp" : "2014-09-30T09:07:17Z",
    "build_snapshot" : false,
    "lucene_version" : "4.9"
  },
  "tagline" : "You Know, for Search"
}

```
