---
layout: post
title: "Zookeeper集群搭建（伪集群）"
subtitle: 'Zookeeper集群搭建教程'
author: "Oumuv"
date:   2018-11-26 12:00:00
header-img:   "img/about-bg.jpg"
header-mask:  0.3
catalog:      true
tags:
  - Zookeeper
  - 架构
---

环境要求
===
- jdk8
- zookeeper3.4
- Linux or mac系统

步骤
===

一、安装jdk8：参考 [Linux安装jdk8并配置环境变量](https://blog.csdn.net/oumuv/article/details/83856541)
---

二、下载Zookeeper安装包
---

- 下载地址：[http://mirrors.hust.edu.cn/apache/zookeeper/](http://mirrors.hust.edu.cn/apache/zookeeper/)

三、安装Zookeeper
---

- 点位到安装包所在目录，解压安装包

>    tar -zxvf zookeeper-3.4.10.tar.gz

- 进入到解压后的安装包目录，修改配置文件：
    - 重命名配置文件
    > mv conf/zoo_sample.cfg  conf/zoo.cfg

-